---
title: "How to Use Playback States to Control Audio Flow"
date: 2024-06-12
description: "Learn how to use FMOD Playback States in Unity to manage audio events and prevent overlapping sounds."
tags: ["FMOD", "Unity", "Audio", "Playback States", "C#"]
---

When implementing dynamic audio in Unity using FMOD, you often need to know exactly what an audio event is doing at any given moment. Is it playing? Is it stopping? Has it already stopped?

This is where **Playback States** come in.

In this tutorial, we will explore what FMOD Playback States are, how to access them in your C# scripts, and how to use them to fix a common audio bug: the "stuttering" sound effect on UI sliders.

## What is a Playback State?

A Playback State is a tool from FMOD’s API that allows us to check the status of an Event Instance. It returns the current status of the audio as an **Enumerator (Enum)**.

The five main states returned by the API are:
1.  **PLAYING**
2.  **STARTING**
3.  **STOPPING**
4.  **STOPPED**
5.  **SUSTAINING**

By accessing these states, we can write logic that prevents sounds from overlapping or triggering incorrectly.

## Part 1: Setting Up the Variable

To use Playback States, you first need to define a variable to store the state information. Open the `MusicPlayer` script.

Inside your class, declare a variable of type `FMOD.Studio.PLAYBACK_STATE`:

```csharp
private FMOD.Studio.PLAYBACK_STATE musicPlayState;
```

*Note: You can omit `FMOD.Studio` if you are already using that namespace at the top of your script.*

## Part 2: Retrieving the State

To see what your audio is doing, you need to use the `.getPlaybackState()` command. This command queries the event instance and outputs the result into the variable we just created.

If you want to track the state in real-time, place this logic in your `Update()` function:

```csharp
void Update() 
{
    // Assuming '_musicInst' is your FMOD Event Instance
    _musicInst.getPlaybackState(out musicPlayState);

    // Debug to the console to see the state change
    Debug.Log(musicPlayState);
}
```

**How it works:**
*   **While Playing:** The console will log `PLAYING`.
*   **Entering a Portal/Stopping:** If you trigger a stop command, it switches to `STOPPING`.
*   **Finished:** Once the audio fades out completely, it switches to `STOPPED`.

*Important:* `getPlaybackState` only checks the state on the specific frame it is called. If you only put this in `Start()`, it will likely only ever say `STARTING` because it never updates again.

## Part 3: A Practical Example (The UI Slider Fix)

One of the most useful applications for Playback States is preventing audio spam.

Imagine you have a volume slider in your Settings menu. You want a sound effect to play when the user moves the slider so they can hear the volume level. However, if you simply tell the sound to `Start()` every time the slider value changes, the sound will restart every single frame the mouse moves. This creates a messy "machine gun" stuttering effect.

We can use Playback States to ensure the sound only starts if it isn't *already* playing.

### Step 1: The Setup
1.  **In FMOD:** Create a 2D Event (e.g., `LevelTest`) in a "UI" folder.
    1.  Add some test sounds into a Multi Instrument.
    2.  Ensure the event is sent to the SFX bus.
2.  **In Unity:** Open your `F_BusControl` script.

### Step 2: Modify the Script 

```csharp
// ... Your existing using statements ...

public class F_BusControl_class : MonoBehaviour
{
    // .. . Your existing variables ...
    EventInstance levelTestEvent; 
    
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        // ... Your existing bus setup code ...

        // only assign the event if its actually an SFX
        if(busPath == "SFX")
        {
            levelTestEvent = RuntimeManager.CreateInstance("event:/SFX/UI/LevelTest"); 
        } else
        {
            levelTestEvent.release(); 
        }
    }

    public void VolumeLevel(float newSliderValue)
    {
        bus.setVolume(newSliderValue); 
        levelTestEvent.start(); 
    }
}
```


You can hear that the sound stutters when you drag the slider quickly. We need to fix it by telling it to only start if th sound is not already playing.

We can use playback states to fix this issue:

```csharp
// ... Your existing using statements ...

public class F_BusControl_class : MonoBehaviour
{
    // .. . Your existing variables ...
    EventInstance levelTestEvent; 
    PLAYBACK_STATE pbState;
    
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        // ... Your existing bus setup code ...

        // only assign the event if its actually an SFX
        if(busPath == "SFX")
        {
            levelTestEvent = RuntimeManager.CreateInstance("event:/SFX/UI/LevelTest"); 
        } else
        {
            levelTestEvent.release(); 
        }
    }

    public void VolumeLevel(float newSliderValue)
    {
        bus.setVolume(newSliderValue); 
        if(busPath == "SFX")
        {
            // Check the playback state before starting the event
            levelTestEvent.getPlaybackState(out pbState);
            
            if (pbState != PLAYBACK_STATE.PLAYING)
            {
                levelTestEvent.start();
            }
        }
    }
}
```


Now, when you drag the slider, the sound will play once. It will only play again after the previous instance has finished, resulting in a smooth, non-stuttering audio experience.


## Summary

By using **Playback States**, you gain precise control over when your audio triggers. You are no longer just telling FMOD to "Play"; you are asking FMOD "Are you busy?" and acting accordingly.

This simple check is essential for creating polished UI sounds, managing dynamic music transitions, and ensuring your game's audio sounds professional and clean.
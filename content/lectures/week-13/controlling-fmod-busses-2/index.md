---
title: "Controlling FMOD Busses with Unity Sliders (Part 2)"
date: 2024-06-12
description: "Learn how to connect Unity UI sliders to FMOD bus volumes and ensure they persist across scene changes."
tags: ["FMOD", "Unity", "Audio", "Busses", "Sliders", "UI"]
---


In this tutorial, we will cover how to control the volume of your FMOD buses (like Music and SFX) using Unity sliders, and more importantly, how to make sure those sliders remember their positions when your player changes scenes.

## Part 1: Setting the Volume

### The Code
In your Bus Control script, create a new public function. Let’s call it `VolumeLevel`. This function needs to accept a `float` parameter, which will represent the data coming from the slider.

Inside the function, we use the FMOD API command `.setVolume()`.

```csharp
public void VolumeLevel(float newSliderValue) 
{
    // 'Bus' is the variable where you stored your FMOD Bus path earlier
    Bus.setVolume(newSliderValue);
}
```

### Understanding FMOD Volume Floats
It is important to understand how FMOD interprets these numbers. FMOD faders use a logarithmic scale (decibels), but the API uses a linear float scale between **0** and **1**.

*   **1.0f:** This equals the volume the fader was set to when you built your banks in FMOD. (If your fader was at 0dB, 1.0 = 0dB. If it was at -10dB, 1.0 = -10dB).
*   **0.0f:** This equals -infinity dB (silence).
*   **0.5f:** This is roughly -28dB (depending on the curve), effectively half the "fader distance" between the start point and silence.

## Part 2: Connecting the UI Slider

Now that the logic exists, we need to hook it up to the Unity UI.

1.  Select your **Slider** object in the Unity Hierarchy.
2.  Find the **Slider** component in the Inspector.
3.  Look for the **"On Value Changed (Single)"** event box at the bottom.
4.  Click the **(+)** icon to add a listener.
5.  Drag the GameObject containing your Bus Control script into the "Object" slot.
6.  In the function dropdown, look for your script name and select `VolumeLevel`.

**Crucial Step:** When selecting the function, you will see it listed twice: once under "Dynamic float" and once under "Static Parameters."
*   **Select the Dynamic Float version.** This ensures the function receives the *actual* current value of the slider as the player moves it.

## Part 3: The "Scene Reset" Problem

If you play your game now, the sliders will work. However, you will notice a bug if you switch scenes.

Let's say the player lowers the volume to 50%. When they walk through a portal to Level 2, the scene reloads. FMOD is smart—it remembers the volume is at 50%. However, the **UI Slider** is just a dumb object; it reloads from the prefab and resets visually to its default position (usually 100% or 0.9).

Now you have a slider showing 100% volume, but the audio is playing at 50%. We need to sync them up when the scene starts.

## Part 4: syncing Sliders with `.getVolume()`

To fix this, we need to tell the slider where the bus volume is actually located the moment the script starts. We do this using the `.getVolume()` command.

### The Challenge with `.getVolume()`
This command is slightly unique because it outputs **two** distinct values. It requires two `out` variables:
1.  **Volume:** The value set by the `setVolume` command (User input).
2.  **Final Volume:** The value calculated after combining user input with FMOD modulators or automation.

We only care about the first one (User input).

### The Solution
First, update your script to include the UI namespace, or Unity won't recognize what a "Slider" is.

```csharp
using UnityEngine;
using UnityEngine.UI; // Don't forget this!
```

Next, inside your class, create a reference to the Slider and variables to hold the volume data.

```csharp
private Slider slider;
private float busVolume;
private float finalBusVolume;
```

Finally, in your `Start()` function, grab the slider component and sync it to the FMOD bus:

```csharp
void Start() 
{
    // 1. Get the slider component attached to this object
    slider = GetComponent<Slider>();

    // 2. Get the current volume from the FMOD Bus
    // We pass in our two float variables to catch the data
    Bus.getVolume(out busVolume, out finalBusVolume);

    // 3. Update the slider visual to match the FMOD bus volume
    slider.value = busVolume;
}
```

## Summary

By using `setVolume` dynamically and `getVolume` on initialization, you create a seamless experience for the player.
1.  **On Start:** The script checks FMOD to see what the volume *should* be and updates the slider visual.
2.  **During Gameplay:** The slider updates the FMOD bus using the Dynamic Float event.
3.  **On Scene Change:** Even though the UI destroys and reloads, the `Start` function runs again, grabs the persistent FMOD volume, and snaps the slider back to the correct position.

Now your audio settings menu is robust and persistent across your entire game!
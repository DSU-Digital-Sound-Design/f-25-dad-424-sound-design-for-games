---
title: "Controlling FMOD Busses: Part 2"
date: 2024-03-14
draft: false
---

## Overview

This lesson introduces three major concepts:

### Implementing Real-Time Bus Volume Control

You’ll add a public function that updates FMOD bus faders based on slider values.

### Using Unity Events to Trigger Volume Updates

You’ll connect the slider’s On Value Changed UnityEvent to your BusControl function.

### Saving Slider Values Across Scenes

Using FMOD’s getVolume, you’ll retrieve the true bus volume and sync the slider values each time a scene loads.

---

## Adding Volume Control to the Script

Your BusControl script already contains:

* A bus reference obtained with GetBus
* A public string to specify each slider’s bus path
* Unity-side setup where each slider is bound to the correct bus

Now you’ll implement a function the sliders can call.

### Step 1: Create the Volume Control Function

Add this to your script:

```csharp
public void SetLevel(float newSliderValue)
{
    Bus.setVolume(newSliderValue);
}
```

Key ideas:

* newSliderValue is whatever value the slider currently holds.
* FMOD's setVolume expects a float between 0 and 1.
* FMOD maps 1.0 to the bus fader’s built-in level in FMOD Studio (not necessarily 0 dB unless your banks were built that way).
* 0.0 maps to negative infinity decibels.

### How FMOD Interprets Slider Values

Because FMOD uses a decibel scale internally, setVolume doesn't set dB directly. Instead:

* 1.0 = current FMOD fader position when banks were built
* 0.0 = silence
* Values in between interpolate logarithmically

For example:

* If your music bus is set to -10 dB in FMOD and banks are rebuilt, then setVolume(1f) equals -10 dB.
* setVolume(0.5f) would position the fader roughly halfway between -10 dB and negative infinity.

This is why your Unity slider should remain in 0–1 range.

---

## Connecting the Slider to the Function

### Step 2: Use Unity Events to Trigger the Function

1. Select a slider (Master, Music, or SFX).
2. In the Slider component, scroll down to On Value Changed.
3. Press the plus (+) button to add a new event.
4. Drag the slider’s own GameObject into the object field.
5. Choose the F_BusControl script.
6. Select setLevel under Dynamic Float.

Why Dynamic Float?
Because this passes the slider’s current float value directly into your function. Static parameters wouldn’t let the slider send its live value.

Repeat these steps for all three sliders.

Now your sliders can directly modify FMOD’s bus volumes during gameplay.

---

## The Problem: Slider Values Reset When Changing Scenes

Once this works, you’ll notice an issue:

* The player moves to a new scene.
* The MenuCanvas prefab loads anew.
* All sliders reset to their default value (0.9).
* But the FMOD buses still retain their previous levels.

So the UI no longer reflects actual audio levels.

We need the sliders to adopt the bus’s current value every time a prefab loads.

---

## Retrieving Bus Volume with getVolume()

FMOD offers a companion function:

```csharp
Bus.getVolume(out float volume, out float finalVolume);
```

* volume returns the value last set by the FMOD API (i.e., your script).
* finalVolume includes effects from modulation or automation inside FMOD.
* Because our buses have no modulation, we only use volume.

### Step 3: Create Two Float Variables

```csharp
private float BusVolume;
private float FinalBusVolume;
```

### Step 4: Retrieve Values in Start()

In your Start method, add:

```csharp
Bus.getVolume(out BusVolume, out FinalBusVolume);
```

This captures the bus’s volume exactly as it was left in the last scene.

---

## Syncing Slider Values to the Bus

Sliders must reflect BusVolume after the prefab loads.

### Step 5: Reference the Slider Component

Add at top:

```csharp
using UnityEngine.UI;
```

In the class:

```csharp
private Slider Slider;
```

In Start():

```csharp
Slider = GetComponent<Slider>();
Slider.value = BusVolume;
```

Every time a scene loads:

* MenuCanvas prefab loads new sliders.
* Your script retrieves the true FMOD bus volume.
* The slider value updates to match that level before gameplay begins.

This prevents unwanted jumps in volume and keeps UI and FMOD perfectly synced.

---

## Testing the System

Test steps:

1. Start the game.
2. Adjust Music, SFX, and Master sliders to various positions.
3. Enter the next scene.
4. Open the audio menu.
5. Verify that sliders appear in the exact positions you left them.

If the values match and the audio reflects those changes, the system is working correctly.

---

## Summary of New Concepts

This lesson introduced several essential tools for dynamic audio implementation:

### Controlling FMOD Buses

* setVolume adjusts realtime bus levels linearly (mapped to dB internally).
* getVolume fetches current bus levels so UI remains consistent across scenes.

### Working with UnityEvents

* OnValueChanged allows UI elements to trigger custom functions.
* Dynamic Float ensures live slider values are passed correctly.

### Scene-Independent UI Persistence

* Retrieving bus volume before scene start prevents slider resets.
* This aligns UI with FMOD state across multiple game levels.

---
title: "Controlling FMOD Busses: Part 1"
date: 2024-03-12
draft: false
---

## Overview

This lesson focuses on three core skills:

### Understanding FMOD Bus Routing

You’ll learn how group buses work, how to organize events into them, and how to prepare them for Unity integration.

### Understanding Unity UI Sliders

We’ll explore how Unity UI sliders behave, how the 3D GameKit implements its menus, and what parts of the UI we need to modify.

### Building a Reusable C# Bus-Control Script

You’ll create a script that dynamically connects each slider to the correct FMOD bus using a flexible string-based routing system.

---

## Preparing the Unity Scenes

### Step 1: Duplicate the Music Object for Scene Testing

To test audio control across multiple scenes:

1. Open Scene 1.
2. Copy the Music object from the Hierarchy.
3. Open the Gameplay → Level 2 scene.
4. Paste the Music object.
5. Play the scene to confirm the audio works.
6. Save the scene, then return to Scene 1.

This ensures your audio persists across scenes for testing.

---

## Creating FMOD Buses

FMOD buses behave like buses in a DAW—multiple events can route into them for shared processing, FX, and level control.

There are two types of main busses: group and return buses. For this system, we’ll use group buses only.

Group busses let you organize events into categories (e.g., Music, SFX) for collective volume control.

### Step-by-Step FMOD Bus Setup

1. Open FMOD Studio’s Mixer window:
   * Window → Mixer
   * Or press Ctrl+2 (PC) / Cmd+2 (Mac)
2. In the Routing view, create group buses:
   * Right-click → New Group
   * Create one named Music
   * Create another named SFX
3. Assign events to buses:
   * Drag music events to the Music bus.
   * Select all other events and drag them to SFX.
4. (Optional) Add FX to the group buses or create parent/child bus relationships.
   For this system, keep the buses independent.

### Final Bus Structure

* Master (built-in)
* Music 
* SFX

This structure mirrors the UI options players will control.

---

## Understanding Unity’s UI System

Unity’s UI system displays interactive elements on a Canvas GameObject. The 3D GameKit organizes its UI prefabs into multiple canvases that only activate at runtime.

### Navigating the Menus

1. Expand Menu Canvas in the Hierarchy.
2. Enable Pause Canvas to observe how UI elements appear.
3. Disable it again.
4. Open Audio Canvas (enable it) → BG.
5. Locate:
   * Master Volume Slider
   * Music Volume Slider
   * SFX Volume Slider

Each slider has a Slider component with:
* A value (0–1)
* An On Value Changed event (UnityEvent)

You won’t connect the UnityEvent yet—that comes in Part 2.

---

## Editing the UI Prefab (Important)

The Menu Canvas exists as a prefab shared across all scenes.

Therefore:
* Changes must be made to the **prefab**, NOT to a scene instance.
* Otherwise your work will disappear when loading a new scene.

### Editing the Prefab - Do this after you create the script

1. Project → Assets / 3DGameKit / Prefabs / UIPrefabs
2. Open MenuCanvas.prefab
3. Locate each of the slider objects.
4. Remove the “Mixer Slider Link” component.
5. Add your new script (F_BusControl) to each slider.

This ensures your changes propagate to every scene.

---

## Creating the Bus-Control Script

Create a new C# script in your FMOD scripts folder:

Name: F_BusControl.cs

### Step 1: Declare a Bus Variable

```csharp
FMOD.Studio.Bus Bus;
```

This references an actual FMOD bus—not an instance.

### Step 2: Add a Public String for the Bus Path

```csharp
public string BusPath;
```

This lets each slider connect to a different bus through the Inspector, using the same script.

### Step 3: Retrieve the Bus in Start()

```csharp
Bus = FMODUnity.RuntimeManager.GetBus("bus:/" + BusPath);
```

FMOD buses always begin with the prefix:

```
bus:/
```

You append the bus name (Music or SFX) via the BusPath variable.

### Important Notes

* FMOD bus references point to the actual bus—not an instance.
* Multiple scripts referencing the same bus will control the same bus.
* Event instances work differently: they create separate instances per variable.

---

## Connecting Sliders to FMOD Buses

Back in Unity:

1. Select Music Volume Slider.
2. In the F_BusControl component, set BusPath to: `Music`
3. Select SFX Volume Slider.
4. Set BusPath to: `SFX`
5. Select Master Volume Slider.
6. Leave BusPath empty.

FMOD’s Master Bus does not have a path because FMOD avoids conflicts when users create custom Master buses. The script will automatically bind to the system Master bus when the string is empty.

---

## Summary of What We Achieved

* You prepared scenes for testing audio across levels.
* You set up group buses in FMOD for Music, SFX, and Master.
* You explored how Unity’s UI system handles sliders and prefabs.
* You created a reusable bus-control script.
* You connected each slider to its FMOD bus via flexible string-based paths.

In Part 2, you’ll modify the script so the slider values actually adjust the FMOD bus volumes in real time.

This is where the system becomes fully interactive.


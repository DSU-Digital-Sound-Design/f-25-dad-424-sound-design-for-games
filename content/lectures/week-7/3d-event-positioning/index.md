---
title: 3D Event Positioning
---

## Overview

By the end of this lesson, you’ll:

* Understand 2D vs. 3D events in FMOD and when to use each
* Configure a Studio Listener so the player “hears” your world
* Build a spatialized FMOD event (Fireflies) and wire it up in Unity
* Learn two reliable ways to position events in 3D: `set3DAttributes` and `AttachInstanceToGameObject`
* Choose the right data sources for positioning (`Transform` and `Rigidbody`)
* Apply prefab best practices and avoid common pitfalls

---

## Prerequisites

* Unity with the FMOD Unity Integration installed
* An FMOD Studio project with banks building into your Unity project
* A Unity scene with a controllable camera and at least one GameObject to emit sound

---

## 2D vs. 3D in FMOD (and why 3D isn’t only for “3D games”)

* 2D events play without spatialization—no distance attenuation or positional panning.
* 3D events include a spatializer that:
  * Applies distance-based attenuation (volume changes with proximity)
  * Pans left/right to simulate direction relative to the listener

Use 3D events even in side-scrollers or top-down games whenever you want distance and direction cues (e.g., off-screen enemies, ambient sources).

> Our goal: a spatialized Fireflies emitter that loops as you approach and fades out as you walk away.

## Step 1 — Create a Spatialized Event in FMOD

1. In FMOD Studio, create folders:
   * SFX → Environment
2. Create a `3D Timeline Event` named `FireFlies` under SFX/Environment and assign it to the `Master` bank.
   1. Notice the spatializer component is added automatically.
3. Add your looping audio asset (e.g., `FireFlies_Loop_01`) to the event and add a **loop region**.
   1. Remember: assets are in the Audio Bin (ctrl + 3).
4. Leave the spatializer’s default curve for now; you’ll tweak min/max distance and curve later.
5. Build banks and save.

Tip: For teaching, prepare several presets of the distance curve so students can A/B the perceptual effects quickly during lab.

---

## Step 2 — Add a Studio Listener to Your Player Camera in Unity

* Add the `Studio Listener` component to the same GameObject that has your active `Camera` (your “ears” should live with your “eyes”).
* Our camera component is on the `Camera Brain` GameObject, which is a child of `CameraRig`.
* If your camera rig is a prefab (common in character controllers), add the component to the prefab so all scenes inherit it.
  * Find the prefabs in your Project window at `Prefabs -> Utilities`. 
  * Open the prefab, find the `Camera Brain` GameObject, and add `Studio Listener` there.
  * Return to the scene by clicking the back arrow in the top-left of the Scene view.

Prefab reminder: If you add the listener to a scene instance of a prefab, either “Open Prefab” and add it there, or click “Apply” in the Inspector so it persists across scenes.

---

## Step 3 — Script the Event Instance

Create a C# MonoBehaviour (e.g., `F_FireFlies.cs`) script in your `FMOD Scripts` folder. Find the fireflies GameObject in the Hierarchy under `Effects -> FireFlies` and attach to the prefab to open it with the right arrow next to the word `FireFlies`. After that you can see that each of the other `FireFlies` objects also have the same script attached .

---

### 1. Create the F_FireFlies Script


```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class F_FireFlies : MonoBehaviour
{
    FMOD.Studio.EventInstance FF;
    Rigidbody rb;

    // Start is called before the first frame update
    void Start()
    {
        FF = FMODUnity.RuntimeManager.CreateInstance("event:/SFX/Environment/FireFlies");
        rb = GetComponent<Rigidbody>();
        FMODUnity.RuntimeManager.AttachInstanceToGameObject(FF, transform, rb);
        FF.start();
        FF.release();
    }

    void OnDestroy()
    {
        FF.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);
    }
}
```
> Note: there are performance enhancements possible here, but this is the simplest reliable pattern for most use cases.

---

### 3. (Optional) Add a Rigidbody

If your FireFlies object drifts or moves dynamically:

* Add a **Rigidbody** component.
* Uncheck “Use Gravity” if you want it to float.
* FMOD will automatically use its velocity to calculate Doppler effects.

If it’s a static ambience point, skip the Rigidbody—`AttachInstanceToGameObject` will still position it using the Transform.

---

### 4. Test in Play Mode

1. Enter **Play Mode**.
2. Move your player camera (with the Studio Listener attached) around the FireFlies object.
3. Listen for panning and attenuation:
   * Louder when close
   * Softer when distant
   * Panned to the left/right depending on listener orientation

If it sounds static or incorrect, double-check:

* The event in FMOD is **3D**, not 2D.
* The event reference is assigned correctly in Unity.
* The `Studio Listener` is active on the main camera.

---

### 5. Alternative: Manual Positioning with set3DAttributes

If you’re managing position manually (e.g., procedural motion, teleports, or networked actors), replace the `OnEnable` body with:

```csharp
void Update()
{
    if (rb != null)
        instance.set3DAttributes(RuntimeUtils.To3DAttributes(transform, rb));
    else
        instance.set3DAttributes(RuntimeUtils.To3DAttributes(transform));
}
```

Use this version if you want fine-grained control over when spatial data is updated—especially useful for non-Unity physics movement.





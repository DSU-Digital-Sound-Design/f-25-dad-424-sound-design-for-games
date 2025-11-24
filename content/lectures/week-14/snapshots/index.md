---
title: "Creating Audio Zones and Dynamic Mixing with Snapshots"
---

In our previous tutorial, we mastered **Playback States** to control *when* sounds play. Now, we’re going to control *how* they sound based on the game environment.

Have you ever noticed how audio changes when a character walks into a cave (reverb kicks in) or when they are low on health (the sound gets muffled and bass-heavy)? In FMOD, these dynamic mixing changes are handled by **Snapshots**.

In this guide, we will cover:
1.  What Snapshots are and how to create them.
2.  Creating a **Reverb Zone** using Triggers.
3.  Handling signal routing (so your UI clicks don't echo!).
4.  Creating a **"Low Health" filter** using Parameters.

---

## What is a Snapshot?

Think of a Snapshot as a "preset" for your FMOD Mixer. When active, a Snapshot can change the volume of buses, toggle effects on and off, or change effect parameters.

There are two main types:
*   **Overriding:** Forces values to a specific state (good for absolute changes).
*   **Blending:** Adds changes on top of existing values (good for layering).

For this tutorial, we will focus on **Overriding** snapshots to create distinct audio zones.

---

## Part 1: The Reverb Zone (Trigger-Based)

Let’s create a system where entering a tunnel applies reverb to our sound effects.

### Step 1: FMOD Setup
1.  Go to the **Mixer** window in FMOD.
2.  Create a Return Bus for Reverb if you haven't already, and add a Reverb effect to it.
3.  Go to the **Snapshots** tab and create a new **Overriding Snapshot** named "Reverb Zone".
4.  **Scoping:** When you select the snapshot, your mixer faders will turn into yellow outlines. This means they are "scoped out" (unaffected). Click the fader for your **Reverb Return Bus** to "scope it in."
5.  Set the fader to 0dB.
6.  **Modulation:** To make the reverb fade in smoothly, right-click the Snapshot's **Intensity** dial (in the deck area) and add an **AHDSR Modulator**. This ensures the reverb doesn't snap on/off instantly.

### Step 2: The Unity Script
In Unity, Snapshots are treated almost exactly like Events. We create an instance, play it, and stop it.

Create a script called `ReverbZone` and attach it to a GameObject with a Box Collider (set to **Is Trigger**).

```csharp
using UnityEngine;
using FMODUnity;
using FMOD.Studio;

public class ReverbZone : MonoBehaviour
{
    private EventInstance reverbSnapshot;

    void Start()
    {
        // Create the instance just like a normal event
        // Note: The path starts with "snapshot:/"
        reverbSnapshot = RuntimeManager.CreateInstance("snapshot:/Reverb Zone");
    }

    void OnTriggerEnter(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            reverbSnapshot.start();
        }
    }

    void OnTriggerExit(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            // Allow the AHDSR to fade it out naturally
            reverbSnapshot.stop(STOP_MODE.ALLOWFADEOUT);
        }
    }

    void OnDestroy()
    {
        reverbSnapshot.release();
    }
}
```

### Step 3: Fixing the Signal Path (The UI Echo Problem)
If you test the game now, entering the zone will reverb *everything* sent to the SFX bus—including your UI menu clicks! That’s not what we want. We need to split the signal.

**In the FMOD Mixer:**
1.  Create two new Group Buses under your main **SFX** bus: call them **In-Game** and **UI**.
2.  Route your footsteps, attacks, and environmental sounds into **In-Game**.
3.  Route your menu sounds into **UI**.
4.  Place the **Reverb Send** on the **In-Game** bus only.

Now, your UI remains crisp and dry, while the game world echoes around you.

---

## Part 2: The Distance-Based Zone (Automation)

Sometimes you don't want a hard trigger; you want the effect to get stronger as you get closer to a specific object.

### FMOD Setup
1.  Create a new snapshot (e.g., "Reverb Source").
2.  Instead of an AHDSR on the **Intensity** dial, right-click and **Add Parameter**.
3.  Select the built-in **Distance** parameter.
4.  Draw a curve: Full intensity at 0 distance, fading to zero intensity at 10-20 units away.

### Unity Script
Since this relies on distance, we must tell FMOD where the snapshot is located in 3D space.

```csharp
void Start()
{
    reverbSnapshot = RuntimeManager.CreateInstance("snapshot:/Reverb Source");
    reverbSnapshot.start(); // Start immediately
    
    // Attach the instance to this object so FMOD knows its location
    RuntimeManager.AttachInstanceToGameObject(reverbSnapshot, transform, GetComponent<Rigidbody>());
}

void OnDestroy()
{
    reverbSnapshot.stop(STOP_MODE.IMMEDIATE);
    reverbSnapshot.release();
}
```
*Note: Make sure your Unity object has a Rigidbody for the attachment to work correctly.*

---

## Part 3: The "Low Health" Filter (Parameter Control)

A common game mechanic is muffling audio when the player is dying. We can achieve this by controlling a Snapshot via a script parameter.

### Step 1: FMOD Setup
1.  Add a **3-EQ Effect** to your **In-Game** bus.
2.  Create a Snapshot called "Low Health".
3.  Scope in the **High** and **Mid** bands of the EQ and turn them all the way down (leaving only low frequencies).
4.  Right-click the Snapshot's **Intensity** dial and select **Expose as Parameter**.
5.  Name the parameter "Health" (Range: 0 to 5).
6.  **Invert the curve:**
    *   When Parameter = 5 (Full Health), Intensity = 0% (No filter).
    *   When Parameter = 1 (Low Health), Intensity = 100% (Fully muffled).

### Step 2: Linking Health to Audio
In your Player Controller script, you need to update the snapshot whenever health changes.

```csharp
FMOD.Studio.EventInstance healthFilter;

void Start()
{
    healthFilter = RuntimeManager.CreateInstance("snapshot:/Low Health");
    healthFilter.start();
    healthFilter.release(); // Release immediately so it cleans up when stopped
}

// Call this function whenever the player takes damage or heals
public void UpdateAudioHealth(float currentHealth)
{
    // "Intensity" is the name of the exposed parameter on the snapshot
    healthFilter.setParameterByName("Intensity", currentHealth);
}

void OnDestroy()
{
    healthFilter.stop(STOP_MODE.IMMEDIATE);
}
```

By hooking the `UpdateAudioHealth` function into your existing damage logic (using Unity Events or direct method calls), your audio will dynamically react to the player's survival status.

---

## Summary

Snapshots are powerful tools that move beyond simple "Play/Stop" commands. By treating them as Event Instances in code, you can:
*   Trigger reverb zones using **Colliders**.
*   Automate audio changes based on **3D Distance**.
*   Drive mix changes using gameplay variables like **Player Health**.

With these tools, you've now covered the core pillars of FMOD implementation: Events, Parameters, Playback States, and Snapshots.

**Next up:** We will dive into the final piece of the puzzle: **FMOD Soundbanks** and how to manage them efficiently. See you in the next lesson!
---
title: "FMOD Event Instances"
---

# Event Instances in FMOD + Unity: A Hands-On Guide

## What You’ll Build

By the end, you will:

* Create an FMOD Event for background music
* Assign it to a Bank and connect it to Unity
* Instantiate, start, stop (with proper Stop Modes), and release an EventInstance in C#
* Verify correct lifecycle behavior using FMOD Profiler

## Setup

Open FMOD Studio with the 3D Game Kit Project and the Unity 3D Game Kit Project.

> Note: I had to update FMOD Studio and FMOD for Unity to the latest version (2.03.09 and 2.03.09 respectively) to get this working on my machine. See the [FMOD Download Page](https://www.fmod.com/download).

## Events

Events are how your game plays audio—sound effects, music, and dialogue. They’re flexible: you can build them with multiple tracks and layer or swap different assets. Think of an event as the unit you reference from code. In C#, you trigger an event (by creating and starting an EventInstance) whenever you want a sound to play.

---

## 1) Create a Music Event in FMOD

* In the **Events Browser**, right-click and choose `Event Preset → 2D Timeline`.
  Name the event `Gameplay_Music` and place it inside a folder called `Music`.
  *This event will serve as your background music for the first level.*
* Open the **Audio Bin** (`Ctrl+3` on Windows / `Cmd+3` on macOS`).
  Drag your chosen music file into this window to import it.
  * You can also import audio via `File → Import Assets`.
* With the `Gameplay_Music` event selected, drag your audio file from the Audio Bin onto a track in the event’s timeline.
  * Test playback using the transport controls at the top or by pressing the spacebar.
  * To loop the music, right-click the audio clip, choose `Add Loop Region`, and extend the loop region to cover the full track.
* Assign the event to a **Bank**, so Unity can load it at runtime.
  * Right-click the event and select `Assign to Bank → Master Bank`.
  * Banks package your FMOD events and assets into loadable groups for the game.
* Build your Banks (`File → Build` or press `F7`).
  * Building compiles and exports your latest FMOD data so Unity can recognize your new event.

---

## 2) Bring the Event into Unity

> Open the Level 1 scene in Unity Project tab: `3DGameKit -> Scenes -> GamePlay`.

* In Unity, create an empty GameObject named `Music Object`.
* In your Assets, create a folder in `3DGameKit -> Scripts` called `FMOD Scripts`.
* Create a new `MonoBehaviour` script called `MusicPlayer.cs` and attach it to `Music Object`.
* Open the script in your code editor.

---

## 3) Declare the EventInstance

Create a field to hold the FMOD event instance:

```csharp
using UnityEngine;

public class MusicPlayer : MonoBehaviour
{
    // Treat this as a single FMOD data type for now.
    private FMOD.Studio.EventInstance _musicInst;
}
```

**Concept:** An EventInstance is a runtime “copy” of your FMOD Event. You can create multiple instances for overlapping or independent playback. 

---

## 4) Choose How You Reference the Event Path

You can find your event path in FMOD Studio’s Events Browser. Right-click the event and select `Copy Path`. It will look something like `event:/Music/Gameplay_Music`.

You have two reliable approaches:

### A) Hard-code the Event Path

```csharp
void Start()
{
    _musicInst = FMODUnity.RuntimeManager.CreateInstance("event:/Music/Gameplay_Music");
}
```

### B) Use a searchable inspector field (recommended for reuse)

```csharp
public FMODUnity.EventReference eventPath;


void Start()
{
    _musicInst = FMODUnity.RuntimeManager.CreateInstance(eventPath);
}
```

* With `FMODUnity.EventReference`, Unity’s Inspector exposes a browser to pick the exact FMOD Event.
* Great for reusing the same script across different objects that trigger different events. 

---

## 5) Start the Event on Scene Start

```csharp
void Start()
{
    _musicInst.start();
    // Optional: immediately schedule the instance to be released when it’s done
    _musicInst.release();
}
```

**Note on `.start()`:** Calling `.start()` on a currently-playing instance restarts it from the beginning. Plan for this if you retrigger. 

> Play your game and you should hear your music start when the scene loads! If you don't hear anything you'll need to manually load the FMOD banks by adding an `FMOD Studio Bank Loader` component to a GameObject in your scene and selecting the `Master Bank` and `Master Bank Strings` banks.

---

## 6) Stop Gracefully on Scene Exit (or Object Destruction)

Use `OnDestroy()` to ensure your music stops when the level ends or the object is removed:

```csharp
void OnDestroy()
{
    // Choose an appropriate Stop Mode:
    _musicInst.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);
    // If you did NOT call release() in Start(), you can release here:
    // _musicInst.release();
}
```

**Choosing a Stop Mode**

* `STOP_MODE.IMMEDIATE` – hard stop (clicks/cutoffs if you haven’t designed for it)
* `STOP_MODE.ALLOWFADEOUT` – respects envelopes/modulation (preferred for music)
  Pair this with an AHDSR modulator on the Event’s Master volume in FMOD for musical fades. 

---

## 7) Manage Instance Lifetime with `.release()`

* `.release()` frees the native resources for an instance.
* If called while the event is playing, it defers destruction until playback stops (or is stopped).
* Strategy:
  * Call `release()` right after `start()` for fire-and-forget music cues.
  * Or defer `release()` to `OnDestroy()` if you need to keep explicit control of the instance’s lifecycle. 

---

## 8) Verify with FMOD Profiler (Live Update)

1. Enter Play Mode in Unity.
2. In FMOD Studio, open **Window → Profiler**.
3. Click **Live Update**, connect to `localhost` (if FMOD and Unity run on the same machine).
4. Press **Record** to see sessions and real-time metrics.
5. Play through your level; when the scene unloads or the object is destroyed, confirm:
   * Instances count drops to zero (if released)
   * The master bus signal reflects your fades and stops as expected

This confirms that your Start/Stop/Release logic works under actual gameplay conditions. 

---

## Full Example Script

```csharp
using UnityEngine;

public class MusicPlayer : MonoBehaviour
{
    // Pick the FMOD Event via the Inspector
    public FMODUnity.EventReference eventPath;

    private FMOD.Studio.EventInstance _musicInst;

    void Start()
    {
        // Create and start the instance when the scene starts
        _musicInst = FMODUnity.RuntimeManager.CreateInstance(eventPath);
        _musicInst.start();

        // Fire-and-forget: schedule cleanup when playback stops
        _musicInst.release();
    }

    void OnDestroy()
    {
        // Stop gracefully on scene/object teardown
        _musicInst.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);

        // If you didn’t call release() in Start(), release here instead:
        // _musicInst.release();
    }
}
```

---

## Troubleshooting Checklist

* Built Banks after changes in FMOD? If not, Unity won’t have the latest events.
* Event path correct? Use the FMOD Event Browser in Unity (via an `EventReference` field) to avoid typos.
* Hearing abrupt cuts? Switch to `ALLOWFADEOUT` and add an AHDSR envelope on the Event’s Master volume.
* Instances not freeing? Ensure `.release()` is called either after `start()` or in `OnDestroy()` and verify in Profiler. 


<!-- # Lab Idea (For Teaching)

* Provide students with a silent build and a handful of stems (music + ambience).
* Require:
  * Music event with AHDSR envelope
  * Ambient loop with parameterized crossfades (wind intensity)
  * Proper Start/Stop/Release logic
  * Profiler screenshot showing instances returning to zero on level exit
* Grade on correct event wiring, lifecycle management, and audible fade behavior under stop conditions.  -->

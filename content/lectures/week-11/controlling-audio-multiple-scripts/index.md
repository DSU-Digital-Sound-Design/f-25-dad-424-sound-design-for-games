---
title: "Controlling Audio From Multiple Scripts"
date: 2024-11-04
description: "Learn how to manage FMOD audio events from different Unity scripts without conflicts."
tags: ["FMOD", "Unity", "Audio Scripting", "Game Audio"]
---

# Overview

A hands-on guide to managing one FMOD event from different places in your Unity game. By the end, you’ll be able to start music in one script and safely stop or change it from another, without duplicate sounds or messy references.

## Learning goals

* Understand when to use instance (non-static) vs class-wide (static) variables
* Create and manage a single FMOD EventInstance for music
* Trigger fades and parameter changes from other scripts
* Avoid common pitfalls like invalid handles and race conditions

## What you’ll build

* A MusicScript that starts a looping music event
* A trigger script that fades the music when the player enters a zone
* An optional UI control to change a music parameter (e.g., intensity or low-pass)

---

# Static Vs Non-Static Variables Refresher

Here’s a simple example to clarify the difference between **non-static** and **static** data types in C# — especially in a Unity scripting context.


### Example: Player Score

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    public int playerScore = 0;          // Non-static (instance-based)
    public static int totalScore = 0;    // Static (shared across all players)

    void Start()
    {
        playerScore = Random.Range(1, 10);
        totalScore += playerScore;
    }
}
```

### How this works

* **Non-static (playerScore)**
  Each Player object keeps track of its own score.
  If you have 3 Player GameObjects, each will have a different `playerScore` value.
* **Static (totalScore)**
  This value is shared by all Player objects. Every time a new Player adds its score, `totalScore` updates globally.
  You can access it from anywhere with `Player.totalScore`—no need to reference a specific Player instance.

### Why it matters

* Use **non-static** when each instance should have its own data.
  Example: individual enemies with their own health or position.
* Use **static** when there should be only one value shared across all instances.
  Example: total score, global music controller, or global game state flag.


---

# Approach 1: Instance-based control (non-static)

Use this when the music belongs to a specific GameObject in the scene and you want to wire references explicitly in the Inspector.

## MusicPlayer.cs

```csharp
using UnityEngine;
using FMODUnity;

public class MusicPlayer : MonoBehaviour
{
    [SerializeField] private EventReference musicEvent;
    public FMOD.Studio.EventInstance MusicInst;

    void Start()
    {
        MusicInst = RuntimeManager.CreateInstance(musicEvent);
        MusicInst.start();
    }

    void OnDestroy()
    {
        MusicInst.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);
        MusicInst.release();
    }
}
```

## F_Teleporter.cs (fade music on trigger)

There are two ways to reference our `MusicPlayer` here. One is to use Unity's find methods to search for it in the scene; the other is to create a serialized field and drag the reference in the Inspector. The latter is preferred for performance and clarity.

Method 1: Using a find method (not recommended for performance reasons)
```csharp
// Example only — prefer the serialized field approach below
// var musicPlayer = GameObject.Find("Music Object").GetComponent<MusicPlayer>();
// or
// var musicPlayer = FindObjectOfType<MusicPlayer>();
```

Method 2: Using a serialized field (preferred)

```csharp
using UnityEngine;

public class F_Teleporter : MonoBehaviour
{
    [SerializeField] private MusicPlayer musicPlayer; // drag your MusicPlayer object here

    void OnTriggerEnter(Collider other)
    {
        if (!other.CompareTag("Player")) return;

        // Check if the music instance is valid before stopping
        if (musicPlayer != null && musicPlayer.MusicInst.isValid())
        {
            musicPlayer.MusicInst.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);
        }
    }
}
```

Why choose this: it’s explicit and great for scenes with multiple independent music or ambience controllers. You control exactly which instance you’re touching by wiring it in the Inspector.

To finish, select the GameObject with the `F_Teleporter` component and drag the GameObject with the `MusicPlayer` script into the `Music Player` field in the Inspector.

---

# Approach 2: Class-wide control (static)

Use this when there’s exactly one music instance for the whole scene or game and you want to access it from anywhere without passing references.

## MusicScript.cs

```csharp
using UnityEngine;
using FMODUnity;

public class MusicScript : MonoBehaviour
{
    [SerializeField] private EventReference musicEvent;
    public static FMOD.Studio.EventInstance MusicInst;

    void Start()
    {
        if (!MusicInst.isValid())
        {
            MusicInst = RuntimeManager.CreateInstance(musicEvent);
            MusicInst.start();
        }
    }

    void OnDestroy()
    {
        if (MusicInst.isValid())
        {
            MusicInst.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);
            MusicInst.release();
        }
    }

    public static void SetMusicParam(string name, float value)
    {
        if (MusicInst.isValid())
            MusicInst.setParameterByName(name, value);
    }
}
```

## F_Teleporter.cs (fade music on trigger)

```csharp
using UnityEngine;

public class F_Teleporter : MonoBehaviour
{
    void OnTriggerEnter(Collider other)
    {
        if (!other.CompareTag("Player")) return;

        if (MusicScript.MusicInst.isValid())
        {
            MusicScript.MusicInst.stop(FMOD.Studio.STOP_MODE.ALLOWFADEOUT);
        }
    }
}
```

Why choose this: it’s quick and convenient when you truly have a single, global music state. Anywhere in code can reach it via the class name.

---

# When to use which

Use instance-based if:

* You have multiple music or ambience controllers
* You want explicit Inspector wiring and easy prefab testing

Use static if:

* There is only one music instance
* Many systems need to access it without passing references
* You’re building a lightweight global music controller


---

# Troubleshooting checklist

* Does your Player have the Player tag and a collider/rigidbody appropriate for trigger events?
* Is the FMOD event assigned in the Inspector and valid in FMOD Studio?
* Are you calling stop on a valid instance? Check MusicInst.isValid() before using it.
* Are you starting the event before trying to stop it? Initialize in Start and verify logs.
* For static mode, do you accidentally create multiple MusicScripts? Guard with isValid().

---

# Clean-up and lifecycle tips

* stop ends playback; release frees the handle. After stopping with ALLOWFADEOUT, release the instance when you’re truly done with it.
* If music should persist across scenes, mark the music GameObject with DontDestroyOnLoad and manage transitions centrally.
* Avoid GameObject.Find. Prefer serialized fields (instance approach) or the class name (static approach) for clarity and performance.

---

# Quick reference

* Instance-based access: keep MusicInst non-static and pass references via the Inspector.
* Static access: make MusicInst static and reach it from anywhere with MusicScript.MusicInst.
* Always check isValid before using an EventInstance.
* Stop with ALLOWFADEOUT, then release when finished.

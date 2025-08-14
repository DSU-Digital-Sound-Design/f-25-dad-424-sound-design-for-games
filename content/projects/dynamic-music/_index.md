---
title: "Intermediate Project: State-Driven Dynamic Music with FMOD + Unity 3D Game Kit"
---

# Intermediate Project: State-Driven Dynamic Music with FMOD + Unity 3D Game Kit

## Project Brief

Design a reusable music system that reacts to **gameplay state** in the Unity **3D Game Kit**, using **FMOD** for authoring and a **single global parameter** to steer musical layers (e.g., Exploration ↔ Combat). Your solution should be modular, scalable to multiple enemies, and resilient against rapid state flapping.

---

## Learning Outcomes

* **Map gameplay states → FMOD parameters**
* **Architect an event-driven audio flow** using UnityEvents/C# events instead of per-object bespoke code
* **Author musical transitions** in FMOD (attack/release/curves) that feel intentional in play

---

## Requirements

* **Two or more states** (minimum: Exploration = 0, Combat = 1) controlled by **one FMOD global parameter**
* **One music source** in the scene (no per-enemy music instances)
* **Event-driven switching** from 3D Game Kit enemies/triggers without hand-editing every prefab
* **Audible smoothing** via FMOD envelopes/curves (no hard cuts)
* **Scalable logic** that works with many Chompers and other kit enemies

---

## FMOD Authoring (you choose the details)

* **Music event**: a single event containing layers/stems for each state
* **Global parameter**: name it clearly (e.g., `GameMusicState`, values 0/1\[/2])
* **Layer logic**: parameter-conditioned volume curves (not simple mutes)
* **Smoothing**: design **attack/release** per state (e.g., Combat = quicker attack, Exploration = longer release)
* **Max Instances = 1** for the music event
* **Banks/paths**: keep event path stable and documented for the Unity side

---

## Unity Architecture (guided, no full code)

### 1) **Central Music Manager** (single GameObject)

* **Start the FMOD music event** on scene load
* **Cache the global parameter ID** once
* **Expose a public method** (e.g., `SetState(int value)`) to change states
* **Stop with fadeout** on destroy/scene change
* **Use setParameterByID** for performance
* **Let FMOD handle crossfades**

### 2) **Trigger Layer**

* **UnityEvents Bridge**: Add a small component to enemies/volumes with `OnEnterCombat` and `OnExitCombat` events wired to `MusicManager.SetState()`
* **Combat Counter**: Track number of enemies engaged; increment on spotted/attack start, decrement on lost/death; derive state from counter value

### 3) **Debounce / Hysteresis**

* **Cooldown**: ignore flips for N ms after a switch
* **Min-time-in-state**: require minimum duration before switching again
* **Weighted votes**: require threshold of enemies before switching to combat

### 4) **3D Game Kit Integration Points**

* **Spot player / begin pursuit** → request Combat
* **Lose player / disengage** → request Exploration
* **On death** → request Exploration
* **Prefab wiring**: add hooks to prefabs, not scene instances

---

## Rubric (50 Points)

* **Functionality (15 points)**: States switch correctly from chosen triggers; single music instance; parameter updates reach FMOD event
* **Audio Experience (10 points)**: Transitions sound musical; envelopes tuned; no clicks/pops
* **Technical Design (10 points)**: Efficient architecture; decoupled triggers and manager; minimal duplication
* **Integration with 3D Game Kit (5 points)**: Correct use of enemy AI lifecycle events or prefab wiring
* **Scalability & Stability (5 points)**: Works reliably with multiple enemies; handles edge cases; avoids rapid state thrashing
* **Documentation & Clarity (5 points)**: Clear description of states, triggers, and debounce method

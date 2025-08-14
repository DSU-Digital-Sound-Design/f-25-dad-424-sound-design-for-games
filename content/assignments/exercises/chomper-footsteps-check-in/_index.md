---
title: "Chomper Footsteps Check-In"
---

**Checkpoint: Chomper Footsteps (20 pts)**

**Goal:** Add walking and running footsteps to all chomper enemies in your game, without editing each chomper individually.

**Requirements:**

* Use **`PlayOneShot`** only — no event instances.
* Store your event path or GUID in a **string variable** before using it.
* Every footstep should sound slightly different.
* Apply footsteps to **all chompers at once** (e.g., via prefab or shared script).

**Bonus (+2 pts):** Limit how many footsteps can play at the same time (done in FMOD).

**Tips:**

* Footstep audio is in **Enemies / Chomper / Locomotion** in your FMOD project.
* See “Using Play-One-Shot” and “Attaching Audio to Animations” lessons if you get stuck.

**Submit:**

* Unity scene (or prefab) with footsteps implemented.
* Script(s) you created or modified.
* Short screen capture showing chompers walking/running with varied footsteps.
* Text file with Unity + FMOD versions and your event path(s).

**Grading (20 pts total):**

* 5 pts – Uses `PlayOneShot` only, with event path stored in a string.
* 5 pts – Random variation in footsteps is audible.
* 5 pts – Footsteps play for all chompers without manual per-object edits.
* 5 pts – Works without FMOD errors in Console.
* +2 pts – Bonus: Footstep playback limit implemented in FMOD.


---
title: "Challenge 3: Health Crate Audio"
date: 2024-11-04
description: "Design and implement audio behavior for a Health Crate in Unity using FMOD."
tags: ["FMOD", "Unity", "Game Audio", "Challenge"]
---


### Overview

In this challenge, you’ll design and implement the **audio behavior** for the Health Crate in Unity using FMOD.
The crate should emit a **looping hum** before interaction and trigger a **one-shot burst** when the player collects health. 

---

### Objectives

* Integrate FMOD events with Unity using correct namespaces and instance management.
* Implement 3D spatialization so the audio responds to distance.
* Use parameters to automate playback and control transitions.
* Apply event lifecycle management to avoid leaks and redundant instances.

---

### Criteria (12 Points Total)

Follow the criteria below to complete the challenge:

| Criteria                                                                               | Points |
| -------------------------------------------------------------------------------------- | ------ |
| All sounds are 3D and get louder as the player approaches                              | 3      |
| The looping hum stops once the player collects health                                  | 3      |
| Instances are properly destroyed when no longer needed                                 | 2      |
| FMOD namespaces are used to shorten your code                                          | 2      |
| The one-shot triggers only when the player interacts with the health crate             | 2      |
| **Bonus:** Add a delay to the one-shot that increases as the player’s health decreases | **3**  |

---

### Hints & Resources

* Audio files are in your FMOD project under:
  **Audio Bin → Interactables → Health Boxes**
  * *Box Loop* (for the hum)
  * *Box Open* (for the one-shot)
* Lessons that may help:
  * *Using Play-One-Shot’s*
  * *Automating Audio with Parameters: Part 1 & 2*
* To find the player’s health, open the **Damageable** script on the **Ellen** GameObject.

---

### Deliverables

* **Short video (1–2 minutes):**
  Demonstrate the crate’s audio behavior in-game.
  * Show the 3D hum changing with distance.
  * Interact with the crate to trigger the one-shot.
  * (Optional bonus) Demonstrate the delay effect at different health levels.

---

### Reflection Prompt

Write 100–150 words explaining:

* How you structured your FMOD event.
* How you managed start/stop logic in Unity.
* (If you completed the bonus) How your delay changes with player health.



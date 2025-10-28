---
title: "Challenge: Chomper Footsteps (FMOD + Unity)"
---

## Goal

Add walking and running footsteps to all Chomper enemies using FMOD events and Unity’s animation system. You’ve already done this for your player—now apply the same principles to a non-player character.

---

## Challenge Criteria (25 Points Total)

| Category                       | Description                                                                                                      | Points |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------- | ------ |
| **1. Implementation Approach** | Footsteps use PlayOneShot or PlayOneShotAttached only—no declared event instances.                               | 5      |
| **2. Data Management**         | Event path or GUID stored in a string variable before being played.                                              | 5      |
| **3. Sound Variation**         | Each footstep sounds slightly different (through FMOD design choices).                                           | 5      |
| **4. System Design**           | All Chompers get footsteps without editing individual scene instances (e.g., prefab-based or scripted solution). | 5      |
| **5. Audio Quality & Polish**  | Footsteps feel natural, sync with animation timing, and show attention to mix and detail.                        | 5      |
| **Bonus**                      | Implement instance-limiting in FMOD so multiple Chompers don’t flood the mix.                                    | +3     |

---

## Guidelines

1. **You may only use PlayOneShot commands.**
   No event instances—keep things lightweight and stateless.
2. **Store your event reference.**
   Use a string to hold the event path or GUID before triggering the sound.
3. **Make footsteps varied.**
   You can do this inside FMOD through randomization, modulation, or playlists.
4. **Apply changes globally.**
   Update the Chomper prefab, animator events, or a shared script so every Chomper benefits automatically.
5. **Keep it in sync.**
   Animation events should call your function right on the step frames.
6. **For the bonus:**
   Limit max simultaneous instances of the footstep event in FMOD, and rebuild banks.

---

## Tips 

* The Chomper audio assets are in your FMOD Audio Bin under Enemies → Chomper → Locomotion.
* Refer to previous lessons on “Using Play-One-Shot” and “Attaching Audio to Animations.”
* You don’t need to follow a specific code structure—just ensure you meet the criteria above.
* Consider efficiency: one prefab update should cover all enemies.

---

## Submission Requirements

* Short video or gameplay capture demonstrating Chomper footsteps while walking and running.
* Screenshot or short note showing your FMOD event structure.
* (Optional) A brief paragraph describing how you ensured variety and limited instance counts.



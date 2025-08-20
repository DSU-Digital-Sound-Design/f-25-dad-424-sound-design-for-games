---
title: "Schedule"
author: ""
---

{{< toc >}}



# Week 1 (8/26) - Game Audio History

## Tuesday

- Syllabus introduction
- [Level 1: AAA \(Animation, Art, Audio\): Making Sense of Sound for Games](../lectures/week-1/level-1/)


## Thursday

- [Level 2: On the Road—to NOW! A Brief History of Games and Game Audio](../lectures/week-1/level-2/)

# Week 2 (9/2)

## Tuesday

- [Level 3: My Non-Linear Life: Audio for Interactive Environments](../lectures/week-2/level-3/)

## Thursday

- [Level 4: What Is Hip? Styles and Genres: Welcome to Acronym Hell](../lectures/week-2/level-4/)


# Week 3 (9/9) - Sound Design

## Tuesday

- [Level 5: Bleeps, Blops, Clicks, and Pops: Sound Design in Games](../lectures/week-3/level-5/)

> [Exercise 1: Source or create sounds given an asset list](../assignments/exercises/exercise-1/) - find or record these sounds
> DUE by the next class (Thursday, September 11)

## Thursday

- [Level 7: Do you Hear That Voice in My Head? Voice-Over for Games](../lectures/week-4/level-7/)
- Studio introduction/review
  - Demo recording voice
  - [Adventure Video Game Voice Over Scripts | Voices](https://www.voices.com/blog/adventure-video-game-voice-over-scripts/)


> [Exercise 2: Voice Over](../assignments/exercises/exercise-3/) - DUE Thursday, September 25

# Week 4 (9/16)

## Tuesday

- [VO Editing](../lectures/week-4/vo-editing/)
- more studio time/instruction for those who need it
- AI Voice
  - Look at Soundly Voices
  - Others: [LOVO](https://lovo.ai/) and [Resemble](https://www.resemble.ai/)
    - Create and clone voice and compare the results. 
    - Very Creepy! 

## Thursday

- [Level 6: Compose Yourself! The Art of Composing for Games](../lectures/week-6/level-6/)
- Some game music analysis from https://www.youtube.com/watch?v=DtHLMGiQlJw&list=PL-ZQIvQFPv4J_32ofFpI5Nd-WCk88rAC4

> Exercise 3: Prepare a short game music analysis using some or all of the topics we talked about today. DUE Thursday, October 2 (2 Weeks from now). [Instructions](../assignments/game-music-analysis/)

# Week 5 (9/23) — FMOD Integration + C# Basics

## Tuesday — Module: Introduction & Module 1 (start)

- Lesson 2: [Project Set-Up & FMOD Integration](../lectures/week-5/module-1/project-setup/)
- Module 1 – Lesson 1: The Basics of C# (Part 1)

## Thursday — Module 1 (continue)

- no class for Day of Service
- Lesson 2: The Basics of C# (Part 2)
- Lesson 3: FMOD Event Instances
- In-class lab: first Event, first Bank, Event Emitter in Unity

> **Check-in:** Unity scene + FMOD project path set, one one-shot event triggers in play mode.
> See [instructions](../assignments/exercises/fmod-event-instance-check-in/)

# Week 6 (9/30) — 3D, Positioning, and Challenge 1

## Tuesday — Module 1 (continue)

- Lesson 4: 3D Event Positioning (attenuation, spatializer)
- Live Update/Profiler connection test

## Thursday — Module 1 (finish) + Challenge 1

- Game Music Analysis Presentations
- Extra times? TBD
  - Lesson 5: Challenge Time!
  - In-class build: 3 emitters placed in world, audibly distinct distance curves

# Week 7 (10/7) — Interactivity Foundations

## Tuesday — Module 2 (start)

- Lesson 1: Using PlayOneShot
- Lesson 2: Automating Audio With Parameters (Part 1)

## Thursday — Module 2 (continue)

- Lesson 3: Attaching Audio to Animations
- Lesson 4: Automating Audio With Parameters (Part 2)


# Week 8 (10/14) — Challenge 2 + Launch Intermediate Project

## Tuesday — Module 2 (finish)

- Lesson 5: Challenge Time! (wrap Module 2)
- Code snippets: SetParameter by name vs ID, sanity checks in console

> **Check-in:** complete [challenge](../assignments/exercises/chomper-footsteps-check-in/); Due Friday

## Thursday — Launch Intermediate Project: Dynamic Music

- Brief: build a parameter-driven music system (Intro/Explore/Combat or Intensity 0–1)
- Map: snapshots/VCAs optional; use labeled or continuous parameters
- Show reference mini-scene setup; distribute template Unity scene

> **Intermediate Project: Dynamic Music** — Due Thu 10/30 (Week 10). [instructions](../projects/dynamic-music/)

# Week 9 (10/21) — Code Architecture & Namespaces

## Tuesday — Module 3 (start)

- Lesson 1: Interpreting Code
- Lesson 2: FMOD Namespaces

## Thursday — Module 3 (finish)

- Lesson 3: Controlling Audio Between Multiple Scripts
- Lesson 4: Challenge Time!
- Apply to Dynamic Music: separate input, state, and audio controllers

# Week 10 (10/28) — Present Dynamic Music + Start Mixing

## Tuesday — Presentations & Critique

- 1–2 min per team: demonstrate parameter mapping, transitions, profiling notes

## Thursday — Module 4 (start)

- Lesson 1: Controlling FMOD Buses (Part 1)
- Lesson 2: Controlling FMOD Buses (Part 2)
- Small lab: master, Music, SFX, VO buses; one VCA; target LUFS range for music bed

# Week 11 (11/4) — Snapshots, Playback States, Banks + Footsteps Prep

## Tuesday — Module 4 (continue)

- Lesson 3: Playback States
- Lesson 4: Snapshots
- Lesson 5: Loading Sound-Banks (builds, bank load modes)

## Thursday — Footsteps Project Brief (Regenstoet)

- Labeled parameter: Surface (Grass/Wood/Stone/Metal)
- Multi-Instrument variability (≥5 samples per surface), light pitch/vol randomization
- Animation events vs speed-based triggers; simple raycast material detection

> **Footsteps & Terrain Textures** — Due Thu 11/20 (Week 13). [Instructions](../projects/footsteps/) 

# Week 12 (11/11) — Veterans Day (No Class)

## Tuesday

- Veterans Day - No Class

## Thursday — Lab

- Implement surface detection → set Surface param
- Optional: Speed parameter modulates layer or cadence; snapshot for crouch/stealth

> **Introduce final project** — Due 12/16 (Finals Week). [Instructions](../projects/final/)

# Week 13 (11/18) — Footsteps Finishing + Short Shares

## Tuesday

- Peer tuning: cadence realism, repetition control, mix balance

## Thursday

- Final troubleshooting & submission packaging

> **Footsteps Project DUE Thursday, November 20**


# Week 14 (11/25) — Collision & Attack Sounds Sprint (Rowlilo)

## Tuesday — Module 5 (selected topics) + Sprint Launch

- Module 5 Lesson 1: Parameter IDs
- Lesson 2: Global vs Local Parameters
- Lesson 3: VCAs (tie into quick ducking/mix control)
- Sprint Brief: Collision, Material Detection & Attack Sounds
  - OnCollisionEnter/Stay/Exit patterns
  - Per-material responses (wood, stone, metal), intensity scaling by impact velocity
  - Attack/charge/release events with parameter-driven layers

## Thursday

- Thanksgiving Break - No Class

> **Sprint Submission window:** flexible; recommended by Tue 12/2 or roll into Final Project as a required feature.

# Week 15 (12/2) — Final Project Production

## Tuesday — Module 6 (pick what you need)

- Return Functions, Delegates, Event Callbacks, Programmer Instruments (for adaptive/interactive music or dialog variations)
- Apply selectively to final-project scope

## Thursday — Work Session

- Asset list, event map, parameter plan, mix plan, profiling goals

> **Final Project Asset List** — Due Thu 12/4.

# Week 16 (12/9) — Finalize & Present

## Tuesday

- Perf pass with Profiler, voice budgets, bank size checks

## Thursday

- Final presentations

> **Final Presentations** - December 16 at 3:30 - 5:30 pm

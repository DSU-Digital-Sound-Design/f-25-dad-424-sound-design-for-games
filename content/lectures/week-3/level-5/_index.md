+++
title =  "Level 5: Bleeps, Blops, Clicks, and Pops: Sound Design in Games"
outputs = ["Reveal"]
[reveal_hugo]
custom_theme = "reveal-hugo/themes/sunblind.css"
margin = 0.2
+++

# Bleeps, Blops, Clicks, and Pops
## Sound Design in Games

{{% note %}}
Total time: ~40 minutes
Structure: 3 hook + 3 outcomes + 8 concepts + 10 mini-lab + 8 case study + 5 wrap/exit
Handouts: Asset List CSV, Game Sound Analysis Worksheet (post to LMS)
{{%/ note %}}

---

## Adaptive Audio 

<iframe width="560" height="315" src="https://www.youtube.com/embed/p-FLWabby4Y" title="Adaptive audio example" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Different levels of adaptive audio; play 4 minutes
{{%/ note %}}

---

## Learning outcomes 

- Map a practical game-audio workflow from asset list to runtime behavior
- Differentiate interactive versus adaptive audio using observable criteria
- Classify layers and propose mix and accessibility strategies

{{% note %}}
Set expectations: we will practice a small end-to-end thread rather than lecture everything about formats and history.
{{%/ note %}}

---

## From Foley to parameters

- Theatrical sound effects and Foley established timing and gesture
- Digital libraries and DAWs scaled content creation and layering
- Middleware and parameters enabled systems that respond at runtime

{{% note %}}
Bridge explicitly: in film we place sounds to picture; in games we prebuild a palette and let systems place and transform them via state and parameters.
{{%/ note %}}

---

## Interactive versus adaptive 

- Interactive: audio is triggered directly by player input or discrete events
- Adaptive: audio changes in response to game state or parameter values
- Common mappings
  - Input → one-shot SFX
  - State → music section or snapshot
  - Parameter → continuous change of pitch, filter, send level

{{% note %}}
Ask for one example of each from any game they know. If needed, suggest player_speed, enemy_count, health, stamina, stealth_visibility.
{{%/ note %}}

---

## Diegetic and non-diegetic

- Diegetic: exists in the world; characters could hear it
- Non-diegetic: player-facing guidance or score
- Ambiguous cases to debate
  - In-world radio that crossfades to score
  - UI sounds that are framed as in-world devices

{{% note %}}
Quick show of hands on a tricky example. Ask each table to state a rule they will use when in doubt.
{{%/ note %}}

---

## Layered sound taxonomy

| Layer        | Primary goal                       | Pitfalls                        | Mix tools and policies                 |
|--------------|------------------------------------|----------------------------------|----------------------------------------|
| Ambience     | Sense of place and time            | Masking dialogue                 | EQ dips, level, bus ducking             |
| World/Foley  | Material identity, affordances     | Repetition, machine-gun effect   | Variations, random start, filters       |
| UI/UX        | Feedback and guidance              | Loudness spikes, overuse         | Loudness targets, short decay           |
| Dialogue/VO  | Intelligibility                    | Fighting music/ambience          | Sidechain, clarity EQ                   |
| Music        | Narrative pacing and emotion       | Loop fatigue, clashes            | Stingers, states, blends                |

{{% note %}}
Anchor today’s mini-lab in World/Foley and its relationship to ambience and UI ducking.
{{%/ note %}}

---

## Platform realities and mix strategy 

- Constrained platforms: pre-mix, consolidate layers, bake variation into assets
- Capable platforms: runtime mixing, snapshots, sends, real-time effects
- Decide what you pre-bake versus what the engine controls

{{% note %}}
Name checks: randomization in assets versus parameterized change at runtime. Students should always justify which side of the line they choose.
{{%/ note %}}

---

## Choosing file formats

- There is no single codec that fits every audio use case; each has strengths for different scenarios.
- Opus is best for compressing voice and dialog, combining high quality with small file sizes.
- WAV/PCM offers the fastest decoding and no loss of quality but results in very large files.
- Vorbis is a strong, widely compatible alternative when Opus isn't available.
- Hardware or software decoding methods can affect performance, so codec choice may depend on platform support.

[Source](https://www.audiokinetic.com/en/blog/a-guide-for-choosing-the-right-codec/)

{{% note %}}
- For extremely short sounds, uncompressed formats like WAV (or sometimes ADPCM) are preferred to avoid overhead.
- Opus has largely replaced Vorbis for speech and general use where supported, but Vorbis remains useful due to compatibility.
- Profiling your project and categorizing sounds before picking codecs yields optimal results.
- Hardware decoding is efficient, but not all platforms or codecs support it equally, and it's less effective for ultra-short sound effects.{{%/ note %}}

---

## Start with an asset list  

- Name, category, trigger, diegetic flag
- Playback (one-shot or loop), variations, randomization
- Parameters, ducking, priority, spatialization
- File format, SR/bit depth, loudness target, owner, status

---
| ID | Asset Name           | Category | Trigger/Event   | Diegetic | Playback |
|----|----------------------|----------|-----------------|----------|----------|
| 01 | footstep_grass_light | Foley    | player_step     | Yes      | One-shot |
| 02 | door_metal_open      | Foley    | interact_open   | Yes      | One-shot |
| 03 | ui_inventory_open    | UI/UX    | ui_open         | No       | One-shot |

---

| ID | Variations | Randomization             | Parameters      | Ducking             | Format |
|----|------------|---------------------------|-----------------|---------------------|--------|
| 01 | 8          | start ±20%, pitch ±3 st   | player_speed    | UI bus −4 dB, 50/200| OGG    |
| 02 | 3          | start ±10%, vol ±2 dB     | none            | music bus −3 dB     | WAV    |
| 03 | 2          | none                      | none            | none                | OGG    |

{{% note %}}
Point students to the CSV template posted on LMS and require consistent filenames and tags.
{{%/ note %}}

---

### Mini-lab: footsteps that adapt

> Goal: Design a small assets list for footsteps that adapt to player_speed and surface.
> 
> [Template](https://docs.google.com/spreadsheets/d/11qfMwjdae6Goc5L82WthQ08uevSRG5eDyDik1ziI_kY/edit?usp=sharing)

**Steps**
- Groups of 3–4 choose one surface: grass, metal, water, stone
- In the class Google Sheet (tab for your surface), fill 5 rows using:
  Asset Name · Category · Trigger/Event · Diegetic · Playback · Variations ·
  Randomization · Parameters/RTPCs · Ducking · Priority · File Format
- In Notes: define mappings (e.g., player_speed → pitch ±3 st, vol ±3 dB; crouch → high-cut)
- Prepare a 1-minute rationale: how you avoid repetition and masking

> - Deliverable: Five rows completed + 1-minute talk-through

{{% note %}}

* **Asset Name**
  Use snake\_case with surface + action + intensity.
  Examples: `footstep_grass_light`, `footstep_metal_heavy`, `ui_inventory_open`

* **Category**
  Broad grouping for mix policies: Ambience, Foley, UI, Dialogue, Music

* **Trigger/Event**
  When the sound plays, written like an in-engine hook.
  Example: `player_step(surface=stone)`

* **Diegetic**
  Yes = in the world (footsteps, doors). No = player-only (UI clicks)

* **Playback**
  One-shot (footsteps, UI) vs. Loop (ambience beds, wind)

* **Variations**
  Number of alternates to reduce repetition (e.g., 6–10 for footsteps)

* **Randomization**
  Small changes per playback to humanize:
  Examples: `start ±15%`, `pitch ±2 st`, `vol ±2 dB`

* **Parameters/RTPCs**
  Gameplay values that drive change.
  Examples: `player_speed → pitch ±3 st`, `crouch → LPF 5 kHz`

* **Ducking**
  Sidechain to protect clarity.
  Example: `UI −3 dB (attack 10 ms, release 200 ms)`

* **Priority**
  High (critical cues), Medium (most Foley), Low (ambience)

* **File Format**
  OGG for runtime SFX/music, WAV/CAF for source/tight loops, AAC for streams

* **Notes**
  Implementation details, test methods, or accessibility intent
  Example: “Caption: \[Soft crunch]; Test: sweep player\_speed 0–1, confirm smooth pitch change”

{{%/ note %}}

---

## Roles and collaboration thread  

- Audio Director or Lead: loudness targets and scope guardrails
- Sound Designer: variation design, naming, and mix intent
- Audio Programmer: parameter plumbing, snapshots, performance budgets

{{% note %}}
Tie roles back to the mini-lab: who owns player_speed mapping, who verifies, who signs off.
{{%/ note %}}

---

## Appendix: optional early tech clip

Mike Patton and the Intonarumori

<iframe width="560" height="315" src="https://www.youtube.com/embed/lrfCq71EfNU" title="Intonarumori example" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Use only if you have extra time or want a historical segue. Prompt: what’s the through-line from mechanical noise instruments to today’s parameterized SFX?
{{%/ note %}}

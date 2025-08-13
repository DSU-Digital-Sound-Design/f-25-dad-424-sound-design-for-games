---
title: "Exercise 1: Source or Create Sounds Given an Asset List"
---

# Exercise 1: Source or Create Sounds Given an Asset List

## Assignment Overview

You are working for a client developing an **Untitled Cat Game**. An updated [Asset List](asset-list_with_columns_with_comments.xlsx) has been provided. It contains all required audio assets for the demo level. Your job is to source or create these sounds to meet the provided technical and creative specifications.

You will:

1. Record, design, or source each sound listed.
2. Save each file to the `sound_assets` directory in the proper subfolder.
3. Update the spreadsheet with filenames, category, license info, and designer notes.

---

## Requirements for All Audio Assets

**File Specs**

* **Format**: 24-bit, 44.1 kHz WAV
* **Channels**: Mono unless stereo is intentional and justified in spreadsheet
* **Normalization**: Peak normalize to **-0.5 dBFS** (true peak)
* **Silence**:
  * < 0.5 s at the beginning
  * < 1 s at the end (unless designed that way)
  * Multi-version files: ≥ 2 s silence between versions
* **Fades**: ≥ 10 ms at clip start and end to avoid clicks
* **Noise Floor**: Below -50 dBFS for non-noise-based sounds

**Naming**

* Filenames are pre-filled in the spreadsheet — don’t change them except to add `_var01`, `_var02`, etc.
* Place files into subfolders within `sound_assets/` based on Category:

  ```
  sound_assets/
    cat/
    foley/
    amb/
    ui/
    docs/
  ```

---

## Spreadsheet Columns — Abbreviated Guide

* **Sound Designer Notes** – Communicate to the game designer how to use the sound.
* **Category** – Foley, Character/VO, Ambience, UI
* **Priority** – High (frequent/core), Medium (occasional), Low (rare/polish)
* **Loopable?** – Yes if it should loop seamlessly, No if it’s a one-shot
* **Variation Required?** – Yes if multiple takes needed, No if one is enough
* **Source/License** – Origin and license (e.g., “Recorded by student”, “Freesound CC0 + URL”)
* **Implementation Notes** – Short instructions for in-game use (looping, pitch randomization, etc.)

---

## Communication With the Game Designer

If you deviate from any requirement, note it in **Implementation Notes** and suggest an alternative.

Example:

> “3 variations, 2 s apart; normalized to loudest sound; mono for efficiency; suggest pitch ±2% in middleware.”

---

## Deliverables

Submit a **zipped folder** containing:

1. `sound_assets/` directory with organized subfolders
2. Updated spreadsheet
3. Original/raw files in `_src/`
4. License documents (if applicable)

---

## Rubric (10 points)

| Category                 | Points |
| ------------------------ | ------ |
| Technical compliance     | 3      |
| Creative appropriateness | 3      |
| Documentation & notes    | 2      |
| Organization & delivery  | 2      |


> Based on [Game-220-Exercise-2/README.md at main · APUGames/Game-220-Exercise-2](https://github.com/APUGames/Game-220-Exercise-2/blob/main/README.md)

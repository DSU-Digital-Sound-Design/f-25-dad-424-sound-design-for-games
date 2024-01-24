---
title: "Exercise 2: Creating a UI Sound Library"
---

# Exercise 2: Creating a UI Sound Library

This exercise involves the creation of a User Interface (UI) sound library tailored for the menu page and inventory screen of an adventure/survival-themed game. The sounds you'll produce should complement the game's outdoor survival theme and have an organic feel, steering clear of electronic tones.

## Objective

Your task is to design and compile a collection of non-diegetic, theme-fitting sounds for the game's UI, specifically focusing on the menu page and inventory screen. These sounds must integrate seamlessly with the game's outdoor survival theme and possess an organic quality as per the client's request.

## Requirements and Guidelines

### Sound File Specifications

- **Format and Quality**: Each sound file must be a 24-bit, 44.1kHz Stereo WAV file.
- **Organization**: Place all sound files within a folder titled `sound_assets`.
- **Naming Convention**: Name each file clearly and descriptively, matching the `Asset Name`. For instance, a sound file for an asset named "menu-open" should be titled `menu-open.wav`.
- **Audio Normalization**: Normalize the peak of each sound file to -5 dBFs.
- **Silence Duration**: Ensure that each sound file has less than 0.25 seconds of silence at both the beginning and the end.

### Documentation and Communication

- **Designer Notes**: Some assets may include `Designer Notes`. Make sure to read and consider these notes while creating the sounds.
- **Sound Designer Notes**: If you have any comments or suggestions regarding the sound files, document them in the `Sound Designer Notes` field.
- **Asset List**: An [asset list](asset-list.xlsx) will guide you through the required sounds. After creating a sound, update the asset list by filling in the `Filename` column and adding any relevant notes in the `Sound Designer Notes` column. Your notes should be concise and provide clear guidance to the Game Designer on how to implement the sound.

#### Example of Asset List Documentation

Here's an example of how you might document a completed sound asset in the asset list:

**Before:**

| Asset Name  | Description                                 | Filename | Game Designer Notes | Sound Designer Notes |
| ----------- | ------------------------------------------- | -------- | ------------------- | -------------------- |
| ui-navigate | When user moves from one UI item to another |          | Something organic   |

**After:**

| Asset Name  | Description                                 | Filename            | Game Designer Notes | Sound Designer Notes                                      |
| ----------- | ------------------------------------------- | ------------------- | ------------------- | --------------------------------------------------------- |
| ui-navigate | When user moves from one UI item to another | _ui-navigate-1.wav_ | Something organic   | _Provided multiple options with 2 seconds between each_ |

By following these steps and adhering to the specifications, you will create a cohesive and thematic UI sound library that enhances the player's experience in the game's menu and inventory interfaces.

<!-- # Exercise 2: Creating a UI sound library

## Assignment

You are tasked with creating User Interface sounds for the menu page and inventory screen of an adventure/survival game. These sounds are _non diagetic_, but they should fit the overall theme of the game, which is "outdoor survival". The client requested that the sounds "sound organic" and "not electronic".

### Audio asset requirements

- **Each file must be a 24bit, 44.1kHz Stereo .wav file.**
- Each sound should be in a folder named `sound_assets`
- Each filename should be human readable and use the `Asset Name` _as_ its filename:
  - For example, for an `Asset Name`: "menu-open":
    - `menu-open.wav`
- Each file should be peak normalized to -5 dBFs
- Each file should have less than 0.25 seconds of silence at beginning
- Each file should have less than 0.25 seconds of silence at ending

### Communication

Some `Designer Notes` are included for a couple sounds. Please read these.

If needed, please leave any notes on the sounds provided in the `Sound Designer Notes` field.

An [asset list](asset-list.xlsx) is provided with a list of requested sounds. **Update `asset-list.xlsx` with the filename, and any notes you have for the game designer.** Notes should be clear in meaning and directed toward the Game Designer in how to use the sound.

For example, given this asset list row:

| Asset Name  | Description                                 | Filename | Game Designer Notes | Sound Designer Notes |
| ----------- | ------------------------------------------- | -------- | ------------------- | -------------------- |
| ui-navigate | When user moves from one UI item to another |          | Something organic   |

You add a `ui-navigate-multiple.wav` and update the row :

| Asset Name  | Description                                 | Filename            | Game Designer Notes | Sound Designer Notes                                      |
| ----------- | ------------------------------------------- | ------------------- | ------------------- | --------------------------------------------------------- |
| ui-navigate | When user moves from one UI item to another | _ui-navigate-1.wav_ | Something organic   | _I provided multiple options with 2 seconds between each_ | -->

> Based on: [APUGames/Game-220-Exercise-3: UI Sound Library](https://github.com/APUGames/Game-220-Exercise-3)

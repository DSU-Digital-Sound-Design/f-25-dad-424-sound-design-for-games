# Exercise 2: Creating a UI sound library

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

An [asset list](assets-list.xlsx) is provided with a list of requested sounds. **Update `asset-list.xlsx` with the filename, and any notes you have for the game designer.** Notes should be clear in meaning and directed toward the Game Designer in how to use the sound.

For example, given this asset list row:

| Asset Name  | Description                                 | Filename | Game Designer Notes | Sound Designer Notes |
| ----------- | ------------------------------------------- | -------- | ------------------- | -------------------- |
| ui-navigate | When user moves from one UI item to another |          | Something organic   |

You add a `ui-navigate-multiple.wav` and update the row :

| Asset Name  | Description                                 | Filename            | Game Designer Notes | Sound Designer Notes                                      |
| ----------- | ------------------------------------------- | ------------------- | ------------------- | --------------------------------------------------------- |
| ui-navigate | When user moves from one UI item to another | _ui-navigate-1.wav_ | Something organic   | _I provided multiple options with 2 seconds between each_ |

> Based on: [APUGames/Game-220-Exercise-3: UI Sound Library](https://github.com/APUGames/Game-220-Exercise-3)

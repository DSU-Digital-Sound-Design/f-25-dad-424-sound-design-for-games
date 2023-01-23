# Exercise 1: Source or create sounds given an asset list

## Assignment

A client is working on an Untitled Cat Game. An [Asset List](../asset-list.xlsx) has been provided. In it are several sounds needed for the demo level of the game.

Source or create the sounds provided, and place the files in a directory called `sound_assets`. Update the [Asset List](../asset-list.xlsx) file with the filename.

> Tips for finding [Sound Effects](https://www.freeaudioresource.com/sound-effects)

### Audio asset requirements

- **Each file must be a 24bit, 44.1kHz Stereo .wav file.**
- Each filename should be human readable and use the `Asset Name` in it's filename:
  - For example, for an `Asset Name`: "Kitten Meow":
    - `Kitten meow.wav`, `kitten-meow.wav` and or `KITTEN_MEOW.wav` are all acceptable.
    - `FSWEB__einen_katzenmeow__FREESOUNDZWEB-293847298347.wav` is not.
- Each file should be peak normalized to -0.5 dBFs
- Each file should have less than 0.5 seconds of silence at beginning
- Each file should have less than 1 seconds of silence at ending
- If providing a sound file with multiple versions of a sound, please separate each sound with at least 2 seconds of silence.

### Communication

Some `Designer Notes` are included for a couple sounds. Please read these.

If needed, please leave any notes on the sounds provided in the `Sound Designer Notes` field.

**Update `asset-list.xlsx` with the filename, and any notes you have for the game designer.** Notes should be clear in meaning and directed toward the Game Designer in how to use the sound.

For example, this is a helpful note:

> "File includes multiple meows with 2 seconds of silence between each. Whole file is peak normalized to loudest sound in clip"

> Based on [Game-220-Exercise-2/README.md at main · APUGames/Game-220-Exercise-2](https://github.com/APUGames/Game-220-Exercise-2/blob/main/README.md)

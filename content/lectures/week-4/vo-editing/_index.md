---
title: "VO Editing"
---

See this video for reference: [Recording and Processing Voiceover or Narration in REAPER](https://www.youtube.com/watch?v=eTNo3yrWGww)

Download [Max's VO](max-vo.wav) recording to edit with me in class.

After we record our voice over a few things need to be done to make sure our recording sound good and are edited properly.

## ReaFir

First, we'll remove any noise added during the recording process with ReaFir. Add the plugin with the following settings:

![](reafir.png)

Make a time selection on a part of the recording with silence. Play the recording to build your noise profile. Then, uncheck "Automatically build noise profile." Now, ReaFir will filter out any unwanted noise from your VO Recordings.

Listen to the track to make sure you haven't added any unwanted artifacts.

## Editing

Now you can split your track into media items for each line you need for the assets list. Add fade ins at the start of the item and fade outs at the end.

Make sure _Options: Auto-crossfade media items when editing_ is on.

Max is making some clicky mouth noises. Let's try to find them and remove them. After removing them, replace them with silence from the part of the recording that you used for ReaFir noise suppression. One trick for this is the action _Item: Split items at time selection_ (Shift + S). This will make it easy to cut the right amount of silence to replace your mouth sound.

If you would like to remove part of an item and move it over in time you can enable **ripple editing** and select the part you want to remove with a razor edit (option + right click drag).

When you're happy with your edits, glue the items back together to remove any cuts. This will allow easy rendering.

Other editing tips: [How To Remove Mouth Noises In Your Recordings](https://www.youtube.com/watch?v=r5ki_fo2rlk)

## Effects

- EQ: Add a high pass filter with ReaEQ to cut out low end that isn't needed for the voice.
- Compression: Add ReaComp with a 4:1 ratio and auto-makeup gain.
- Multiband Compression: Add ReaXComp to do compress each frequency range of the voice separately. Use a 4:1 ratio on each band and select "[program dependent release](https://www.sweetwater.com/insync/program-dependent-release/)." Select "solo current band" and set the threshold on each band to your liking.
- Limiter: Add ReaLimit with a brickwall ceiling of -5 dB
- Meter: Add JS: Loudness Meter Peak/RMS/LUFS (Cockos) to your master, so that you can see what your levels are at before exporting.

## Extra rendering instructions

See the rendering settings below. Notice the checked parameter _tracks with only mono media to mono.files_. This setting allows us to render stereo and mono tracks depending on the channel count of the original media items. Rendering mono items as mono files saves storage space.

![](rendering.png)

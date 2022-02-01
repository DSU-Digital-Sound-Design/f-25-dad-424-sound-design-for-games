---
title: "Re-orchestration"
---

## Building a Layered Structure

Import the CombatA folder to the Music work unit as a music segment. Each of the wav files will be a music track of this CombatA music segment.

Make sure you're in the interactive music view. See how now our music has multiple tracks, much like a typical DAW. This allows us to re-orchestrate the music, not just re-sequence it. This music was intentionally over orchestrated. If everything plays at once, it sounds like too much sound. It was done this way so we can have variations on orchestration that all work.

Again, set the tempo to 138 bpm so that the timeline matches the music's tempo. Fix the exit point so that its at the end of bar 9, giving us 8 bars of music.

Add the Combat-A music segment to a music playlist container and call it combat. Remember the the playlist allows us to arrange and loop segments. Again, set the tempo of the music playlist to 138 bpm. Add the combat-a music segment to the playlist and set the looping to infinite on the group. Play it and hear how the music loops seamlessly because we set our exit point correctly.

## Experimentation with the Layered Approach

It's a little busy when every layer plays at the same time. With the combat playlist selected, pin the transport control. This allows us to solo and mute the layers without taking focus from the playlist. Listen to each track to hear how it sounds by soloing it. To solo one track at a time "command + click" on the track. To reset the mutes or solos "alt + click" on the mute or solo. You can also click on the icon in the menu bar or music track property editor.

These tracks were premixed in the DAW, so we shouldn't have to do any balancing in Wwise. Because of this we can leave our voice volume at 0.

## Editing Clips

Select the Combat-A Music Segment, right-click and select Import Audio Files. Then select Add Files and navigate to the Combat-AB-Rhythm folder located at Cube Music > Combat > Combat-AB-Rhythm. Find them at the bottom of the music segment and solo to listen. Because they don't take up the full 8 bars we need to loop them. Select the three tracks then drag the rectangle to the end of the music segment.

We can make variations on tracks that are provided. Copy the arpeggio clip and paste it into a new track called Arpeggio2. Repeat the steps to create one more arpeggio track.

Split the arpeggio2 tracks so that it plays only every other measure. You can split a clip at the playhead by moving the playhead where you want to split and pressing S. To make the entrances and exits of the clips less abrupt we can add in fades. Bring in the triangles at the top of hte clips to fade. Add a highpass filter sweep to arpeggio3 that goes from 0 to 100 over the first 4 measures then back down to 0 over the last 4 measures. Make sure the highpass envelope is enabled.

## Configuring Sub-Tracks

Make the arpeggio1 track a random step track and add two sub-tracks to it. Move the arpeggio2 and 3 clips into these new sub clips. Don't forget to delete the empty tracks. By default a different sub-track will randomly play each time it repeats. Add one more sub-track so that sometimes the instrument won't play at all.

You can force one of them to play by selecting the F button, but this won't be understood by the soundbank is just for auditioning purposes.

Apply this concept to all of your tracks in the music segment. If the track has variations group them together into sub-tracks. If it doesn't still group the track with a silent sub-track. Leave the Combat-AB-Rhythm-Main Music Track alone so there is always a beat going.

Take a minute to listen to your amazing variations!

If you want more control some tracks can be sequence step tracks. Turn Combat-A-Gtr1 into a sequence step track. Make sure the empty sub-track is on top so that it plays first.

## Building the Layered Approach into Cube

Replace the explore music event with the combat music playlist you just created. View all of your changes in a profiler session. Build the soundbank and test in your game.

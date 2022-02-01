---
title: "Lesson 1: Re-sequencing – Creating Variation Using a Sequential Approach"
---

First import the course material from the Wwise 201 course. and put it in the same folder as the other course material.

Create a new work unit called Music in the Interactive Music Hierarchy. Import the audio files from the explore folder.

## Viewing Waveforms on a Timeline

Open the interactive music layout. Click on a music segment and watch how you now have a playhead that can start playback from different parts of the track. If you don't see a clip on some tracks click the zoom button in the bottom right corner of the music segment editor.

## Defining the Timing Grid

Right click on the timeline to change the time value to "Bars and Beats". You made need to zoom in to see the beats. Set the tempo to 138 bpm in the time settings section. We know it's this tempo because it's written in the file name. Change the remaining music segments to the same tempo, try using the multi editor.

## Positioning Entry and Exit Cues

Notice that there is silence at the beginning and end of the Explore Arpeggio Music Segment. This is the pre-entry and post-exit. These were necessary because there is a swell at the beginning of the music segment and at the end there is a reverb tail. We'll now set entry and exit points with the green and red icons. Turn on "snap to bars/beats" and align both cues to the grid. Click control to move a cue. Do this process in the remaining music segments.

## Using Music Playlist Containers

Let's now connect these music segments to a playlist container. Create a new playlist container called explore with all the explore segments in it.

## Configuring Multi-Group Playlists

Music playlist containers have tempos. Let's set ours to be 138 bpm. We could also override the parent, but this is easier. Override the Explore-TransToBridge Music Segment and set its time signature to 3/4. Add the arpeggio, piano, rhythm and theme segments to the playlist in the default group.

You can now play the explore music playlist container and the segments will jump from one to another. Notice the two yellow playheads that happen for a moment. This is how Wwise fades between one segment to the next. Drag the theme to the top and notice how the order of the segments changes. Set the loop count of the whole container to infinite so that the music never stops.

Change the playback type to random continuous and listen to the changes. Currently the segments are all equally likely to play. We can weight certain ones though to make them more likely to play. Increase the Explore-Theme weight to 75, and lower the Explore-Rhythm weight to 25. Set avoid repeat to 0 so that segments will never repeat in sequence.

Create a new palyback group and add the arpeggio, piano, and rhythm segments to it. Set the group's playback type to random step. This means that only one item in this group will play before repeating the whole sequence.

We'll now randomize the segment playback further. Set the loop count of the second group to 2 and randomize it's offset from -1 to 1. Select the shuffle random playback type. Remember that this type removes the previous segment from the list of possible segments to play.

To test out the randomizations set the playback rate of the container to 4. it will move through faster so you can hear the changes.

Let's add the unique bridge music. Make a new random step group and add the explore-bridge to it. Add a sequence container here and add the Explore-TransToBridge Music Segment of the new Group followed by the Explore-Bridge.

Your playlist should look like this:

![](https://www.audiokinetic.com/images/wwise201/?source=wwise201&id=images/L1_image64.png)

Now the music follows this sequence:

1. The Explore music is played.

2. Either the Arpeggio, Piano or Rhythm part will be randomly selected. That process will repeat for 1 to 3 times as dictated by the randomly chosen loop value.

3. The music will either jump directly to the bridge, or go through a short transition before hearing the bridge.

## Viewing Behavior and Performance in Profiler

Play the music then open the profiler. You can clearly see all the decisions made by Wwise here. Stop capture and return to the designer.

## Building the Music Into the Game

We now need to make an event to play our music. In the events tab create a new work unit called music and inside of it create an event called music. Add the explore playlist to the music event. Test the music even to make sure it works. Create a new soundbank called Music. Drag the music event to the music soundbank. Go to the music level in single player and test it out!

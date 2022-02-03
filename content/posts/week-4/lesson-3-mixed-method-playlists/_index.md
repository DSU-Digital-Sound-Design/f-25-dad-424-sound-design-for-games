---
title: "Create a Mixed Method Playlist"
---

## Using an Existing Music Segment as a Template

How do we vary our music even more and not repeat the same chord progression? We'll review the last two lessons and add more variety with chordal variations on our combat theme. We'll have two 8 bar sections to allow for maximum variety using sub-tracks.

Instead of importing the new files to a new music segment, lets duplicate the one we already have so we can use it's settings. Call that duplicate segment "Combat-B". Delete all of the clips from Combat-B except for the Combat-AB-Rhythm tracks. Notice how the removed clips have turned red in the hierarchy.

If we imported our audio now the music track names wouldn't update to reflect the new audio. To fix this let's batch rename those red files then find and replace Combat-A with Combat-B.

Import the Arpeggio track from Combat-B and redo the variations from the previous lesson. For instruments that already have variations you can import their variations at the same time. Notice that when you do this Wwise places the variations in sequential order, instead of on the sub-tracks. Continue this process until you've imported all the Combat-B variations.

## Combining Sequential and Layered Structures

Add Combat-B to the Combat music playlist. We now have a 16 bar loop with lots of variations.

## Finishing the Combat Music

We'll now add music that bridges the explore and combat music. Import the Combat-Bridge folder into the combat music playlist. Make a sub-track to randomly play the three guitar tracks. Make sure to set the exit cues here!

Finally, add the Combat-TransToBridge segment to the playlist. Update the time settings to 3/4 and the tempo to 138 bpm. Adjust the entry and exit cues appropriately.

In the music playlist editor make a continuous sequence and add the combat-a and b segments to it. Add the bridge segment to a random step group. Then, inside of that random step group, create another continuous sequence group and add the transition to bridge then bridge segments. The music will now sometimes go directly to the bridge and sometimes play a transition before going to the bridge.

Give the second continuous sequence container a chance of looping 1 - 3 times.

---
title: "Working with MIDI"
---

## Importing a MIDI File

Wwise can play MIDI but cannot edit it. Because of this the MIDI needs to be created in a DAW.

Import the two boss-a MIDI tracks into the boss-a music segment. If you try to play it you won't hear anything because you have to hook up a synth to it in Wwise.

## Connecting MIDI Tracks to a Synthesizer

Switch to the designer view to add a synth one plugin. Create a new work unit called "Music" in the Actor-Mixer Hierarchy. Then add a Sound SFX inside of it called "Arpeggio Synth". In the contents editor click "add source" then "Wwise Synth One". You should be able to play a tone now. Switch the frequency mode to MIDI to hear a lower tone.

We'll now connect the MIDI track to the synth we just created. Select the boss-a-arp in the interactive music hierarch. Click on the plus to the right to show the MIDI tab. Now click on the MIDI tab. Under MIDI target override the parent then drag in the Arpeggio Synth sound SFX. If you go back to the interactive music view you should be able to hear the MIDI track with a synth on it.

## Editing Synth Properties

Pin the transport with the Boss-A music segment selected. Go back to the designer view and select the Arpeggio Synth. Doubleclick the plug icon in the content editor. This brings up the synth parameters. Play around with these setting until you have something you like. This is a good start but the sound is bad the default envelopes. Go to the RTPC tab and adjust the envelope to a very short and percussive sound.

Duplicate the Arpeggio Synth and call it "Melody Synth". Add it to the Boss-A-Melody segment. Edit the parameters of this synth to contrast with the previous one. Change the FM to 0 on this one and add an LFO. To do this an another RTPC called Osc1 Transpose. Create a new LFO, on the X axis, called "Synth Vibrato". This creates a shared modulator with a shareset.

This graph represents the intensity of the LFO, not the shape of the LFO. Set the intensity to go up to 150 and the frequency of the LFO to 6. Play around with these values until you get something you like. You can adjust them in real-time.

Now we'll use some CC data to make the LFO more or less apparent. Bring up the RTPC of the Synth Vibrato by clicking on the little rectangle to the right of the depth parameter. Add depth on the Y axis and MIDI CC# 1 to the X axis. The programmer of the music added in during the composition phase. This is how we read that continuous control message. This graph shows the mapping of the CC messages to the LFO depth. Change the graph so that it goes slowly from 0 cc 0 depth to 127 cc 100 depth. Use an exponential base 3 curve.

## Using the Same Synthesizer with Multiple Music Tracks

We'll now add some more MIDI files that use the same synthesizers we just created. Import the Boss-C Arpeggio and Boss-C Melody MIDI files into the Boss-C Music Segment. Assign the arp and melody synths respectively.

## Configuring a Sampler

We can also use a sampler! Remember MIDI is a way of saving processor power because we can have less SFX and perform them with MIDI. Go to Boss-D and force play the first of the sub-tracks that have MIDI.

Import the Suling_C#5 file into the Music work unit in the Actor-Mixer Hierarchy. Select the Boss-D-Sampler-Suling and make the MIDI target the sfx file you just imported. The MIDI track should now play that sound, but it won't transpose yet. Pin the transport and go back to the suling SFX to the MIDI tab. Enable note tracking. Set the root note to C#5 so that we hear the correct transposed pitch.

## Setting up a Multi-Sampled Instrument

We can even multi-sample instruments for more realistic sample sounds!! To do this we need to change the key range properties from C#5 to F5. We will now only hear notes that fall within that range. Delete the suling sound you currently have. Import the the other ones as a folder. Set the object type to "blend container".

Select the folder and open the keymap editor. For all sounds select Override MIDI note tracking check box and then the Enable MIDI note tracking. Adjust the root notes to match the names in the file type. Set the key min range the same as the root note. Set the max values so that they don't overlap the next sample. Count one halfstep down from the next note.

Add your synth to the Boss-D-Sampler-Suling segment and test it out.

Test in the profiler and export your soundbanks and have fun playing!

<!-- TODO: finish exporting and review -->

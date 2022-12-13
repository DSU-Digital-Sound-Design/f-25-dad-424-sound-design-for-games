---
title: "Lesson 8: Mixing"
---

{{< toc >}}

# Creating a Bus Structure

Now we'll create a finished mix for all of our musical elements.

Find the Master Audio bus and expand all of its children. Here you can see busses set up for different types of sound effects and environments. In this lesson we'll create more busses for the music, so that the music and sound effects can be mixed independently.

Create a new audio bus called "Music" in the Master Audio bus. We can have different music for different maps. To control our map we'll route the music to a "Wwise 201 Music Bus". Then we'll make busses for all of our musical cues Combat, Explore, Boss, Story, Defeated, and Victory.

Now we'll assign each Playlist container to its corresponding bus by overriding the parent then dragging the bus to the output bus section.

Since the stingers can play over various types of music we'll assign them directly to the "Wwise 201 Music Bus". We have to assign each one separately because they are in a normal folder that doesn't have its own routing system.

Assign the Boss-D Suling Samples to the Boss Audio Bus. Assign the Arpeggio Synth and Melody Synth objects to the Boss Audio Bus.

## Creating a music mixer

We need to create a mixer to control all the busses we just created. Go to the Mixer view and create a new Mixing Desk Session called "Music". Add all of the busses you just created.

Load the "Music Testing" soundcaster session. Play the different musical cues using triggers. Test that the busses you created are working. Be sure to return all the voice volume faders to 0 dB.

# Volume and Metering

## Configuring Meters in the Mixing Desk

We don't see any meters currently because our busses are not true summing busses. This is done because it is more efficient for CPU use when playing the game. We'll add meters to aid in our mixing process.

Bring the meter section into view. Select all of your busses and "show in multi editor". Set effect 3 to "Wwise Gain" and "Default Custom". We see meters now!

Don't forget to remove these gain plugins before exporting your soundbanks. This will help save on CPU usage.

## Adjusting the Meter View

We can either view our meters in Peak or RMS. Remember, peak metering responds immediately to transients. Because of this something with more transient material will seem louder if looking at the meters than something with a higher perceived loudness with less transients. To view a busses overall loudness we can use RMS an averaging style of metering.

We can setup different presets for meter assignments. Click on the 1 at the top right corner of the meter view. We'll assign the Music buss to "Meter Sync Group 2" and set the metering to RMS. We can now see the differences between peak and rms if we look at the normal bus meter then our new meter.

## Using Loudness Metering

RMS is useful, but it doesn't reflect totally how we perceive loudness, as it reacts to sounds the same no matter their frequency content. We perceive sounds as louder in mid-range frequencies. To account for that we can use LUFS (Loudness Units Per Full Scale) metering.

Chose View > Loudness Meter > Loudness Meter - Sync Group 2. Assign the Loudness Meter to the Wwise 201 Music Bus.

The momentary meter averages sound over 0.4 seconds, where the short-term meter does it over 3 seconds. Click "measure" to get an integrated measurement, or a measurement over a longer period of time. The meter keeps measuring until you reset it.

Loudness Range is a calculation of the material's dynamic range expressed in LU–Loudness Units.

Start capture to view the momentary and short-term loudness graphed over time. This graph helps to see how often each is measuring loudness.

The green area of the meter is the "target zone". This value depends on the target application. The game industry has no standard LUFS level, but a game company will have its own internal standards.

The target level can be adjusted in the settings. You can switch the Unit to LU, loudness unit. This now shows 0 as your target level on the meter.

Drag the loudness meter to below the master peak meter. You can now see all types of metering at once!

# Using a Compressor to Control Volume

Since we can't control how events happen in the game, we have to take care that musical and sfx do not combine to create a level that is too loud. We'll use a compressor to help with this issue.

Open the "Wwise 201 Music" bus and choose Wwise Compressor > Hard_Knee_Minus_3dB_RMS. Click edit to see the compressor's settings.

To hear the effects of the compressor lower it's threshold value to -40 dB. It's not compressing all of the music and sfx. Reduce the threshold level and see hte difference in gain reduction.

Start capture to view the average loudness and see what setting brings us closest to the target level.

# Adding Reverberation

Reverb is often added to a sound effect in the DAW to save processing power in the game. There are times where we want the reverb to be applied more flexibly though.

Go to the designer layout.

## Applying Reverb to MIDI Tracks

Because MIDI tracks don't have sound on them, we have to apply reverb within Wwise. We'll add our reverb on a bus to save on CPU usage.

The Synth tracks only play during the Boss-A and Boss-C Music Segments. We'll add reverb to the Synth tracks.

In the Boss bus create a new bus called "Boss Synths". Add a Wwise Matrix reverb effect with the "Medium_Room1" preset. Set the wet value to -16 dB.

Go find the Arpeggio Synth and Melody Synth and open them in the multi editor.

## Applying Dynamic Reverberation

We'll use a game parameter to change the reverb level in relation to our health. Select the "Wwise 201 Music" bus and apply a matrix reverb with the "Underground Parking1" preset. We'll now setup an RTPC to control the reverbs wet level.

Select the RTPC tab and create a new one for the wet level. Assign it to "PlayerHealth". Configure the graph to look like this:

![](reverb_rtpc.png)

# Panning Considerations

Again, most of the panning decisions happen in the DAW, but the synths need to be panned in Wwise.

Select the arpeggio synth and go to the positioning tab. Change the speaker panning to "balance-fade". Set the panning halfway between the center and right channels.

# Side-Chaining Stingers

we'll use a side-chaining system to make the stingers play over the music.

## Configuring Busses

Create a bus called 201 Main inside of the Wwise 201 Music bus. Add the other busses to this new bus. In the Wwise 201 Music bus create a bus for the stingers called "201 Stingers". Assign both stringer health segments to this new bus.

## Tailoring Meter Output Values

Add these new busses to the Mixer view. Add a gain plugin to 201 Main. Add the Wwise Meter plug-in to the 201 Stingers Audio Bus. Click edit to see more settings. Here we can actually change how our output volume acts, making it more easy to control how the side-chain will work. Set the release time to 0.5 seconds. Change the output max value to 6.

## Generating an RTPC

Create a new RTPC from this menu in the Music workunit and call it "Stinger_Sidechain". Double-click on it to change its settings. Set the Min value to -48, the Max value to 6, and the Default value to -48.

## Mapping the Sidechain RTPC to the Target Bus

Double-click the "Main 201" bus and select "RTPC" from the menu. Assign the bus volume to the "Stringer_Sidechain" RTPC.

Adjust the curve to match this image:

![](stinger_sidechain.png)

Test your work.

So that the sound doesn't cut out completely adjust the curve to reflect a maximum attenuation of approximately 15 dB.

Now play the game!!

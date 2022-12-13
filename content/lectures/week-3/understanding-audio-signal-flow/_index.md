---
title: "Understanding Audio Signal Flow"
---

Now we'll learn how the audio signal can flow through different components of the audio system in Wwise.

## Organizing with Actor-Mixers

Take a minute to explore some of the new sounds and how they're organized. Create an Actor-Mixer called "Items" and drag all of the SFX except for "Cube_Main_Theme" and "HeartBeat" into it. You can think of the Actor-Mixer as a container that can offset settings of the children contained within it. I think of it similar to a folder in a DAW, rather than a bus. The results are cumulative, so if you have multiple nested Actor-Mixers their parameters add up to the final result.

An Example:

![](https://www.audiokinetic.com/images/wwise101/?source=wwise101&id=images/L6_image03.png)

This chain of offsets does not effect the Output Bus Assignment.

Add Defeated, Jump, Pain, Footsteps, and Heartbeat to a new Actor-Mixer called "Main Character".

Color code each Actor-Mixer to make them easier to identify. This should be a familiar organizational tactic from working in DAWs.

## Using the Master-Mixer Hierarchy

Since no mixing actually occurs in the Actor-Mixer hierarchy, we need to study where this actually occurs, in the Project Explorer’s Master-Mixer Hierarchy. Click on the items object and see how everything in it is routed through the Master Audio Bus. Now find the Master Audio Bus in the Master-Mixer hierarchy. Select any playable object then go back to the Master Audio Bus and see it playing through the meters. Notice the two volume controls. The bus volume control is like the master mixer. The voice controls below are further offsets to any sounds that are routed through the bus. Using these could have confusing results.

We can explore this routing more with the Voice Profiler. Open it and start capture. Play the teleporter sound and examine the signal flow in the Voice Profiler. Change the voice volume and see it's value reflected in this signal flow chart. Then open the items object and reduce the voice volume there. See how the volumes are added together at the end of the chain. Finally go to the master bus and change the voice volume there. Again you can see that it has a cumulative effect on that one sound. Change the bus volume and watch it visually update in the Voice Inspector. You can see now why the voice profiler is so useful for visualizing the signal flow and checking the final level. Don't forget to reset all of your offsets and stop capture!

Submixing can give the player more control over the audio in the game. For example, all the music can be routed to a music bus, or all the SFX can be routed to a SFX bus. Create two new busses in the Master Audio Bus, "Music" and "Environmental". To give the user even more control we'll create another bus called "SFX" inside the "Environmental" bus.

Now that we've created these busses, we need to assign them. Assign the "Cube_Main_Theme" to the Music bus because its the main musical theme. Open the remaining Actor-Mixers in the Multi Editor. Find the output bus section and right click then set output bus -> browse -> SFX. This is quicker than doing them each individually. Reroute the HeartBeat to the master mixer. It needs to be louder for when we add reverb to it in the next section.

Using busses allows us to mix the elements more easily. We can "duck" all the sounds in one bus out of the way of another bus. Find the auto-ducking tab on the Environmental bus and insert the Music bus in the bus list. You now need to indicate how the volume of the Music bus will be affected when there's an audio signal on the Environmental bus. The default Volume change is -6 dB, which is where volume changes just begin to become noticeable. You’ll exaggerate the volume change just a bit more. Change the volume to -9 dB so that you get more volume reduction.

## Working with Effects

Add a delay to the Teleport SFX. Choose the "One_Tap_Quarter_Second" preset on the delay plugin. Open the effects editor and change the feedback value to 25 to elongate the sound. Select "render" to have this effect render to an audio file when you create your soundbank.

We'll now look at using aux sends to apply effects to multiple sounds at once. Select the Environmental bus and create a new auxillary bus called "env_corridor". Add the "Room_small" reverb preset to it.

Now go to the Main Character Actor-Mixer and assign "env_corridor" to the "User Defined Auxillary Sends". You should now hear reverb on any of the main character sounds. Try to turn up the aux send level and listen for the changes. Go back to the reverb preset and edit it to your liking.

This works for our purposes now, but Cube actually sends a message telling Wwise what the level of the aux send should be. For this to work we need to change the setup slightly. Unassign the send from the Main Character Actor-Mixer. Select the Use game-defined aux sends checkbox for all actor mixers.

## Using the Schematic View

We can view the routing of all of our objects in the Semantic View. Find the "Defeated1" sound. Select the Mute/Solo, Bus Volume, Voice Volume, Voice Pitch and Voice LPF check boxes, and click OK. Now we can change these parameters from the Semantic View.

Export your soundbank and hear how it sounds in the game.

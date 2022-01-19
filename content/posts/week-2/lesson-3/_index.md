---
title: Lesson 3
---

[Understanding Game Syncs](https://www.audiokinetic.com/courses/wwise101/?source=wwise101&id=understanding_game_syncs)

- Game syncs are ways of dealing with more complex game calls. They can transfer more information to the audio middleware.
- Footsteps are a good example. If the player is moving the game will send a call to the audio middleware to play a footstep sound. It also sends the information for what surface the player is on.
- Open the Lesson 3 project in Wwise.

## Using switches

- Creating a switch group, these are the most appropriate game sync for footsteps.
  - Create a new switch group called "Material".
  - A switch will define the types of surfaces the player can be on. Create one for concrete, grass, gravel, metal, sand, stone, tile, water, and wood.
  - These switches can now receive messages from the game engine.
- Now go to the Default work unit on the Actor-Mixer Hierarchy and import the footstep sounds as a "Switch Container". Changing it to a switch container will also change all the child folders to random containers.
- Connect the switches to the switch containers. On the footsteps object set the switch group to "Material". Set the default switch to concrete. See the assigned objects list.
- Now drag the random containers in the content editor over to the objects in the assigned objects list. Have it match this:

![](https://www.audiokinetic.com/images/wwise101/?source=wwise101&id=images/L4_image16.png)

- Your switch container should now play the footstep sound for the concrete surface because you set it as the default surface.
- We still don't know if a footstep has been taken so we need to add an event called "Foot_Player". Add the footsteps switch container to the "Foot_Player" event.
- If you select switches in the Transport Control you can now audition the different footstep surface sounds. After your done click "reset all" to reset the switches.

## Using Game Parameters aka RTPCs

- Any parameter that varies over time. We'll use it for our wizards health.
- Create a new game parameter called "PlayerHealth". Here you set the range of the parameter. The range is from 0 to 100 with a default of 100.
- Add the Heartbeat sound file and set it to loop.
- Now map the Y Axis of the RTPC to "Voice Volume" and the X axis to the "PlayerHealth" Game Parameter. You should now be able to see the mapping of the game parameter to the RTPC.
- The way it is set now we'll hear the heartbeat when the player's health is good, so let's adjust it. Create a break point in the center then adjust the point where the player is at 0 health to have a 0.0 dB heartbeat. Now the heartbeat will get louder until the player is dead, but not be heard until the health is at 50 or less.
- Change the curve to an Exponential curve. Now adjust the players health to test your new mapping.
- Create another mapping for the low pass filter parameter. Adjust the curve so that the heartbeat sounds more muffled when it is first heard then less muffled as the players health gets worse.
- You can also adust RTPCs from the transport control.

## Using States

- States are a way to group together a set of parameters. We'l use them for our wizard's state, alive or dead.
- Create a new state group in the Game Syncs tab called "PlayerLife". In that group create a state for alive and defeated.
- States changes can be immediate or have a transition time. Insert a transition to the State Group Property Editor that goes from Alive to Defeated over 5 seconds.
- Now we have to map these state changes to properties.
- Select the Heartbeat sfx then click the "State" tab. Click "Add State Group" and select the "PlayerLife" state group. We can now change some default parameters.
- Change the parameters of the defeated state to make the sound muffled and far away then eventfully fades to nothing. Set the volume to -96 dB and low pass filter settings to 100. The LPF is a percentage value from 0 to 100.
- Test the state changes using the transport control.

# Displaying Voice Volume Calculations

- Panes can be split if necessary to see the different RTPCs and states.
- Open the voice profiler layout and setup the capture settings to capture voice inspector data.
- Click the capture button then play the HeartBeat sfx object. Change the states and parameters to see a log of the voice inspector data.
- Stop capture when you're done inspecting the voice inspector data.

# Integrating Your Game Syncs Into Cube

- Right click on the Heartbeat sfx object and create a new Play event called "Map_Loaded".
- Copy this event and make change the type to "Stop". Add this event first. This will ensure that any event that was playing before is stopped, so there can't be two heartbeats playing at the same time.
- Now you can export the new events to the Cube project as soundbanks.
- Walk around then find some bad guys and test the heart beat sound.

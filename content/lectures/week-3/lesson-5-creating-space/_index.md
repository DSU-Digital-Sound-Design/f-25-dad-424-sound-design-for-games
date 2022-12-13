---
title: "Creating Space"
---

## Using 3D Spatialization

Games have emitters, things making sound, and listeners, who hear the sound. In a single player game there is only one listener but there can be many emitters. Emitters and listeners are positioned in 3D space using x, y and z coordinates. Knowing the positions Wwise will set appropriate volume and panning settings. While Wwise does a lot for you, we still have to decide how this spatialization will work, how far away does an emitter have to be before you can't hear it anymore?

Under the ShareSets tab create a new attenuation called "Object_Attenuation". We'll use this attenuation curve to determine how close we can be to a teleporter before we hear it. Add the teleporter sound in the Actor-Mixer Hierarchy. In it's positioning tab chang the 3D spatialization to "position + orientation". Assign your "Object_Attenuation" curve to the "Attenuation" parameter. Click edit to change the attenuation curve parameters.

Change the max distance to 50 units. This is the maximum distance we can hear the teleporter. Play the teleporter sound and move the listener distance to hear how it will sound in the game. Let's modify the curve to make it a little more realistic. Double-click the parameter curve to create a new control point and set it to a distance of 30, with an Output Bus Volume of -17.

Now add a low-pass filter curve. Keep its settings the same. Now that we've added this curve it makes more sense to have the distance at 100 units. Play with these values until it seems right to you.

We can also change the directionality of a sound. This is done using cone attenuation. We can use it to emit sound from one side of the teleporter. The attenuation preview represents visually how the emitter will sound. It also shows the inner and outer angle of the cone. No attenuation occurs in the inner angle. Attenuation starts to occur between the inner angle and outer angle. Your attenuations are at their maximum at the outer angle.

Now we'll ad an event to the teleporter object. Right click on it in the audio tab and create a play event. Rename it to "Teleporter".

## Using 3D Position Automation

Sometimes we'll want to add spatialization to sounds that don't have their own game objects. In our case we'll want to do this to the gem sound that is in our Gem Drop sequence. To accomplish this we'll use 3D Position Automation. Add "Position + Orientation" and "Object_Attenuation" to the Gem Drop object. This is why we created the shareset, so we can share attenuations between objects.

Change the 3D Position to "Listener with automation". Open the automation window, here you can create paths for objects to follow in the 3d audio space. Create a new path. Move the starting point closer to the listener then create 3 more control points to define the movement of the gem. Since the gem drop only lasts for two seconds lets shorten our timeline to 2 seconds in the configure timeline window. Add a little bit of randomness to the points in the random range section. Create 6 new paths, by copying and pasting, with different paths to make the sound more realistic. Set the play type to random, so a random path will be chosen each time. Also set the play mode to continuous. Test out your sound by itself and then with the whole Fire_IceGem_Player event. Hear how the change in positioning helps us hear the gem sound more clearly.

## Using Speaker Panning

Sometimes our sounds don't need to be 3d, think narration, music, or UI sounds. For this we can just use speaker panning. We'll use this for our woosh and magic sounds because their position relative to the listener is always the same. Add your Gem_Recharge_Magic and Gem_Recharge_Woosh sounds to an Actor-Mixer object. This will allow those objects to share settings. Choose "balance-fade" panning in the positioning tab. This will allow us greater flexibility in positioning the sounds. Move the position up and to the right. Experiment with this while playing the whole Fire_IceGem_Player event.

## Play the Game

Add the teleporter to your main soundbank and export to test out your game.

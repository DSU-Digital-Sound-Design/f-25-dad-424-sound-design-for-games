---
title": "Player Sounds"
---

# Player movement sounds

We need to implement the basic player sounds, which include footsteps, jump, land, and land damage. Unlike in our Wwise 101 Certification, we don't need to provide footsteps for various surfaces. So, you can just use a single random container with multiple generic footstep sounds to create the desired effect. Follow the hierarchy in the Wwise 101 project closely to get practice on working on a project with more sounds.

## Footsteps

First create the container and events in Wwise, then figure out where to send the Post messages from in Unity. See the `PlayerCharacterController` script for most of this functionality.

> To find footsteps sounds, go back to the Wwise 101 Certification to the Audio for lesson 3. Use any of the footstep types here.

After implementing the sounds, you may find that these new footsteps happen too quickly to sound realistic. Adjust the `FootstepSfxFrequency` in the Unity editor until the footsteps sound like you want them to.

## Jump + Land

Use audio blocks, or free sound, to find some fun jumping and landing sounds. Use at least 3 sounds for jumping and 3 for landing. Implement them both with Random Containers then trigger their events in the correct place in the Unity script.

> As you begin to add more elements, go back and do some premixing by adjusting the voice volumes to make sure everything is sounding good together.

Be sure to save your changes to the script in the Player Prefab.

## Land Damage

Land damage only happens when you fall off of something. To test this you'll need to be in the secondary scene.

> Don't forget to load the sound bank into this new scene.

Check the receives fall damage checkbox in the Unity editor then find a place in the game where you can test out the landing damage.

Find a sound that represents that landing damage and implement it in the Unity script.

# Laser gun

Pew Pew! In the secondary scene we'll implement more complex weapon sounds, but first we'll implement the laser gun in the main scene. Find the Prefab where the laser gun is triggered and implement the sounds in the Unity script.

Now add the cool down sound for when the blaster has shot too much in a span of time. This is implemented on a different script in Unity. You'll need to find the script and implement the sound in the Unity script. This script in Unity is implemented so that if it stops charging, the sound stops. Recreate this by stopping the event in Wwise.

> This script has a conditional statement that relies on a Unity Audio Source existing. This means that it won't work correctly for our needs. Just write a slightly simpler version of the if statement that doesn't include a reference to the Audio Source and it will work.

# Health

Have some sound relate to the player loosing health. I chose a sound of heavy breathing, but you could choose something else. Follow the [tutorial here](https://www.audiokinetic.com/courses/wwise101/?source=wwise101&id=modifying_object_properties_with_game_parameters#read) for a refresher on how to work with game parameters. See [this tutorial](https://www.audiokinetic.com/courses/wwise301/?source=wwise301&id=Setting_Game_Parameters_using_WwiseTypes#read) for more information on how to use this game parameter in Unity.

I triggered the breath sound to play at the start of the game. But you only hear it once you start taking on damage. This is controlled by the RTPC. Also, once my player dies, there is a sound that plays. These are both related to the `currentHealth` variable in the Unity script provided by the game designers.

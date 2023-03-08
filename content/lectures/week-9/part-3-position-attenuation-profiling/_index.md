**Source**: [(116) Game Audio with Unity and Wwise Part 3: Position, Attenuation, and Profiling. - YouTube](https://www.youtube.com/watch?v=RoUUdfInrTs&list=PLzlEBXWjqM97U5rHMERc82sTXRBoSB_Fu&index=3)

# Position, Attenuation, and Profiling

## Adjusting the gain

We'll add some ability to attenuate the sound depending on how far away we are from it. Go to Wwise, find the sound, and then look at the _General Settings_ tab. Adjust the voice slider to increase the sound level of the breath in your game. This is the gain of your _GameObject_.

## Looping the sample

Also, check the loop checkbox so that your sound loops continuously. Check that your sound will loop correctly by going into the _Source Editor_ and moving the loop end point.

## Attenuating the sound

We want the sound to be more realistic, to get quieter as we move away from it and louder as we approach it. We can do this by setting an attenuation curve on the sound back in the positioning tab. We'll create our curve with a ShareSet so it can be used between many sound sources and have it act the same way.

Create a new ShareSet and call it _Box Attenuation_. Click on the up/right facing arrow to open the _Attenuation Editor_.

![](attenuation-editor.png)

Reduce the max distance to 10 meters. Play the event and test your curve by moving the player distance in the _Attenuation Editor_.

Right-click on the line to see the different curve options. Choose the one that best suits your needs. I choose _Logarithmic (Base 3)_.

Test it in Unity now.

## Adding a low-pass filter

Add a low-pass filter to add realism to the distance attenuation.

## Cone attenuation

It allows you to create a more directional sound. Add cone attenuation to your attenuation curve and listen to how the box now only emits sound out of one direction, like a musical instrument or our voice.

> The Attenuation Preview is designed to give you a visual representation, as well as a way to simulate the relationship between an emitter and a listener. It’s natural to think that the graphic for the cone attenuation puts the listener in the center of the circle, with the white dot representing the emitter; however, it’s just the opposite. As a whole, the diagram represents how the sound-emitting object in the game will project its sound into the world with that sound source positioned at the center of the circle. The position of the listener is defined by the white dot.

> The pie-shaped area at the top of the Attenuation Preview shows that if a listener is within that forward facing zone, no additional changes to sound emitter properties will be made. The pie-shaped area at the bottom of the Attenuation Preview shows that when the listener is behind the emitter, the emitter's object properties will be modified by the values displayed just to the left of the Attenuation Preview area. The areas on either side of the Attenuation Preview represent a transition area that will gradually change property values from those used in the top and bottom areas.

[Source](https://www.audiokinetic.com/en/courses/wwise101/?source=wwise101&id=adding_cone_attenuation#read)

## Sound source orientation

Notice that our sound source is in stereo, but when we use the position setting for 3d spatialization, it makes the sound mono. This makes sense when you think of examples of directional sound. Most of them come from only one source.

You can hear this by adjusting the slider for the _3D Spatialization Mix_.

To use the stereo information of this sound, we'll need to change the 3D Spatialization setting to _Position + Orientation_. This will put two speakers, separated by about 1 meter, on the object pointing to the X-axis.

> More info on spatialization [here](https://www.audiokinetic.com/en/library/edge/?source=Help&id=working_with_3d_objects)

## Emitter automation

We can also automate the emitter position within a _GameObject_. For example, if you wanted to have a sound of a mosquito buzzing around, you could make the game object take up the space of a pond, then automate the position of the mosquito in the pond.

Set the _3D Position_ to _Emitter with Automation_. Then, open the _Automation_ editor. Create a new _Automation Path_. Move the dot around, and restart your sound to hear the change. Create more paths, moving the listener position each time. If you press play, each time will jump to a different listener position as defined by the paths. Try the random play type. This will jump randomly to different paths. The continuous play mode will jump between paths without restarting the sound.

> Check hold listener orientation

Each path can have multiple points. Draw these points by double-clicking in the window.

Find a a buzzing insect sound. Add this to your Unity project with an event.

> See [best practices](https://www.audiokinetic.com/en/library/edge/?source=Help&id=positioning_tips_and_best_practices) for positioning.

## Profiling

Sometimes we need to see if something is working when we can't hear it. Profiling is a way of seeing if Wwise is doing what we think it's doing. We can also use Profiling to optimize game performance.

First, we must connect Wwise with the Unity Game editor in real-time. Click the remote connections button, then connect. Now, switch to the profiler layout. If you click play in Unity, you can see your SoundBank load, your event trigger, and the breathing sound that the event triggers. As you move closer to the sound source in the game, you can see that the output peak goes up. Wwise records all of this data, so you can play it back after you stop Unity. This is very useful for diagnosing issues.

> Remember, remote connections must be turned off to be able to create and update sound banks.

## Triggering a play event from within Unity

Currently, the play event is triggered immediately when the game starts. This may not always be the preferred method. Let's change it to trigger when we move close to the cube and stop when we move away. This method can also help with optimization, to have fewer things playing simultaneously.

To make this possible, we'll have to create a new cube to trigger sound. First, we'll disable the cube we've been using. Uncheck the AkAmbient script on the cube GameObject.

Go into the project tab &#10132; Assets &#10132; StarterAssets &#10132; Environment &#10132; Prefabs, then drag the first box into the scene. Reset the transform of the cube to 0, 0, 0. Do this by right-clicking on the transform property and selecting _reset_.

We'll now add this cube to a parent object that will control the cube's trigger area. In the menu, select GameObject &#10132; Create Empty Parent and call it _Sound Box_. Move the _Sound Cube_ so it sits on the ground away from the player.

Add the horror event to the _Sound Cube_ object. Test the object by clicking play. You may need to turn off cone attenuation to make this more noticeable.

Change the trigger event of the _Sound Cube_ to _AkTriggerEnter_. Also, add a _Sphere Collider_ component and check the _Is Trigger_ checkbox. Make the radius of the sphere collider large to see it.

We also want to ensure that only the first-person character is triggering this sound, not any NPCs or anything else. To do this, add an _AkTriggerEnter_ component and set its _Trigger Object_ to _Player Capsule_.

Check in your profiler to see that the event triggers only when you move into its trigger area.

## Triggering a stop event from within Unity

We'll create a separate stop event that stops the sound when we leave the trigger area of the _GameObject_. Add this event to the SoundBanks and export. Add the stop event to the _Sound Cube_ object and set it to trigger on exit.

Again, open the profiler and check to see that the event is starting and stopping.

## Cleaning up the project

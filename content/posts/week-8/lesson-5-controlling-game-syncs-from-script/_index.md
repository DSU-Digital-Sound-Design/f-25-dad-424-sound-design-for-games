---
title: "Lesson 5: Controlling Game Syncs from Script"
---

# Controlling Game Syncs from Script

Let's get more control over our game sound using Game Syncs.

# Setting States using the AkState Component

While you can set state with scripts, we'll first set it using a component, the AkState script.

Open the "Setting States using the AkState Component" lesson in the Wwise project.

Select the " MusicRegion_WwizardMagicHouse" game object. You shoudl see a green outline that represents the Mesh Collider. Add an AkState component and select the Mz2_InsideHouse State. Set it to trigger on enter. Then add the AkTriggerEnter script and add the player as the trigger object.

Do the same process but set the state to trigger on exit. Add the MZ_Outside house state. Add an AkTriggerExit script and add the player as the trigger object.

Play the game and listen for the changes to the sounds that happen when you enter the Wwizard House.

# Setting Game Parameters using Wwise-Types

Go to the "Setting Game Parameters" lesson in the Wwise project. We'll use game parameters to change the ambience in the game depending on the time of day.

Find the Sun game object and add a new script to it called "SetTimeOfDayRTPC". Open the script to edit it.

Setup an RTPC by adding the following to the class:

```c#
public AK.Wwise.RTPC TimeOfDayRTPC;
```

This gives your game object the ability to reference an RTPC. Save the script and see how the script component has a new property called "TimeOfDayRTPC".

To actually use it we need to add another line to the Update() function:

```c#
TimeOfDayRTPC.SetGlobalValue(GameManager.TimeOfDay);
```

This method effects all game objects that are using the RTPC. We're setting this value with the GameManager.TimeOfDay variable from our game. This was setup by the game designer to hold the value of the time of day. We can view where this comes from by right clicking on it then "go to declaration". Save and return to Unity.

Add the "Time_Of_Day" RTPC as a property to the script component.

We'll test this in the Game Object Profiler in Wwise. Select the watches tab in the "Game Object Explorer" (I had to reset the layout to the factory layout to see this tab). Add a "Global Game Object". In the "Game Sync Monitor" add "Time_Of_Day" to the "RTPC" list.

Connect to Unity and play the game. Switch to Wwise and view the game sync monitor. You should now see a steadily increasing line that represents the time of day.

# Setting a Switch using a Wwise-Type

We've added footstep sounds that match the animation int he previous lesson, but the sounds are not responding to the surface material. To do this we'll have to set a switch.

Let's look at how the footsteps are organized in the Wwise project.

Open the "Setting a Switch using a Wwise-Type" lesson in the Wwise project.

Go to Wwise and select the Profiler then connect to Unity. Play the game and run a little then stop. Filter the events for just the Switches. Notice that the "Surface_Type" switch is not in the list. It should be changing the surface type.

Select the Road Space in Unity so you can see it's outline. Open it's SoundMaterial script. We won't be editing this script directly, but controlling it from out PostWwiseEvent script.

Open the PostWwiseEvent script and add this line to the PlayFootstepSound() function:

```c#
PlayerManager.foot_L.GetMaterial().SetValue(gameObject);
```

This method was created for you by the Wwise tutorial. It returns the material of the surface the player is on.

Play the game while connected with Wwise then view the changes in the profiler.

# Understanding Global and Game Object Scope

## Switches

The "Surface_Type" switch is shared by the player footsteps but also the player's weapon. How do we make sure that there is no interference if the player is using their weapon while moving?

Open the Main Scene from the Audiokenetic menu. Play the game and connect with Wwise. Skip through the dialogue. Run on a few surface types and hit the stone. Now let's look at the events in the capture log. Make sure you're filtering the capture log for switches. Notice that after you swing at the stone the "Surface_Type" switch is set to "Stone". If you move it's set back to "Grass".

## Game Parameters

Remember, game parameters can be both global and local.

Open the "Understanding Global and Game Object Scope" lesson in the Wwise project.

Open the Game Object Profiler to see how the EvilHead_Hover_LP sfx is effected by an RTPC with a tremolo effect. Open the watches tab and clear what was in there from before. Add a type of "Game Object Name" and watch "EvilHead". Remove anything in the Game Sync Monitor list. Add the "Enemy_EvilHead_MovementSpeed" game parameter.

Play the game in "God Mode". Connect with Wwise. Play the game for 5 to 10 seconds.

View the three graphs for each evil head you saw. An upward curve represents the heads moving towards you. The curve decays when the head isn't charging. An abrupt curve increase represents an attack on the head. Here we can see that each head has its own value, so is local. In the code the following method is used:

```c#
private void SetMovementSpeed(float speed) {
    MovementRTPC.SetValue(gameObject, speed);
}
```

`SetValue` is for local setting of the RTPC.

# Component or Script

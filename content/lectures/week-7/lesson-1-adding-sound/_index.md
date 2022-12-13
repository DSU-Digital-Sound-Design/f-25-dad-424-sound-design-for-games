---
title: "Lesson 1: Adding Sound"
---

{{< toc >}}

# Quickest Way to Enable Sound

![](script-execution.png)

Unity has an order of execution for scripts.

## Loading a SoundBank

To connect Wwise to Unity we need to load a SoundBank. The sound bank is loaded on a specific game object in Unity and at a certain triggered time. Most of our sound banks will be added as components to the GeneralSoundBanks Game Object.

Open the "loading a SoundBank" lesson.

We'll set our sound bank so that it plays before the game starts. This happens in the "Awake" function of Unity.

Find the "General" sound bank in the Wwise Picker tab and add it to the GeneralSoundBanks Game Object by dragging and dropping. This adds an AkBank script that handles loading the sound bank into Unity for you. This script tells Unity when to load the sound bank and which sound bank to load.

Set your sound bank to load on Awake.

In Wwise generate All sound banks. Open the profiler then click Remote to connect to Unity.

Click play in Unity then go back to Wwise. Check the Memory tab in the profiler. If you can see the General.bnk then everything is working correctly.

## Playing Your First Wwise Event

Select "Playing your first Wwise Event" from the lesson menu.

Drag the 301_Campfire Prefab into the scene. In the Picker find the "Ambient_Campfire_Play" event and add it to the campfire Game Object you just added to the scene. Make your Scene and Game tabs both visible so that you can move the campfire Game Object around. Listen to its volume change depending on its distance from the listener.

Notice how this sound plays from the start, not on an event.

# Trigger Conditions

Now we'll trigger sounds with trigger conditions. Add the "301_Coin" PreFab to the scene. Make sure the green trigger area doesn't overlap with the player.

## Adding a Trigger Condition

We'll now add sound to this object by adding a script and then choosing the event from the inspector. Add an AkEvent component to the "301_Coin" Game Object. Select "Pickup_Coins" as the scripts event to trigger. Set the trigger condition to "Enter". Make sure to deselect "Awake".

Test it out!

## Restricting the Trigger Condition

We need a way of restricting triggers so that we don't trigger events more often than we want to. We can do this with an AkTriggerEnter script. Add one to the coin prefab. Add the Player as the trigger object. The coin will only trigger the event when the player enters the trigger.

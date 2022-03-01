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

# Setting a Switch using a Wwise-Type

# Understanding Global and Game Object Scope

## Switches

## Game Parameters

# Component or Script

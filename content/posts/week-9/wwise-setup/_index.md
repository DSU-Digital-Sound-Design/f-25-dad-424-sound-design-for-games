---
title: "Wwise Project Setup"
---

## Make an asset list

If you look in the asset folder you'll see these folders, which categorize the sounds.

- Music
  - Ambient Wind
- SFX
  - Enemies
  - Pickups
  - Player
  - UI
  - Weapons

You'll want to create an asset list containing these sounds, so that it's easier to keep track of what you have done and what you still need to do. This will become much more important on a project where you're creating original content. Use [this template](https://docs.google.com/spreadsheets/d/1hxgcsX4SzMrLBjwMvX-E6rldh4ZIEe0XR-0E4bIuxIw/edit#gid=0) as a starting place. It comes from a blog by Thiago Schiefer. Check out [that page](http://thiagoschiefer.com/home/documentation-and-organization-in-game-audio-with-templates/) for more information on organizing your assets and working in game audio.

You can use this list to plan out your Wwwise project before you start adding elements. To figure this out you'll need to play the game and find how each of the sounds are triggered. Figure out which sounds can share the same events and what types of containers you can put them in.

Go through the list and systematically list how the sounds are triggered. All of the sounds are triggered by a script except for the ambient music. Some of the scripts take a little digging to figure out where the sound is triggered from.

## Finding the sounds

To get a better understanding of how the sounds are triggered you can use the Unity profiler. See details for use [here](https://docs.unity3d.com/Manual/ProfilerAudio.html).

Another helpful tool for hunting down where Unity is calling an SFX from is the [Project Curator](https://github.com/ogxd/project-curator) script. It gives you a list of the dependencies and referencers of each asset.

One more trick is to use the "Find in files" feature in Visual Studio. This searches all of the files in the project for a specific string.

Use all of these techniques to figure out where the laser shooting sound is triggered from.

## Setup your Wwise project

Now that we have a list of all of our assets, let's set up the Wwise project to organize these assets. This might be overkill, but learning good organization is important for getting to bigger projects. Let's open the Wwise adventure game project and try to copy their project structure.

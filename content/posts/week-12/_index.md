---
title: "Adding Music"
---

Add two pieces of music to the game. One should play at the start of the game and be more relaxed. When The player encounters the boss the music should change to a more intense style.

Implement this transition with a `Music Switch Container`. To trigger the transitions between music create corresponding states for the music and for the player life. You can have a state where the player is alive and it hasn't seen the boss yet. Then another where it's seen the boss but still alive.

You will need two different state groups to handle playing the music container. One called `PlayerLife` that has a state of `Alive` and `Defeated`. Another state group is called `Music_State` and has the states `Boss` and `Gameplay`.

Program the "Music Switch Association Editor" so that the ambient music plays when the states are set to "Gameplay.Alive" and then play the boss music when the states are set to "Boss.Alive".

Finally, two events will trigger each of the music tracks. The first event could be called `Music`. It should set the state to `Gameplay`, stop the `Game Music` container if it's already playing, then finally play the container. Another event could be called `Boss_Start`. This event will just set the state of `Music_State` to `Boss`.

See [this lesson](https://www.audiokinetic.com/courses/wwise201/?source=wwise201&id=lesson_6_implementing_transitions_part_i#read) for more information on how to do this.

In Unity set the state of `PlayerLife` to `Alive` using the State Wwise type. Select the appropriate type in Unity then in the code place `StateName.setValue()` in the `Start` function.

You shouldn't have to set any other states manually in Unity because you have them attached to events in the Wwise editor.

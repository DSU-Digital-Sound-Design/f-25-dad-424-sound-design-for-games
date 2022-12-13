---
title: "Lesson 7: Transitions Part II"
---

{{< toc >}}

# Smoothing Transition Decisions

We want different music to play when we're exploring vs when there are monsters around. This switch has to happen very rapidly, but not sound abrupt. We only have the calls "Monster_Aware" and "Monster_Unaware" coming from the game engine. We'll then convert those events as follows: Event > Game Parameter > Switch Group > Music Switch Container.

Because explore and combat are similar in their form and instrumentation it's easier to transition between them.

Select the Wwise 201 Music Switch Container, then the transition tab. Add a new transition with a source of explore and a destination of combat. Set the transition to immediate. Create a fade-out and edit it. Set the time and offset to 0.5.

To make the transition happen at the same point in the next music select sync to "same time as playing segment".

Repeat these steps to create another transition that goes back to combat from explore.

This style of transition works for these pieces but not well for the bridge sections because of their different chord progressions. We'll create transition rules to fix this.

Add another transition from combat-bridge to explore. Use the same settings from before, expect add a fade in with a 0.5 second fade. Set the destination jump to as "specific playlist item". Select "Explore [1. Explore-Bridge_138bpm4-4_L17M-P0]". We are forcing the transitions to happen between bridges of our musical pieces.

Repeat the process, but with the "TransToBridge" music segments. Then do two more transitions that go from the bridge sections of explore back to combat.

We'll now create a custom switch group for the music.

In the game syncs tab open the Music work unit. Add a switch group called "Gameplay_Switch" with children of "Combat" and "Explore".

Select the Wwise-201 Music switch container. Select the "Alive.Gameplay" path and remove it. This was a placeholder from the previous lesson. In the Music Switch Container Association Editor add the Gameplay_Switch switch group.

Select the Alive and Gameplay states then drag the combat music playlist onto the combat switch. This creates a path of Alive.Gameplay.Combat. Repeat for explore.

Test in the soundcaster with the following settings for your states:

![](soundcaster-1.png)

Toggle from combat to explore and listen for the transitions.

## Configuring RTPC Values to Control a Switch

We'll control the "Gameplay_Switch" group with an RTPC instead of setting the switches directly with events. To do this we'll use "Slew Rate", which allows us to transition from one value to another over a period of time. This reminds me of envelopes or automation in the music production world.

Go to the game syncs tab and create a Music work unit in the "Game Parameters" folder. Inside of it create a new Game Parameter called "EnemyAware". Set the min range to -1 and stretch the values. Set the max range to 101 and stretch again. Set the default to 0 so the player will start in exploration mode.

Set the interpolation mode to "Slew Rate" to make the values happen gradually over time. Set the attack to 1000 and the release to 10. The larger the number, the faster the transition.

Now let's map the EnemyAware RTPC to the Gameplay_Switch Switch Group. Select the Gameplay_Switch group and add the EnemyAware RTPC. Set the transition point at halfway.

Play the music event to test the transitions. Make sure that the PlayerLife State Group is set to Alive and the Music_State State Group is set to Gameplay.

## Creating Events for Enemy Awareness

We'll now actually create the events that the game engine will send calls to trigger. Create a "Monsters_Aware" event in the Music work unit. Drag the "EnemyAware" game parameter into the event and set its Game Parameter Value to 100. Do the same for the "Monsters_Unaware" event and make sure its Game Parameter Value is set to 0.

We need to make sure that if a player respawns its slew rate is reset so that the player starts back in exploration mode. Find the Defeated_Player Event and add the EnemyAware game parameter. We want to make sure the defeated sounds finishes so we'll put a 0.5 second delay here. We'll also bypass the game parameter so that we cancel the previously triggered game parameter.

Test your new events in the soundcaster.

## Viewing RTPC Values in the Object Profiler

This is all difficult to visualize, thankfully we have the Game Objects Profiler. Open it from the layouts tab. The first time we use it we need to configure it to display Voice Inspector Data. In the settings window select Inactive Game Syncs and Voice Inspector Data.

Open the soundcaster and right click on the EnemyAware game parameter then profiler -> set as object filter. It's now visible in the game sync monitor. Start capture and view the slew changes in the monitor.

# Using Transition Segments

We'll now implement the story music. This music is different from the combat and explore music, so it needs a different type of transition. The composers have actually provided us for transition music for this purpose and it will be implemented in the wwise transition system.

## Audition the Transition Music

Listen to the story music and hear how it has a more chill feeling to it than the other playlists.

## Configuring the Transition Segment

Go to the Wwise 201 Music container and then the transition tab. We can either get to the story music from explore or combat, but we'll start with explore. Add a new transition that goes explore -> story and set its exit source to next bar. Set the fade out to 1 second with a 0.6 second offset. We'll then use the transition segment to specify which music in the story playlist we'll transition to. Drag in the segment called "transToStory".

Repeat the same steps to go back from story to explore. Specify transFromStory as the transition segment.

Test this out in the soundcaster.

To make sure that the transitions we added only happen when we want lets move them further up in the list. Transitions towards the bottom of the list take precedence.

## Configuring the Events for the Storyline

The story music starts when the first door to the empty room is opened. We'll create a new event called "Story_Start" then add a Set State Action to set the Music_State State Group to Story.

To tell Wwise when the story is over we'll add another event: "Story_End". Add the GamePlay state to that event.

Add these new events to the soundcaster and test.

Export your changes to a soundbank and test the game.

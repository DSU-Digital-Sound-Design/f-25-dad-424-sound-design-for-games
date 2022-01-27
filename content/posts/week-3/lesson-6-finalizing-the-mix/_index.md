---
title: "Finalizing the mix"
---

## Using Soundcaster

This will let us play multiple objects at the same time. We need to do this to finalize our mix. Open the soundcaster view and create a new session called Player. Add the Defeated_Player and Foot_Player events to the session. See how you can change the switches and RTPCs for the imported events. Experiment with playing events at the same time.

Create a new session called "Fire Gem" and Add the Fire_FireGem_Player, End_FireGem_Player and Hit_FireGem_Player Events to the Fire Gem Soundcaster Session. We will need to add the actual Actor-Mixers that make up the events to be able to change their properties in real time. Move the FireGem Magic Actor-Mixer object to the end of the first row, and move the FireGem Blast, FireGem Explode, and FireGem_Flight objects to the left one space on the grid so that the sounds associated with each Event appear closer to the Event object that triggers it. Now you can experiment with playing multiple events at the same time and changing their properties.

## Configuring a Mixing Desk

Open the mixer layout and create a new Mixing Desk session called Fire Gem. In the Project Explorer’s Actor-Mixer Hierarchy, select the FireGem Magic, FireGem Blast, FireGem Explode, and FireGem_Flight objects, and drag them into the Fire Gem Mixing Desk. Also add the master bus and environmental bus. Put the master bus at the end.

Create a new Mixing Desk called "Bus Masters" and drag in each of your busses into the Mixing Desk. Double click on the environmental bus to bring up it's property editor. Add the PlayerLife state as a state group in the states tab. This state should not come up in the "editing states" section of the Mixing Desk. Change the PlayerLife State to Defeated and then scroll down and adjust the Bus Volume to -8 and Low-pass filter value to 65. Now click push states to so that states effect playback. Click the Fire_FireGem_Player event and and change states from alive to dead. Hear the change.

---
title: "Enemy Sounds"
---

## Hover bot

See the sounds that are associated with the hover bot: Alert, Attack, Death, and Movement.

The hoverbot movement sound will happen all of the time when the hoverbot is moving. Because of this you need to set the positioning settings so that you can only heart the hoverbot when you're close to it. Refer back to the lesson on [attenuation curves](https://www.audiokinetic.com/courses/wwise101/?source=wwise101&id=assigning_attenuation_curves_to_objects#read) for more information. Don't forget to test out your curves in Wwise.

The Alert sounds plays when the hoverbot is alerted to your presence. Find the place in the script where this happens and post an event.

Attack is the laser sound. Adding the laser sound should be as easy as adding a new event to the weapon controller script on the hover bot. See the `Weapon_EyeLazers` game object.

Finally add the hover bot death sound for when you destroy it. This will go into the death event on the Health script on the hover bot.

> Extra credit: Add a sound that happens when you're getting close to killing the enemy.

## Turret

The same with the turret!! Do the same processes to finish the death and detect sounds for the turret.

The attack sounds happen on a different game object. Use the profiler to find the game object that plays the laser sound on the turret.

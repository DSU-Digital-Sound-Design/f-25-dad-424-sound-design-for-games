---
title: "Player Sounds 2"
---

## Pickup sounds

These are the sounds that happen when you pickup an object. They give the user feedback that something has been picked up. We need to add these sounds to the health, weapons (launcher, shotgun) and jetpack pickup Prefabs. Use an AKEvent set to trigger on AkTriggerEnter for these. Remember the [coin sound from the example project](https://www.audiokinetic.com/courses/wwise301/?source=wwise301&id=Adding_a_Trigger_Condition#read).

## Jetpack sound

Afterwards implement the jet pack sound itself, make sure to add a stop event before the play event so that the jet pack sound doesn't play over itself if triggered twice. To keep the Jet pack from looping constantly in the same spot use a boolean statement to check if you've already triggered the jet pack sound. Ask me if you need help with this.

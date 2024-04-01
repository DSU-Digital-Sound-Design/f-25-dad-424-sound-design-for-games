---
title: "States, Switches, and Blend Containers"
---

> Adapted from [Game Audio with Unity and Wwise Part 5: Position Types, States, Game Parameters and Blend Containers - YouTube](https://www.youtube.com/watch?v=9HnVMWix0Sw&list=PLzlEBXWjqM97U5rHMERc82sTXRBoSB_Fu&index=6)
 


## Position Types: Multi-position mode

What if we wanted to have a sound play from multiple objects at the same time? We could add events to each of those objects, but this would cause unnecessary voices to play and could cause performance issues. Instead, we can use the multi-position mode in Wwise to play the sound from multiple objects at the same time. An example of this would be torches in a dungeon game. There are many of them, and we want them all to play the same sound at the same time. 

Choose one of our drone events and change its position type to multi-position. This will allow the sound to play from multiple objects at the same time. Because Wwise will only play one voice it's okay to have this sound play on start.  Find the other drone events and change their position types to multi-position as well. Now the drone event will play from all of the objects at the same time with only one voice. 

Check the Wwise profiler to see that only one voice is playing for the single drone event.

## Position Types: Large Mode

Now imagine spreading a sound over a large area such as a river, forest or fire pit. The sound should have a wide apparent source width. We can use the large mode in Wwise to achieve this effect.

Take a different drone and change its position type to large mode. This will give the sound a wide apparent source width. Pick an area in the scene where you want sound to emanate from a large area. Add the event there then add multiple `Large Mode Position Objects` spread over the given area. 

## Game Syncs: States

Another type of Game Sync is the State. States are used to switch multiple sounds for different game states. Use them instead of switches when they are necessary for complexity reasons. For example, a sound could have different versions for different times of day, different weather conditions, or different locations. You can find them under the game syncs tab in Wwise. 

Similarly to switches, you can create a state group and add states to it. Then, you can then assign the states to the sound in the sound property editor.

Add your final drone sound to play from the snow field. Create a state group in Wwise (in the Game Syncs tab) called onSnowField. Add two states to the group: onSnowField and offSnowField. In your drone random container, find the state tab. Add the onSnowField state group here. Set the on state with a higher voice pitch and off state with a lower voice pitch. 

Add two Ak State components to the snow field object in Unity. Set these up in the same way you set up the Ak Switch component. 

Now when the drone plays in the snow field, it will play with a higher pitch. When you are moving away from it, it will play with a lower pitch.

## Game Parameters

We can use game parameters to send continuous controls from Unity back to Wwise. This can be used to control the pitch of a sound, the volume, or any other parameter. One example of this would be controlling the pitch of a sound based on the speed of a car, or the speed of a heartbeat based on the health of a character. 

We'll use it to control the pitch of a drone sound based on the speed of the player. 

In Wwise, create a new game parameter called playerSpeed. Set the default to 0. Set the max to 4 to match our max player speed in Unity. In the sound property editor for your chosen drone, find the voice pitch property and click the RTPC button. Select the playerSpeed game parameter.

We now need to send the speed of the player from Unity to Wwise. In Unity, open up your player controller script. 

Add a new public reference to the game parameter: `public AK.Wwise.RTPC playerSpeed;`. In the start function add `playerSpeed.SetGlobalValue(0);` to set the default value of the game parameter.

Find this function in the Move function: 

```
if (currentHorizontalSpeed < targetSpeed - speedOffset || currentHorizontalSpeed > targetSpeed + speedOffset)
{
    // creates curved result rather than a linear one giving a more organic speed change
    // note T in Lerp is clamped, so we don't need to clamp our speed
    _speed = Mathf.Lerp(currentHorizontalSpeed, targetSpeed * inputMagnitude, Time.deltaTime * SpeedChangeRate);

    // round speed to 3 decimal places
    _speed = Mathf.Round(_speed * 1000f) / 1000f;
}
else
{
    _speed = targetSpeed;
}
```

Directly below this add `playerSpeed.SetGlobalValue(_speed);`. This will send the speed of the player to Wwise.


## Blend Containers

We can go back to our blend containers and use the player speed to blend between the different sounds. A slower speed will play one sound of the blend container and a faster speed will play the other sound.




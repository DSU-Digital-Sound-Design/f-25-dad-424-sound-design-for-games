---
title: "Posting events from Scripts in Wwise"
---

Let's look at the `HealthPickup` script as an example. If you open the script you'll see this code:

```c#
using Unity.FPS.Game;
using UnityEngine;

namespace Unity.FPS.Gameplay
{
    public class HealthPickup : Pickup
    {
        [Header("Parameters")] [Tooltip("Amount of health to heal on pickup")]
        public float HealAmount;

        protected override void OnPicked(PlayerCharacterController player)
        {
            Health playerHealth = player.GetComponent<Health>();
            if (playerHealth && playerHealth.CanPickup())
            {
                playerHealth.Heal(HealAmount);
                PlayPickupFeedback();
                Destroy(gameObject);
            }
        }
    }
}
```

Hopefully you notice that this script is not directly triggering any sounds. So, what's happening here? Notice the line `public class HealthPickup : Pickup`? This is telling the script to inherit from the `Pickup` script. If you right click on `Pickup` and say "Go to declaration", you'll be brought to the `Pickup` script. The game designers wrote the code this way so that they could reuse the same script for multiple pickups.

The important line to see here is:

```c#
if (PickupSfx)
{
    AudioUtility.CreateSFX(PickupSfx, transform.position, AudioUtility.AudioGroups.Pickup, 0f);
}
```

`CreateSFX` is a helper function that wraps functionality that Unity needs to play the sound. We'll look for these in our code and replace them with the Wwise equivalent. If you once again go to the definition of `CreateSFX` you'll see this:

```c#
public static void CreateSFX(AudioClip clip, Vector3 position, AudioGroups audioGroup, float spatialBlend,
    float rolloffDistanceMin = 1f)
{
    GameObject impactSfxInstance = new GameObject();
    impactSfxInstance.transform.position = position;
    AudioSource source = impactSfxInstance.AddComponent<AudioSource>();
    source.clip = clip;
    source.spatialBlend = spatialBlend;
    source.minDistance = rolloffDistanceMin;
    source.Play();

    source.outputAudioMixerGroup = GetAudioGroup(audioGroup);

    TimedSelfDestruct timedSelfDestruct = impactSfxInstance.AddComponent<TimedSelfDestruct>();
    timedSelfDestruct.LifeTime = clip.length;
}
```

This script handles assigning an AudioClip to an AudioSource and playing it. It also handles the spatialization of the sound.

To help with figuring out how to play sounds with scripts and Wwise refer to [Lesson 4: Posting Events from Script](https://www.audiokinetic.com/courses/wwise301/?source=wwise301&id=Lesson_4).

> Now take some time and try to figure out where the blaster sound is being played.

---
title: "Sound Design Tutorials"
---

## PaulXStretch

Download the plugin [here](https://xenakios.wordpress.com/paulxstretch-plugin/). This plugin can stretch audio to create long evolving drones or pad sounds. It's based on a much older program called [Paul's Extreme Sound Stretch](http://hypermammut.sourceforge.net/paulstretch/) by [Paul Nasca](http://www.paulnasca.com/)

Paul'd description:

> Paulstretch is a time-stretching of audio designed for extreme stretching. While the most time-stretching methods produces artifacts on extreme (like 10x) stretches, Paulstretch produces high quality sound even at 1000x stretches. The algorithm implemented in Paulstretch is invented by me and it is described in the Algorithms page.

First, add or record a sound to use in the plugin. Looping is set on by default. So when you add a sound you should immediately hear some stretching happing. If you're working with a longer sound, adjust the sound start and end points so that paul stretch is only stretching part of the sound.

I like to change the setting `Play when host transport running` to true so that I can stop and start the sound with the spacebar.

Find the `stretch amount` parameter and increase it slowly then listen to the result. Stretch values over 5 start to make the sound unrecognizable. Repeat these steps with different types of sounds to hear the result of stretching alone. Try sounds that are more harmonic, or simple, or more noisy. Try vocal sounds, or instrument sounds, or field recordings.

If you are using a harmonic or melodic sound turn on the ratios section. Then go to the ratios mixer. Here you can add octaves above or below the sound at certain volumes. It can have a very similar sound to a pipe organ. You can get really interesting chordal sounds by removing the fundamental, slider 3.

Next change the values of the `FFT Size`. A smaller FFT size will result in a more distorted sound. A larger FFT size will result in a more natural sound. This parameter might be a good one to automate.

`Pitch shift` shifts the pitch of the audio by semitones. This enables extra organ-like sounds if using a simple melodic sound.

The `Free Filter` section allows you to create your own filter shapes then shift, scale or tilt them to get the sound you want. Then try to add randomness to the filter shapes. A lower random rate will give you a faster change between random filter shapes.

Select the `Harmonics` box and see the three highlighted parameters that go along with the harmonics. This allows us to tune the harmonics that are already present in the signal. Set a base harmonic value for the `Harmonics base freq`. Then adjust the `Num harmonics` to get more or less harmonics. You may need to turn on the compressor if you have few harmonics to boost the signal. This is a good way of getting drones that don't sound much like the source material but still develop over time. Alter the `Harmonics Bandwidth` parameter to narrow or widen the harmonics bandwidth.

`Tonal vs Noise` filters out more or less of the noise spectrum of a signal. This is a good parameter to generate very pitched drones.

`Frequency spread` adds detuning to each band.

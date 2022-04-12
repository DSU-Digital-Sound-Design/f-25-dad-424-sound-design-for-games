---
title: "Sound Design Tutorials"
---

## PaulXStretch

Download the plugin [here](https://xenakios.wordpress.com/paulxstretch-plugin/). This plugin can stretch audio to create long evolving drones or pad sounds. PaulXStretch is based on a much older program called [Paul's Extreme Sound Stretch](http://hypermammut.sourceforge.net/paulstretch/) by [Paul Nasca](http://www.paulnasca.com/)

Paul's description:

> Paulstretch is a time-stretching of audio designed for extreme stretching. While the most time-stretching methods produces artifacts on extreme (like 10x) stretches, Paulstretch produces high quality sound even at 1000x stretches. The algorithm implemented in Paulstretch is invented by me and it is described in the Algorithms page.

First, add or record a sound to use in the plugin. Looping is on by default. So when you add a sound, you should immediately hear some stretching happing. If you're working with a longer sound, adjust the sound start and endpoints so that Paul Stretch only stretches part of the sound.

I like to change the setting `Play when host transport running` to true so that I can stop and start the sound with the space bar.

Find the `stretch amount` parameter, increase it slowly, and listen to the result. Stretch values over five start to make the sound unrecognizable. Repeat these steps with different sounds to hear the influence of stretching alone. Try sounds that are more harmonic, simple, or noisy. Try vocal sounds, instrument sounds, or field recordings.

Turn on the ratios section if you are using a harmonic or melodic sound. Then go to the ratios mixer. Here you can add octaves above or below the sound at specific volumes. It can have a very similar sound to a pipe organ. You can get unique chordal sounds by removing the fundamental at slider 3.

Next, change the `FFT Size.` A smaller FFT size will result in a more distorted sound. A larger FFT size will result in a more natural sound. This parameter might be a good one to automate.

`Pitch shift` shifts the pitch of the audio by semitones. This parameter enables organ-like sounds if using a simple melodic sound.

The `Free Filter` section allows you to create filter shapes and then shift, scale, or tilt them to get the sound you want. Then try to add randomness to the filter shapes. A lower random rate will give you a faster change between random filter shapes.

Select the `Harmonics` box and see the three highlighted parameters of the harmonics. This parameter allows us to tune the harmonics already present in the signal. Set a base harmonic value for the `Harmonics base freq.` Then adjust the `Num harmonics` to get more or fewer harmonics. You may need to turn on the compressor with fewer harmonics to boost the signal. This parameter is a good way of getting drones that don't sound much like the source material but still develop over time. Finally, alter the `Harmonics Bandwidth` parameter to narrow or widen the harmonics bandwidth.

The `Tonal vs Noise` section filters out more or less of the noise spectrum of a signal. This is an excellent parameter to generate very pitched drones.

`Frequency spread` adds detuning to each band.

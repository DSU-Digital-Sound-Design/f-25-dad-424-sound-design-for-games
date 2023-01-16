+++
title =  "Level 3: My Non-Linear Life: Audio for Interactive Environments"
outputs = ["Reveal"]
[reveal_hugo]
custom_theme = "reveal-hugo/themes/sunblind.css"
margin = 0.2
+++

# The Essential Guide to Game Audio

## Level 3: My Non-Linear Life

---

# Learning Outcomes

- Linear vs non\-linear—the nuts and bolts of why games are different from film/TV
- Understand how interactivity affects audio design
- Some of the major technical developments in game audio history

---

# Challenges of Interactive Media

- What challenges does a game audio person face?
  - Non-linear situations
  - Unpredictability
  - Need for independently mixed and mastered sounds
  - Organizing 1000s of sound files/assets for programmers
  - Identifying sound triggers

{{% note %}}
Video games are different from any of the other mediums that use sound in that it's non-linear. IN a form of film or tv, the action happens predictably the same way each time.

Each sound we hear in a game is "triggered" by an action on the screen. This changes the workflow from linear media. Sometimes one sound can be triggered, or sometimes hundreds, the mix needs to intelligently respond accordingly.

Games also need many many sounds to create the realistic world that you're used to. ONe reason is to avoid repetitions of sounds that could hurt the immersive quality of the soundscape.

A game audio designer must not only design the sounds, but figure out what part fo the game will trigger that sound.
{{%/ note %}}

---

## Early Console and Arcade Game Development Challenges

<iframe width="560" height="315" src="https://www.youtube.com/embed/jlLPbLdHAJ0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

- sounds programmed directly on microchips
- Pong, space invaders, pacman
- Then technology developed and designers started to use musical abilities

{{%/ note %}}

---

## Nobuo Uematsu

<iframe width="560" height="315" src="https://www.youtube.com/embed/CED4Kf6oHZc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Famous video game composer that spans different eras of game sound.
{{%/ note %}}

---

<iframe width="560" height="315" src="https://www.youtube.com/embed/B7Ix5XDPcNE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Joe Montana II Sports Talk Football for the Sega Genesis was an early game with sampled sound. It made heavy use of voice over, so needed special attention paid to sound quality and file size. AT a time when compression such as MP3 hadn't been invented yet, game companies had to develop their own compression algorithms.

Sports talk uses a small MIDI file that triggers a YM2612 chip. Using MIDI would allow composers to try to make their soundtracks sound the same way on different platforms by using MIDI channels for different instruments.
{{%/ note %}}

---

## Adaptive Audio

<iframe width="560" height="315" src="https://www.youtube.com/embed/p-FLWabby4Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

## Audio Middleware

- [FMOD](https://fmod.com/)
- [Audiokinetic Wwise](https://www.audiokinetic.com/en/)

{{% note %}}
Technologically speaking, things in games got so good for sound artists that around 2000, new pieces of software called middleware started cropping up. The first middleware engines for audio were around throughout the 1990s and even beforehand. These were custom made and proprietary tools; game companies kept the software in-house for their own use. In many cases, middleware was developed by audio folks and programmers working together to solve workflow issues and smooth out production cycles. As these tools became sought after, third-party developers started to produce them and make them available to the general public.
{{%/ note %}}

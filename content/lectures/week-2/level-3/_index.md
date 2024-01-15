+++
title =  "Level 3: My Non-Linear Life: Audio for Interactive Environments"
outputs = ["Reveal"]
[reveal_hugo]
custom_theme = "reveal-hugo/themes/sunblind.css"
margin = 0.2
+++

## Level 3: My Non-Linear Life

---

# Learning Outcomes

- Linear vs non\-linear—the nuts and bolts of why games are different from film/TV
- Understand how interactivity affects audio design
- Some of the major technical developments in game audio history

---

# Challenges of Interactive Media

- Non-linear Nature of Game Audio
- Unpredictability and Indeterminacy
- Action-based Sound Triggering
- Integration with Game Design and Programming

{{% note %}}

- Unlike linear media like films, game audio is non-linear, requiring adaptability to various scenarios and timelines.
- The inherent unpredictability in games makes sound design challenging, as actions occur at different times in each gameplay.
- Instead of spotting a sound at a specific time, sounds are triggered by in-game actions (e.g., a character opening a door triggers the corresponding sound file).
- Game audio design is closely linked with game programming and design, requiring sound files to be organized and integrated effectively for seamless gameplay experiences.

{{%/ note %}}

---

## Early Console and Arcade Game Development Challenges


<iframe width="560" height="315" src="https://www.youtube.com/embed/q_3d1x2VPxk?si=t0OR_RCucySzdmFS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

## Review 

- In the 1970s and 1980s, creating game audio required direct programming of chips, with no advanced tools available for non-programmers.
- Sound design was predominantly done by programmers, often with little knowledge of music or sound, due to the lack of specialized tools.
- Early consoles like the NES could only produce a few notes simultaneously, limiting the complexity of music and sound effects.
- Despite basic technology, creative designers managed to produce significant audio achievements, contributing to the evolution of game sound design.

## Summary of YouTube Transcript

#### Part 1: Beeper Speaker
- **Early Home Computers**: Basic "beeper speaker" for sound, found in IBM PC and Apple II.
- **Functionality**: Controlled by the CPU, producing tones through timed clicking noises.
- **Limitation**: Required significant CPU resources, hindering other functions.

#### Part 2: FM Synthesizer
- **1980s Evolution**: Dedicated sound chips in computers and consoles.
- **Personalities of Systems**: Unique sounds and styles for each system.
- **Voices/Channels**: Importance of the number of voices (or channels) for sound complexity.
- **Voice Flexibility**: Ability to create different waveforms.
- **Examples**: 
    - **Nintendo Entertainment System**: Five voices but limited to specific sound types.
    - **Commodore 64**: Three voices with four waveform types (square, triangle, sawtooth, noise).
- **Programming Techniques**: Advanced methods allowed for dynamic reassignment of voices.

#### Sound Chips in Computers
- **IBM PC Sound Upgrade**: Introduction of AdLib card with Yamaha YM 3812 sound chip, followed by the SoundBlaster card.
- **Features**: YM 3812 chip had nine voices and was used in Yamaha keyboards.
- **Example**: Music from the game Ultima 6, and its recreation on a Yamaha keyboard.

#### Sampling
- **Sampling Keyboard (1985)**: Four voices, showcasing the sampling capability.
- **Commodore Amiga**: First affordable home computer with a four voice stereo sampling system.
- **Modtracker Music**: Music files containing samples and music information, originally designed for the Amiga sound chip.
- **Modern Music Composition**: Shift from Mod Tracker format to large sample files like mp3s due to increased storage and memory.



{{%/ note %}}

---

## Classic video game sound explained


<iframe width="560" height="315" src="https://www.youtube.com/embed/jlLPbLdHAJ0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

## Nobuo Uematsu

<iframe width="560" height="315" src="https://www.youtube.com/embed/9BzkrgVivk4?si=HDJ6l8VsdDRN3cBA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

## MIDI paved the way for composers like Uematsu to create complex music with limited technology.

- MIDI revolutionized digital music by allowing various devices to communicate, control, and trigger audio events, though it's not an audio format itself.
- In gaming, MIDI functions like a player-piano roll, efficiently triggering sounds and music while conserving file space, especially when paired with FM synthesis.
- MIDI's contribution to digital music was acknowledged with a technical Grammy, celebrating its creators and its role in advancing digital music sophistication.
- Early game composers faced challenges with limited sound technology, leading to creative uses of simple waveforms and synthesizer features to craft memorable game audio.

{{%/ note %}}
  
---

##  How PS1 Audio Mechanics Work 

<iframe width="560" height="315" src="https://www.youtube.com/embed/dC3Qy8m2Y7I?si=p5ERc2-_uMohR4fD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
## Summary

### Summary of the YouTube Transcript

#### Introduction to Media Consumption and Sound in Media
- The video begins with a discussion about how media consumption is an integral part of our lives, and how sound has played a crucial role in enhancing the immersion and enjoyment of media.

#### Evolution of Sound Storage: From Phonographs to Compact Discs
- The history of sound storage is explored, highlighting the transition from early phonograph-like devices to the development of the compact disc (CD) by Philips and Sony in 1982. This innovation marked a significant change in media storage, rendering many older mediums obsolete.

#### The Compact Disc: A Game Changer in Media Storage
- The compact disc revolutionized media storage with its release in Japan, offering around 10 megabytes of storage in the 1980s, which was impressive for the time. The CD was initially used by music labels to distribute albums.

#### Advancements and Adaptations in CD Technology
- Over time, CDs evolved to store videos, became rewritable, and even saw size reductions. Video game companies began using CDs, with the TurboGrafx-16 CD-ROM add-on being an early example. By the mid-1990s and 2000s, CDs became a dominant medium for video games.

#### From CDs to DVDs and Beyond
- The evolution continued with DVDs, Blu-ray discs, and 4K Blu-ray discs, with storage capacities reaching up to 100 gigabytes on triple-layer discs.

#### Focus on PlayStation and CD-ROMs
- The video then shifts focus to the PlayStation, which used CD-ROMs, a format similar to CDs but with pre-written, read-only data. The PlayStation's audio capabilities and how it processed sound for games are explored in depth.

#### Understanding the PlayStation's Sound Processing
- The PlayStation used two chips for sound: the Sound Processing Unit (SPU) and its DRAM. These chips processed sound and stored audio data, respectively. The video examines how PlayStation games used tracks for soundtracks, similar to traditional audio CDs.

#### Technicalities of PlayStation Audio
- The intricacies of PlayStation audio are discussed, including the use of ADPCM (Adaptive Differential Pulse Code Modulation) for audio file compression. The PlayStation could understand two subformats of ADPCM: SPU-ADPCM and XA-ADPCM, each with its own characteristics.

#### The Role of VAG and VAB Formats
- PlayStation games often used VAG files for individual sounds and VAB files for sets of sounds. The video describes how these formats are used in conjunction with the PlayStation's hardware to produce game audio.

#### Advanced Sound Processing Capabilities of the PlayStation
- The PlayStation's SPU had advanced capabilities like producing 24 voices, stereo sound, and various sound effects. The video goes into detail about these features, including looping, pitch modulation, and digital reverb.

#### Conclusion: Exploring PlayStation Sound in Action
- The video concludes with a practical exploration of the PlayStation's sound capabilities, using the console's BIOS as an example. The BIOS sequence demonstrates the use of SPU voices, reverb, looping, and other audio features, providing a comprehensive understanding of PlayStation sound processing.

{{%/ note %}}

---


## The Emergence of Middleware in Game Audio

- Introduction of Middleware in 2000s
- Middleware as a Solution for Audio Designers
- Popular Middleware Applications

{{% note %}}

- Around 2000, middleware emerged as a game-changing solution for sound artists, addressing workflow and production issues in game audio.
- Middleware, developed by audio professionals and programmers, empowered designers and composers with more control over in-game audio.
- Examples of popular middleware include FMOD, Wwise, Miles, and xACT, offering graphical interfaces and interactive audio tools for professionals.

{{%/ note %}}

---

## Internet and Flash in Game Audio

- Impact of Internet on Game Audio
- Flash's Role in Early Internet Games
- Evolution of Audio Quality with Internet Speed

{{% note %}}

- The rise of the Internet and broadband speeds significantly influenced game audio, particularly for web-based games.
- Flash played a pivotal role in early internet games, efficiently compressing audio within limited bandwidth constraints.
- As internet speeds improved, from dial-up to DSL and cable modems, the quality of audio in downloadable games increased, accommodating richer audio content.

{{%/ note %}}

---

## Modern Challenges and Innovations in Game Audio

- Advancements in Mobile and Tablet Gaming
- New Platforms and Audio Challenges
- Evolution of Handheld Game Audio

{{% note %}}

- The advent of smartphones and tablets introduced new platforms for gaming, creating unique audio challenges and opportunities.
- Unity3D and other engines offer robust audio features, catering to the needs of contemporary game development.
- Handheld devices like the Nintendo DS, PSP, and Vita, despite their limited audio capacity, have inspired innovative audio design reminiscent of early gaming eras.

{{%/ note %}}

---

## Current Audio Middleware

- [FMOD](https://fmod.com/)
- [Audiokinetic Wwise](https://www.audiokinetic.com/en/)



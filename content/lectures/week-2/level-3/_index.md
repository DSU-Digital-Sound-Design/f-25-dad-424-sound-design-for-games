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

## Linear vs Non-Linear Audio

- **Linear**: fixed sequence, timeline-based (film, TV, radio)
- **Non-Linear**: triggered by user actions, adaptive, unpredictable
- **Hybrid**: cinematic sequences inside interactive play (e.g. *Bandersnatch*)

{{% note %}}
- Linear = sound locked to the same time markers every time.
- Non-linear = sound cues wait in a “pool,” ready to be triggered by player input.
- Hybrid = increasingly common in modern narrative games.
{{% /note %}}

---

## Why Audio Matters

- **Inform** – provides navigation, spatial awareness, environmental cues  
- **Entertain** – sets tone, increases enjoyment  
- **Immerse** – creates believability and emotional connection

{{% note %}}
Jean-Luc Sinclair defines game audio’s role as “Inform, Entertain, Immerse.”
Sound expands what the player sees, compensates for limited field of view, and guides story and emotion.
{{% /note %}}


---

## Unique Challenges in Game Audio

- **Unpredictable Timing** – sounds may need to trigger hundreds of times in different contexts  
- **Branching Content** – dialogue, music, and effects must adapt to multiple story paths  
- **Dynamic Layering** – music and ambience must shift smoothly with game state  
- **Integration with Code** – audio designers collaborate closely with programmers to set triggers and parameters  

{{% note %}}
- In games, you never know *when* a player will open a door, swing a sword, or enter combat — timing can’t be spotted like in film.
- Dialogue trees and branching narratives mean audio teams record and design for many possible paths, not just one fixed script.
- Adaptive systems (e.g., music layers that intensify in combat) must crossfade seamlessly without breaking immersion.
- Sound designers must often use middleware (FMOD, Wwise) or work directly with game code to ensure sounds are triggered by gameplay events.
- Example: footsteps that change automatically with surface type (grass, metal, water) require both design and code hooks.
{{% /note %}}

---

## Before Middleware: How Oldschool Game Audio Worked

- **Internal Speaker Era** (late 1970s)  
    - Single beeper speaker; CPU directly generated tones  
    - Non-linear triggering: CPU paused main work to output sound  

- **Dedicated Sound Chips & Voices** (early 1980s)  
    - Consoles/computers added limited multi-voice chips  
    - Logic decided which sound got which channel (voice stealing/prioritizing)  
    - Each platform had a signature palette (e.g., NES 5 fixed channels, C64 3 flexible SID voices)  

{{% note %}}
- Pre-middleware audio was already event-driven (not timeline spotted).
- Programmers hard-coded: if player jumps → play sound on an available channel.
- Channel/voice management acted as an adaptive system (steal, fade, substitute).
{{% /note %}}

---

## Before Middleware: Trackers, Samples, and Early Rules

- **PCM Samples & Trackers** (mid 1980s–1990s)  
    - Amiga: 4-channel stereo sample playback  
    - Module files = samples + pattern instructions (compact + reusable)  
    - Music & SFX still triggered by in-game events (no global timeline)  
    - Tracker pattern logic = early “rules” for sequencing & variation  

<iframe width="560" height="315" src="https://www.youtube.com/embed/q_3d1x2VPxk?si=t0OR_RCucySzdmFS" title="How Oldschool Sound/Music Worked - The 8-Bit Guy" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>  

[Watch on YouTube](https://www.youtube.com/watch?v=q_3d1x2VPxk)

{{% note %}}
- C64 SID tricks: rapid per-frame voice reassignment to exceed 3 apparent sounds.
- Amiga trackers let composers embed conditional/order logic—proto rule systems.
- These foundations (event triggers + resource management + rules) foreshadow modern middleware.
- Source: The 8-Bit Guy – How Oldschool Sound/Music Worked (YouTube).
{{% /note %}}

---

## MIDI and the Rise of Game Composers

- MIDI = efficient event-based control, not audio  
- Allowed rich, multi-channel compositions on limited hardware  
- Paved the way for composers like **Nobuo Uematsu** (Final Fantasy)  
- Set the stage for adaptive, event-driven music in games  

<iframe width="560" height="315" src="https://www.youtube.com/embed/9BzkrgVivk4?si=HDJ6l8VsdDRN3cBA" title="Nobuo Uematsu & MIDI in Game Music" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>  

[Watch on YouTube](https://www.youtube.com/watch?v=9BzkrgVivk4)

{{% note %}}
- MIDI = “player piano roll” → stores instructions, not sound.  
- Key benefit: efficiency. Tiny files triggered voices on sound chips, conserving memory.  
- Composers like Uematsu made “orchestral” textures by carefully allocating channels, layering simple waveforms, and maximizing limited voices.  
- MIDI workflows foreshadow modern middleware: audio responds to triggers/events, not just fixed tape playback.  
- Uematsu’s work shows how game audio matured artistically while remaining technically constrained.  
{{% /note %}}

---

## PlayStation 1: Toward Adaptive Music (1/2)

- **SPU ADPCM** format: looping, per‑voice reverb, variable sample rates  
- **24 hardware voices**: mix/layer music + SFX in real time  
- Layer manipulation enabled early adaptive scoring (add/remove parts)  
- **Sequenced (event-based) music** instead of long streamed audio  
- Stored note/instrument data → low memory + runtime control (tempo, pitch, instrumentation)  

{{% note %}}
SPU ADPCM (gameplay audio) differed from XA ADPCM (cutscene streams): it supported looping and real-time effects, allowing music to persist until an event triggered a change. The 24-voice SPU let designers treat stems (pads, percussion, melody) as layers they could fade or swap—an evolutionary step toward middleware-style vertical mixing.
{{% /note %}}

---

## PlayStation 1: Toward Adaptive Music (2/2)

- Exploited quirks (e.g., “dummy” data to halt or redirect loops) for transitions  
- Could fade voices, swap instruments, or inject percussion on combat start  
- Real-time parameter tweaks (volume, reverb send) = early adaptive rules  
- Demonstrated hardware-driven path toward later middleware workflows  

<iframe width="560" height="315" src="https://www.youtube.com/embed/dC3Qy8m2Y7I?si=p5ERc2-_uMohR4fD" title="PS1 Audio Mechanics" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>  

[Watch on YouTube](https://www.youtube.com/watch?v=dC3Qy8m2Y7I)

{{% note %}}
Sequenced data = instructions, so transitions cost almost no memory versus storing multiple full mixes. Developers used voice allocation + controlled looping behavior to simulate adaptive layering (e.g., fade in rhythmic layers when entering combat, add reverb indoors). These practices foreshadowed middleware concepts: event triggers, voice management, parameter-driven mixing.
{{% /note %}}

---

## Activity: Choose Your Own Audio Adventure

- You’ve seen how audio evolved from single channels to MIDI to adaptive layering.  
- Now imagine designing for this scene:
  - A player enters a forest clearing.  
  - Suddenly, an enemy appears.  
  - The player can:  
    1. **Fight** → fast combat with swords and spells  
    2. **Run Away** → sneaking and footsteps in brush  
    3. **Talk** → dialogue tree with branching choices  
- In your group (3-4 students):  
  - How should the music adapt in each case?  
  - What sound effects are essential?  
  - How would you keep transitions smooth if the player switches paths quickly?  

> Share your audio design plans with the group.

---

## Interactive Audio: Beyond Looping Tracks

- Must be **reactive** (responding to player input)  
- Must be **responsive** (adapting to game state/context)  
- Behaves like a **database of musical ideas**, ready for recombination  
- Supports **branching, layering, and parameter-driven changes**  
- **iMUSE (LucasArts, 1991)**: early system enabling seamless transitions and adaptive scoring  
  - [Wikipedia – iMUSE](https://en.wikipedia.org/wiki/IMUSE)

{{% note %}}
- Mark Miller (Game Developer, 2001) argued that game music should function as a “database of motifs,” recombined in response to gameplay events.  
- This framing helped spread awareness of interactivity as more than looping tracks.  

- The **iMUSE system** (developed by Michael Land and Peter McConnell at LucasArts) is one of the earliest working examples.  
  - It let music transition smoothly between cues, wait for events before changing, and layer adaptive elements dynamically.  
  - iMUSE was used in games like *Monkey Island 2* and *X-Wing*, where music responded to player actions with seamless crossfades and thematic shifts.  

- Together, Miller’s conceptual framing and iMUSE’s implementation illustrate the shift toward **non-linear, event-driven music design**.  
- Later examples include *Halo*’s vertical re-orchestration layers (combat vs exploration) and *Breath of the Wild*’s sparse adaptive score.  

- Resources:  
  - Miller’s article: [Producing Interactive Audio](https://www.gamedeveloper.com/audio/producing-interactive-audio-thoughts-tools-and-techniques)  
  - iMUSE overview: [Wikipedia – iMUSE](https://en.wikipedia.org/wiki/IMUSE)  
{{% /note %}}

---


## Rules for Interactive Sound Design

- Accept technological limits; use them creatively  
- Serve the game’s vision and emotional goals  
- Collaborate with programmers and designers early  
- Plan interactivity into the **design doc** and **asset pipeline**  

{{% note %}}
Miller’s “rules” are practical design guidelines:
- Limitations are a feature, not a flaw.
- Interactivity can only succeed if planned alongside game mechanics, not bolted on afterward.
- Middleware (FMOD, Wwise) makes these principles easier to realize with tools like **RTPCs** (real-time parameter controls).
See [Audiokinetic’s Wwise tutorials](https://www.audiokinetic.com/learn/) and [FMOD learning resources](https://www.fmod.com/resources) for examples.
{{% /note %}}

---

## The Rise of Middleware in Game Audio

- Emerged in the 2000s to solve workflow challenges  
- Gave composers and designers direct control over adaptive sound  
- Bridges **DAW assets → Middleware → Game Engine**  
- Popular tools: [FMOD](https://fmod.com/), [Wwise](https://www.audiokinetic.com/), Miles, xACT  

{{% note %}}
- Before middleware, programmers hard-coded sound triggers and adaptive logic into game code.  
- Middleware freed audio teams by providing **graphical interfaces** and rule-based systems for interactivity.  
- Enabled standardized techniques such as:  
  - **Vertical re-orchestration** (layering/fading instruments)  
  - **Horizontal resequencing** (switching between cues or sections)  
  - **RTPCs (real-time parameter controls)** to tie audio behavior directly to game variables (e.g., speed, health, tension).  
- Think of middleware as a **translation layer**: audio created in a DAW is imported into middleware, where interactivity rules are defined, then sent to the game engine.  
- Visual idea: show logos (FMOD, Wwise) and a simple pipeline diagram (DAW → Middleware → Engine).  
- Today, middleware is a standard in AAA development and widely used in indie games through Unity and Unreal integration.  
{{% /note %}}

---

## Internet and Flash: Non-Linear Constraints on the Web

- **Bandwidth limits shaped audio** – compressed, short loops were common  
- **Flash enabled event-driven sound** – triggers tied to gameplay actions in browser games  
- **Broadband expansion** – richer, layered audio became possible  

{{% note %}}
- In the dial-up era, bandwidth was the main constraint: audio had to be tiny, often just looping clips or single-event sounds.  
- Flash provided a framework for **event-driven SFX and adaptive loops** — audio responded to player clicks, collisions, and state changes, much like chip-era event triggers.  
- Designers worked around limitations by looping compressed sounds, reusing assets, and layering cleverly within size limits.  
- As internet speeds improved (DSL, cable), games could use **larger samples, more layers, and adaptive background tracks**.  
- Flash games showed that even in constrained contexts, **non-linear design logic** (trigger-based playback, adaptive layering) was central to interactive sound.  

**Examples to mention in class:**  
- *Line Rider* – user actions directly controlled the playback of sliding sounds and music.  
- *Fancy Pants Adventure* – responsive footsteps, jumps, and environmental sounds triggered in real time.  
- *Club Penguin* – music loops in different rooms changed based on player navigation, an early form of adaptive environmental audio.  
{{% /note %}}

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

## Future Directions

- **Procedural Audio**: e.g., *No Man’s Sky*, *Spore*  
- **AI-Driven Systems**: adaptive composition, responsive mixing  
- **Accessibility**: audio cues, haptics, visual indicators

{{% note %}}
Procedural and AI systems point toward a future where designers create frameworks rather than fixed assets.
Accessibility will continue to shape design ethics and practices.
{{% /note %}}

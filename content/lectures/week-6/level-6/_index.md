+++
title =  "Level 6 Compose Yourself!: The Art of Composing for Games"
outputs = ["Reveal"]
[reveal_hugo]
custom_theme = "reveal-hugo/themes/sunblind.css"
margin = 0.2
+++

## Level 6 Compose Yourself!: The Art of Composing for Games

---

# Learning Outcomes

- Identify differences between linear and non\-linear music composition
- Examine the use of loops\, branching\, and transitions
- Recognize the factors involved in non\-linear scoring
- Understand vertical and horizontal musical concepts

---

## Challenges in Music Creation for Media

* Music composition varies across mediums
* Unique challenges in theater, film, television, and games
* Specific issues faced by game composers
* Solutions and strategies for effective game music composition

{{% note %}}

* Composers approach music differently when writing freely versus composing for theater, film, television, or games, each with distinct aesthetic principles and production requirements.
* Game music faces unique hurdles: interactive gameplay demands music that adapts to unpredictable player actions and indefinite play sessions.
* Composers must craft engaging pieces that remain fresh and non-repetitive, even if players linger in one area for hours.
* Effective solutions include modular music systems that reassemble themes dynamically, adaptive layering that responds to player choices, and algorithmic variations to prevent looping fatigue.
* Example: *The Legend of Zelda: Breath of the Wild* uses subtle instrumentation changes as players explore new regions, while *Celeste* layers intensity to mirror player progress.

{{%/ note %}}

---

## Evolution of Video Game Music Composition

* Origins and challenges in early video game music
* Transition to digital music generation in the gaming industry
* Development and constraints of early game music technology
* Technological advancements and their impact on game music composition

{{% note %}}

* Early games like *Pong* (1972) and *Space Invaders* (1978) emerged when audio-recording technology was primitive, prompting developers to create music via tone generators and basic chips.
* Composers pioneered looping and minimalistic melodies to fit severe memory constraints, shaping techniques still used today.
* The 1980s saw chips like the NES’s Ricoh 2A03 enable multi-channel chiptunes, spawning classics like Koji Kondo’s *Super Mario Bros.* theme.
* By the 1990s, tools such as General MIDI expanded possibilities with polyphonic, orchestral textures, though PCM sampling limits kept most music synthesized and hardware-dependent.
* Example milestones include *Tetris* (1984) with its endlessly looping Korobeiniki motif and *Final Fantasy VI* (1994), which achieved sweeping orchestral arrangements within strict memory budgets.

{{%/ note %}}

---

## Modern Game Music Composition

* Role and skill set of contemporary game-music composers
* Technological advancements shaping game music
* Team structures and specialization in music production for games
* Versatility and challenges in current game music composition

{{% note %}}

* Today’s composers blend musical artistry with technical expertise, often working in middleware like Wwise or FMOD to build adaptive soundtracks.
* Modern technology—high-quality sample libraries, spatial audio, and procedural generation—allows for cinematic soundscapes and dynamic interactivity.
* Large-scale productions typically feature teams of composers, integrators, and audio programmers; indie titles may rely on one versatile creator juggling every role.
* Notable examples include *Red Dead Redemption 2* with its live-recorded Americana score that evolves with gameplay, and *Hades*, which layers rock-orchestral elements to intensify combat sequences.

{{%/ note %}}

---

## Impact of Music in Video Games

* Setting the mood and tone
* Defining time and place
* Distinguishing locations and settings
* Character identification through music
* Influencing gameplay pace
* Enhancing player immersion

{{% note %}}

* Music is pivotal in establishing the emotional ambiance of a game, from a memorable title theme to mood-specific background scores, fostering a deeper player connection to the game world.
* Soundtracks provide auditory cues for temporal and spatial context, transporting players to diverse settings such as medieval realms or futuristic galaxies, complementing visual elements like costumes and scenery.
* Just as visuals delineate different locations, music acts as an aural backdrop, distinguishing spaces—whether a tranquil forest (*The Legend of Zelda: Breath of the Wild* [source](https://screenrant.com/zelda-breath-wild-botw-music-soundtrack-link-story)) or a bustling cityscape (*Grand Theft Auto V* [source](https://en.wikipedia.org/wiki/Grand_Theft_Auto_V_soundtrack)).
* Character themes, akin to opera leitmotifs, inform players about character presence and narrative developments. Examples include Sephiroth’s “One-Winged Angel” in *Final Fantasy VII* ([source](https://en.wikipedia.org/wiki/One-Winged_Angel_%28song%29)) and the distinct motifs for each companion in *Hades* ([source](https://online.ucpress.edu/jsmg/article/6/1/8/205397/Interview-with-Darren-Korb)).
* Tempo and rhythm guide gameplay pace, heightening tension during combat (e.g., adaptive battle music in *Celeste* [source](https://en.wikipedia.org/wiki/Celeste_%28video_game%29#Music)) or providing calm during exploration sequences.
* Overall, music enriches immersion by reinforcing emotional resonance and enhancing the player's investment in the game world.

{{%/ note %}}

---

# Journey (2012)

<iframe width="560" height="315" src="https://www.youtube.com/embed/_4BgydcDQfg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

The music in the game "Journey" (2012) achieves several important functions:

1. **Setting the mood and overall tone of the game**: The soundtrack of "Journey" is designed to be both background and foreground music, amplifying the player's emotions at certain cues and providing a delicate, emotional backdrop throughout the game[1].

2. **Identifying time and place within the game**: The music helps in identifying the different stages of the journey and the emotions associated with them, such as loneliness, hope, despair, guilt, innocence, and joy[3].

3. **Identifying locations and settings in the game**: The music is carefully crafted to transport players into different environments, reflecting the game's setting and the cultures within it[5].

4. **Identifying characters within the game**: While the music may not directly identify specific characters, it enhances the emotional connection with the journeyer and reflects the emotional states experienced throughout the game[1][3].

The soundtrack of "Journey" is known for its ability to create an emotional connection with the players and enhance their overall gaming experience.

Citations:
[1] https://thehardmodes.com/journalism/2012/04/10/vgm5_journey
[2] https://www.youtube.com/watch?v=nOmx4ePpuRM
[3] https://www.amazon.com/Journey-Austin-Wintory/dp/B008DCOVP2
[4] https://www.reddit.com/r/patientgamers/comments/qtyrcl/i_played_journey_and_well_everything_people_said/?rdt=41973
[5] https://www.linkedin.com/pulse/soundtrack-gaming-how-music-sets-mood-brazy-gg

{{%/ note %}}

---

## Game Music Form and Structure

* **Cinematic**
  * Music underscores cutscenes, intros, and other story-driven sequences, heightening emotional impact and narrative flow.
* **Interactive Gameplay**
  * **Looping**: a continuous repetition of material that supports long gameplay segments without fatigue (e.g., exploration themes in *Minecraft*).
  * **Branching**: conditional transitions triggered by player actions or game states (e.g., battle-to-victory shifts in *The Legend of Zelda: Breath of the Wild*).
  * **Layered/Stem Mixing**: dynamic addition or removal of instrument layers to match intensity (e.g., combat music in *Hades*).

{{% note %}}

* Cinematic music enriches linear sequences—cutscenes, opening credits, or level-complete moments—guiding emotional arcs and signaling key narrative beats.
* Interactive gameplay music elevates player agency through adaptive techniques. Looping maintains ambience during exploration; branching triggers new cues for events like boss fights or stealth detection; stem mixing adjusts texture in real time for tension or release.
* These forms blur the line between composition and programming, requiring composers to think like both storytellers and system designers.

{{%/ note %}}

---

# Horizontal vs vertical re-orchestration

See examples [here](https://web.archive.org/web/20181113210932/https://www.designingmusicnow.com/2016/06/13/advantages-disadvantages-common-interactive-music-techniques-used-video-games/)

---

## Vertical Remixing – Layering

<iframe width="560" height="315" src="https://www.youtube.com/embed/JR38Yn9qxkQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

* **Definition and Purpose**
  Vertical remixing is an adaptive music technique where a soundtrack is split into separate stems—such as percussion, melody, ambient textures, or harmonic layers—that can be added or removed in real time. This allows the music to respond instantly and seamlessly to gameplay events without an abrupt cue change.
* **Benefits for Gameplay**
  Because only layers change, the player hears a continuous musical flow that deepens immersion and reinforces the emotional stakes of moment-to-moment gameplay. For example, a stealth sequence might begin with just sparse ambience, then add rhythmic layers as tension escalates.
* **Challenges and Limitations**
  Designers must carefully manage potential disruptions to musical phrasing and avoid transitions that feel like abrupt volume fades. Vertical remixing also offers limited control over tempo or key changes, which can reduce dramatic variation.
* **Practical Applications**
  This approach excels during frequent, brief state changes—like sudden combat encounters in open-world games or puzzle-solving sequences—where subtle dynamic shifts can signal progress or danger without overwhelming the player.
  Examples include the layered combat music of *Hades*, the dynamic battle stems in *Halo*, and exploration-to-combat transitions in *The Legend of Zelda: Breath of the Wild*.

{{%/ note %}}

---

## Horizontal Re-sequencing

* Concept of Horizontal Re-sequencing
* Techniques within Horizontal Re-sequencing
* Implementation in Video Games

{{% note %}}

* **Definition**
  Horizontal Re-sequencing is a dynamic, adaptive composition method where pre-composed music segments (or “cues”) are arranged like a flexible playlist. Segments can be triggered, skipped, or reordered based on player actions, creating a score that responds in real time.

* **Techniques**
  Methods include simple cross-fading between cues, modular “block” composition, and bridge or transition stingers that smoothly connect contrasting sections.

* **Game Applications**
  Designers often set multiple start and end points in each cue, enabling seamless jumps and narrative pacing.
  Examples:

  * *Journey* uses horizontal re-sequencing to follow the player’s physical and emotional journey with fluid transitions.
  * *The Legend of Zelda: Skyward Sword* triggers short transition phrases when players enter battle or solve puzzles, ensuring smooth progression.

{{%/ note %}}

---

## Cross-fading

<iframe width="560" height="315" src="https://www.youtube.com/embed/9-JKJMnH8wM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

* **Overview**
  Cross-fading is the most common horizontal re-sequencing technique: one cue fades out while another fades in, keeping the music continuous.

* **Advantages**
  It’s easy to implement and gives composers freedom to focus on creative writing rather than complex coding.

* **Challenges**
  Because the fade timing may not match tempo or key, it can interrupt musical phrasing or sound abrupt if not carefully balanced.

* **Examples**
  Widely used in titles like *World of Warcraft* and *Final Fantasy XIII*, where exploration themes dissolve smoothly into combat tracks. In *Firewatch*, cross-fading helps shift between tranquil exploration and tense narrative beats without breaking immersion.

{{%/ note %}}


---

## Phrase Branching

<iframe width="560" height="315" src="https://www.youtube.com/embed/C58TuhQPHNc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

* **Definition**
  Phrase branching is a horizontal re-sequencing technique where a new music cue starts only after the current musical phrase ends, ensuring smooth and musically coherent transitions.

* **Advantages**
  By waiting for the end of a phrase, the method preserves melodic and harmonic integrity and allows for natural changes in tempo, instrumentation, or mood.

* **Trade-offs**
  Responsiveness can be slightly delayed, especially if phrases are long, which may reduce immediacy compared to vertical remixing.

* **Examples**

  * *Chime* uses phrase-based triggers to rearrange looping motifs without breaking the flow.
  * *Killer Instinct (2013)* employs phrase branching during fights, letting transitions occur at the end of rhythmic phrases so the battle music escalates without abrupt cuts ([postmortem source](https://www.gamedeveloper.com/audio/postmortem-greater-accessibility-through-audio-in-i-killer-instinct-i-)).

{{%/ note %}}

---

## Musical Demarcation Branching

<iframe width="560" height="315" src="https://www.youtube.com/embed/oMVedBq6H24" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

[Killer Instinct Music](https://www.gamedeveloper.com/audio/postmortem-greater-accessibility-through-audio-in-i-killer-instinct-i-)

{{% note %}}

* **Definition**
  Musical demarcation branching triggers transitions at specific musical points—beats, measures, or downbeats—balancing musicality with quicker response.

* **Benefits**
  More adaptable than phrase branching, since it can act at shorter, predictable intervals (e.g., every measure), while still maintaining rhythmic alignment.

* **Limitations**
  There can still be a slight wait until the next demarcation point, and if not carefully composed, a phrase may feel truncated.

* **Examples**

  * *Killer Instinct* uses demarcation points tied to downbeats for smooth state changes during high-intensity combat.
  * *Halo* employs measure-based triggers so music layers shift naturally when enemies appear or battles conclude.

{{%/ note %}}


---
Here’s an updated version of the slide with stronger language, a bit more context, and some game examples—while keeping your exact formatting intact.

---

## Bridge Transition

<iframe width="560" height="315" src="https://www.youtube.com/embed/jZqaEZjxqLo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

* **Definition**
  Bridge transitions use a short, purpose-written musical passage to connect two otherwise unrelated musical segments, creating a smoother, more intentional shift than a simple cross-fade.

* **Benefits**
  The bridge can modulate tempo, harmony, or texture, letting the next cue enter naturally even if it differs drastically in style or key. This is especially valuable when moving between exploration and high-intensity action.

* **Challenges**
  If overused or poorly varied, bridges can feel repetitive and may slightly delay the next cue while the bridge plays. Long or predictable bridges can break immersion if players recognize them as a “loading sound.”

* **Examples**

  * *The Legend of Zelda: Skyward Sword* employs short fanfares as bridges into boss-battle themes.
  * *Halo 3* uses orchestral stingers to link ambient exploration music with sudden combat cues.
  * *Killer Instinct (2013)* combines bridge transitions with phrase and demarcation branching to move between fight states smoothly.

* **Best Use**
  Ideal for punctuating key game events—boss entrances, narrative revelations, or scene changes—while preserving musical flow. For frequent subtle changes, vertical remixing often offers a more continuous alternative.

{{%/ note %}}

---

# Stinger-Based Sequencing

<iframe width="560" height="315" src="https://www.youtube.com/embed/-oKdIbexbPw?si=UPccg-ynhOYvvaXu" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

{{% note %}}

* Stinger-Based Sequencing uses short, distinct musical "stingers" triggered by specific game events (e.g. a kill, a level up, entering a boss fight), often separated by silence or minimal ambient binding cues for impact. It’s effective for sharp auditory punctuation.
* This method allows rapid and clear feedback: a player does something important → cue plays instantly. Because stingers are designed to be discrete, they can connect very different musical cues (differing tempo, instrumentation) without needing a shared rhythmic backing.
* Downsides: frequent stingers can fragment the musical texture, especially if the ambient or background score is minimal or absent during transitions. Without careful design, it can feel like too many “sound effects” rather than musical flow. Sometimes overuse leads to a sense of disjointedness or making musical moments feel less ‘earned’.
* Best used in heavily scripted sequences or games with discrete, important event markers: e.g. boss introductions, environmental reveals, dialogue-milestones, UI feedback, or combat triggers. Less suited for continuous, ambient exploration where musical consistency matters more.

{{%/ note %}}

---

## Fallout 4

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZY5js5jW9LI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

# Fallout 4 Discussion Guide

## 1. Opening Impressions
- Ask: “What feelings or images come to mind when you hear Fallout 4’s music?”
- Follow-up: “If you’ve played it, how did the soundtrack shape your exploration of the wasteland?”

## 2. Musical Identity & World-Building
- Explore the contrast between:
  - Inon Zur’s dark orchestral score.
  - 1950s Americana songs on Diamond City Radio.
- Prompt: “How does this blend of styles support the retro-futuristic setting?”

## 3. Adaptive Score Techniques
- Discuss vertical remixing:
  - Layers of tension added during danger.
  - Gradual fade back to ambience after combat.
- Ask: “Where have you noticed these transitions while exploring or fighting?”

## 4. Diegetic vs. Non-Diegetic Layers
- Player-controlled radio as **diegetic** music vs. orchestral **non-diegetic** score.
- Question: “How does switching the radio on/off change your immersion or mood?”

## 5. Design Takeaways
- “What lessons can composers borrow for other post-apocalyptic or open-world games?”
- “Would you lean on player-controlled music or fully adaptive scoring?”

## Optional Listening Activity
- Play a short clip:
  - Radio song segment.
  - Ambient orchestral theme.
  - Combat transition.
- Have students identify techniques (vertical remixing, horizontal re-sequencing).

## Wrap-Up
- Summarize key insights:
  - Contrast of nostalgic radio and bleak orchestration.
  - Smooth adaptive layering for tension.
  - Player agency in shaping the soundscape.


{{%/ note %}}

---

### The Music Team

- Music director
  - Oversees the creative direction of the music for a game
  - Meets with composers\, game designers\, programmers\, and all other members of the production team to draft a creative vision
- Music producer
  - Controls the creative vision of the musical recording itself
  - Works with all the members to hire the musicians and engineers

![](img/chapter-67.png)

---

### The Music Team

- Composer
  - Writes music\, working in collaboration with the music director and producer to match the creative vision of the game
  - To create the score\, the composer may use a computer\-sequencing program such as Pro tools or Logic\, or even\, in some cases\, pen and paper

---

### The Music Team

- Orchestrator
  - Takes the music from the composer and either makes MIDI orchestrations or prepares parts and scores so that live humans can play the music if need be
  - Works with notation programs such as Finale and Sibelius to get the music ready for recording
- Recording engineer
  - Deals with the nuts and bolts of recording the music for a game
  - Records anything from live instruments to singers and needs a good working knowledge of recording studio technology and digital editing software

---

### The Music Team

- Mix engineer
  - Takes the completed recordings from the studio and balances the instruments and parts to make sure the recorded elements sound great together in the game
- Mastering engineer
  - Produces and delivers the final tracks in the desired format for the game
  - Has great ears and keen understanding of the platform the music will be integrated into

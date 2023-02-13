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

# Game Composers

- Questions:
  - If you don’t know how long the player will stay in a game level\, how long should you make the piece of music for that level?
  - If the action and intensity speed up as the player goes further into the level\, should the music speed up and slow down as well?

{{% note %}}

- Game composers face a host of issues that don’t exist in linear mediums

{{%/ note %}}

---

# New Breed of Composer

- Video games in the 1970s included titles such as _Pong_ and _Space _ Invaders
- At that time\, audio\-recording technology had not yet entered the digital age
- Later\, games used specialized computer chips called tone generators programmed to generate real\-time synthesizer music
- Thus was born a new breed of computer musician: one who used cutting\-edge\, low\-budget technologies

---

# Speaking of Music

- Examples of what a good musical soundtrack can accomplish:
  - Set the mood and overall tone of a game
  - Identify time and place within the game
  - Identify locations and settings in a game
  - Identify characters within a game

> What are some of your favorite examples of each of these?

---

# Journey (2012)

<iframe width="560" height="315" src="https://www.youtube.com/embed/_4BgydcDQfg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

- Examples of what a good musical soundtrack can accomplish:
  - Set the mood and overall tone of a game
  - Identify time and place within the game
  - Identify locations and settings in a game
  - Identify characters within a game

{{%/ note %}}

---

## Game Music Form and Structure

![](img/chapter-60.png)

- Cinematic
  - Music accompanies various cinematics within a game
- Interactive gameplay\. This may include:
  - Looping is going around and around\, repeating the same material
  - Branching is conditional music based on actions in the game

---

# Horizontal vs vertical re-orchestration

See examples [here](https://web.archive.org/web/20181113210932/https://www.designingmusicnow.com/2016/06/13/advantages-disadvantages-common-interactive-music-techniques-used-video-games/)

---

## Vertical remixing - layering

<iframe width="560" height="315" src="https://www.youtube.com/embed/JR38Yn9qxkQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}

Vertical Remixing is the adaptive technique where composers break up a music cue into two or more musical layers. Layers can be broken down by instrument family, or by musical function (Making Full Use of Orchestral Colors in Interactive Music by Jim Fowler.)

**Vertical Remixing Advantages**

Immediate changes to the music based on a game event.
Less impactful to the listener than switching to an entirely new music cue, e.g. the change is more subtle.

**Vertical Remixing Disadvantages**

Musical phrases can be easily interrupted (a melody is faded in or out in the middle of a phrase)
When fading in or out layers it can sound non-musical, e.g. the New York Philharmonic doesn’t fade-in a group of parts except through a well-written crescendo by the composer.
Inability to change the tempo or harmonic map, e.g. the score can’t suddenly change from a major key to a minor key based on game event.
Sometimes the layer that the game is fading in doesn’t have a lot of musical content leaving the game developer to wonder – did anything actually happen?

**Scenarios**

Vertical remixing is often used when a state changes from one state to another are shorter than 30 seconds. For instance if you’re playing an open world game where there are short combat scenarios, it’s better to bring in a layer of music for :15 seconds as opposed to switching to an entirely different music cue which might get repetitive if the player is rotating through explore-combat often.

Vertical remixing is often used when solving puzzles within games. Completion of each phase of the puzzle might bring in a new layer of the music indicating to the player that he’s progressing in the puzzle (Portal 2, and Legend of Zelda: Ocarina of Time).

{{%/ note %}}

---

# Horizontal Re-sequencing

{{% note %}}
Horizontal re-sequencing is a method of adaptive composition where the music is dynamically pieced together based on the actions of the player. This technique queues up the individual music cues dynamically one after another based on player decisions and outcomes similar to the creation of a playlist within iTunes.

There are actually many different methods of horizontal re-sequencing from simply cross-fading between music cue and another, to playing a bridge transition between two cues. When using horizontal re-sequencing techniques It should be noted that frequently composers have multiple start points for individual music cues increasing the variety of musical transitions. Below you’ll find the ones most commonly used in video games.
{{%/ note %}}

---

## Cross-fading

<iframe width="560" height="315" src="https://www.youtube.com/embed/9-JKJMnH8wM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Cross-fading is the simplest horizontal re-sequencing technique. Cross-fading is where one music cue fades out while another music cue fades up. This technique is used commonly across all games but include World of Warcraft, and Final Fantasy XIII.

**Cross-fading Advantages**

Super easy to compose and implement into a game.
Allows the composer to put more time into writing music, than worry about how it connect in the game.
Immediate changes to the music based on a game event.
Ability to completely change the tempo, harmony, instrumentation, or melody instantly based on a game even..

**Cross-fading Disadvantages**

The least musical of all adaptive techniques
Musical phrases are often interrupted in the middle of a phrase.
No accounting for the tempo or key changes when switching from one musical cue to another.

**Scenarios**

Cross-fading is used in all types of games because it’s dead simple to write and implement which saves everyone time. Sadly though it is the worst in terms of musicality because the music changes can be so abrupt, and noticeable to the player. Cross-fading is generally a bad method to use if the cues switch more often than 30 seconds because of the constant interruption to the player. Vertical remixing might be a better choice in that scenario.

{{%/ note %}}

---

## Phrase branching

<iframe width="560" height="315" src="https://www.youtube.com/embed/C58TuhQPHNc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Phrase branching is another horizontal re-sequencing technique which waits for the current musical phrase to end before playing the next musical cue. This technique is used in games such as Chime and Killer Instinct.

Phrase Branching Advantages

Most musical of all the horizontal re-sequencing techniques because it will never interrupt a musical phrase.
Ability to change tempo, harmony, instrumentation or melody in the next phrase based on a game event.

Phrase Branching Disadvantages

Non-immediate musical change because the music change will wait until the end of the current phrase which is dependent on the length of the phrases.
Can be more disruptive to the player in terms of musical changes than vertical remixing.

Scenarios

Phrase branching is better suited for styles/genres which have shorter phrase lengths such as rock and techno. Longer phrase lengths will delay the entrance of the next music cue. This technique is extremely musical in terms of never interrupted the current musical phrase, always allowing it to be completed before continuing. Silence can be embedded in the phrases similar to the stinger-based progression technique below but with specific lengths of silence before continuing.

{{%/ note %}}

---

## Musical Demarcation Branching

<iframe width="560" height="315" src="https://www.youtube.com/embed/oMVedBq6H24" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Musical demarcation branching is a technique which allows the music cue to switch at a musical demarcation point such as a beat, or measure.

Musical Demarcation Advantages

More musical than cross-fading.
Faster changes than phrase branching.
Ability to change tempo, harmony, instrumentation or melody in the musical demarcation point based on a game event.

Musical Demarcation Disadvantages

Non-immediate musical change because the music change will wait until the next demarcation point.
Musical phrases can be interrupted.
Can be more disruptive to the player in terms of musical changes than vertical remixing.

Scenarios

This technique is a hybrid between the non-musicality of switching via cross-fading, and the wait imposed by phrase branching. The changes are more immediate, and the change will happen on a more musically appropriate place than a random point. Music games obviously can take the most advantage of this technique, but this technique is used in all types of games because of the advantages.
{{%/ note %}}

---

## Bridge Transition

<iframe width="560" height="315" src="https://www.youtube.com/embed/jZqaEZjxqLo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
Bridge transitions is another horizontal re-sequencing technique in which short musical cues are used to connect one musical cue with another for more seamless transitions.
{{%/ note %}}

---

# Stinger-Based Sequencing

<iframe width="560" height="315" src="https://www.youtube.com/embed/CH7-CPCZu0c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{{% note %}}
This method of horizontal re-sequencing is a series of stingers which are played back based on game events. The player triggers these stingers individually based on an event that happens in the game. These stingers do not connect with one another, but may overlap. They generally do not have a connecting rhythmic framework, but are composed primarily of crescendos and accents with silence in-between. This technique is used in games such as Uncharted 4, and Tomb Raider.
{{%/ note %}}

---

# Music Gets Dynamic

- Many developers\, producers\, and composers want game music to do more than just loop in the background
- They want it to interact with the player’s progress through the game
- Interactive and adaptive music follows the same logic as interactive and adaptive audio
- Some game scores are adaptive; some are not

---

# Elements of Game Music

- Tempo
  - The change in speed of music can achieve many different psychological effects
- Key
  - The scale or mode that a piece of music is in
- Instrumentation/orchestration
  - The emotion of a piece of music can be altered by changing the instruments that are playing
- Volume/dynamics
  - By varying these elements, a deft composer can foreshadow events

> Favorite examples of this?

---

## Fallout 4

<iframe width="560" height="315" src="https://www.youtube.com/embed/ZY5js5jW9LI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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

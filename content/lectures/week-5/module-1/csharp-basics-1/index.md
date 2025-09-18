---
title: The Basics of C# (Part 1)
---

# Getting Started with C# in Unity (for FMOD Users)

If you’re diving into game audio with FMOD, chances are you’ll need to learn some C#. Unity uses C# as its primary scripting language, and even a basic understanding will help you set up interactivity, manage variables, and connect audio systems to gameplay events. This post walks through the essentials: namespaces, classes, variables, and functions—all in the context of Unity.

## Creating Your First Script

To get started, right-click in Unity’s Project tab and create a new C# script. Name it something descriptive—like `Player`—to keep your project organized. Once it’s generated, double-click the script to open it in an editor (Visual Studio on PC, or Monodevelop on Mac).

Every new script Unity generates comes with a standard template. Understanding this template is key to building your own functionality.

## Namespaces: Unity’s Toolboxes

At the top of your script you’ll see a few lines beginning with `using`. These are **namespaces**, collections of pre-written code that extend your script’s capabilities.

For example:

```csharp
using UnityEngine;
```

This line allows your script to interact with Unity components, such as a GameObject’s Transform. Without it, you wouldn’t be able to move, rotate, or scale objects through code. Think of namespaces as toolboxes—you bring in the ones you need for the job at hand.

## Classes: Containers for Behavior

Below the namespaces you’ll see the word `class`. Every script in Unity is built around a class, usually named the same as the file. Classes act as **containers** for your game logic: variables, functions, and other behaviors.

For instance:

```csharp
public class Player : MonoBehaviour
{
    // Your code goes here
}
```

The curly braces `{ }` mark the boundaries of the class. Everything inside becomes part of your script’s behavior. The `: MonoBehaviour` part links the class to Unity’s engine, giving access to powerful built-in functions.

## Variables: Storing Information

Variables are where your script stores data. Unity recognizes several **data types**, each for a different kind of information:

* `int` – integers (whole numbers): `int health = 5;`
* `float` – decimals: `float speed = 0.5f;`
* `bool` – true/false values: `bool playerIsGrounded = true;`
* `string` – text: `string color = "red";`

If you don’t assign a value, Unity uses a default: `0` for numbers, `false` for booleans, and empty for strings.

Variables are critical in game audio workflows—you might track health to trigger tension music, or speed to adjust footsteps dynamically in FMOD.

## Functions: Running Code at the Right Time

Unity provides some **functions** (also called methods) by default. Two of the most common are:

* `Start()` – runs once, on the first frame the script is active.
* `Update()` – runs once every frame, making it useful for actions tied to real-time gameplay.

For example:

```csharp
void Start()
{
    health = 10;
    Debug.Log(health);
}
```

This increases the player’s health to 10 when the game begins, and prints the value in Unity’s Console.

In contrast:

```csharp
void Update()
{
    speed = speed * 2;
    Debug.Log("Player speed: " + speed);
}
```

This multiplies speed by 2 every frame—quickly spiraling upward, but great for demonstrating variable changes over time.

## Debugging with Console Output

`Debug.Log()` is your best friend as you’re learning. It prints information from your script to Unity’s Console, letting you check whether your code is working as expected. You can log raw variable values or combine them with text labels for clarity.

## Connecting Back to FMOD

So why does this matter for audio? Because FMOD events often rely on Unity variables and functions to trigger them. For example:

* An `Update()` function can check a player’s position and update a music parameter.
* A boolean variable can tell FMOD whether the player is grounded, switching between different footstep sounds.
* An integer health variable can drive the intensity of combat music.

By mastering these basics, you’ll be ready to bridge Unity gameplay and FMOD’s audio system.


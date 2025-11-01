---
title: FMOD Namespaces
date: 2024-06-12
description: "A guide to understanding and using FMOD namespaces in Unity for game audio implementation."
categories: ["Game Audio", "Programming", "Audio Design"]
tags: ["Game Audio", "Unity", "FMOD", "Namespaces", "Audio Implementation"]
---


**Key Concepts**
- *Namespaces* are essential for organizing classes in C#. They let us keep related functionality together and reduce ambiguity in larger projects.
- *Classes* can be placed inside namespaces. When you want to use a class from a namespace, you declare which namespace you're using.
- Unity and FMOD integration relies heavily on namespaces to manage scripts efficiently in your game audio workflow.

**Recap: Namespaces & Classes in Unity**
When you create a new Unity script, you’ll see `using` statements at the top—these are the namespaces. They let you access classes and functions from Unity’s API. Below that, each script has a main public class that generally inherits from `MonoBehaviour`, giving you access to functions like `Start()` and `Update()`. These come from the `MonoBehaviour` class, which is part of the UnityEngine namespace.

You can view the definition of classes like `MonoBehaviour` in Visual Studio using “Go To Definition,” which helps to reveal their structure and included namespaces.

**Working with Namespaces**
If you remove a namespace declaration (say, `using UnityEngine;`), you’ll lose access to essential classes like `MonoBehaviour`—and Unity will show an error. You can also declare your own namespaces to organize custom scripts:

```csharp
namespace MyNamespace {
    public class MyClass { }
}
```
To use `MyClass`, you’d need to include `using MyNamespace;` in another script.

**FMOD Namespaces in Unity**
FMOD commands for game audio, like `PlayOneShot`, rely on namespaces just like Unity does. For example:

```csharp
using FMODUnity;

public string EventPath;
FMODUnity.RuntimeManager.PlayOneShot(EventPath, transform.position);
```

Here:
- `FMODUnity` is a namespace created by the FMOD team.
- `RuntimeManager` is a class within FMODUnity.
- `PlayOneShot` is a function in RuntimeManager.

To see how these work, you can open the FMOD integration scripts included in your project (like `RuntimeManager.cs`), and inspect how namespaces and classes are organized. Declaring `using FMODUnity;` at the top of your script lets you write shorter commands like `RuntimeManager.PlayOneShot(...)` instead of fully qualifying the namespace each time.

**Event Instances and Nested Namespaces**
FMOD events often use nested namespaces, such as `FMOD.Studio.EventInstance`. Here:
- `FMOD` is a namespace.
- `Studio` is a namespace inside FMOD.
- `EventInstance` is a struct inside Studio.

If you're using components from `FMOD.Studio`, you must declare both namespaces:

```csharp
using FMOD;
using FMOD.Studio;
```

**Streamlining Your Scripts**
Unity sometimes adds unused namespaces to your scripts by default. Visual Studio will gray out those not needed; clean them up to keep your code clear.

**Wrap-Up**
By understanding and leveraging namespaces:
- You can organize code more efficiently.
- Shorten commands by declaring the required namespaces at the top.
- Easily navigate Unity and FMOD codebases for game audio development.



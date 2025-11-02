---
title: FMOD Namespaces
date: 2024-06-12
description: "A guide to understanding and using FMOD namespaces in Unity for game audio implementation."
categories: ["Game Audio", "Programming", "Audio Design"]
tags: ["Game Audio", "Unity", "FMOD", "Namespaces", "Audio Implementation"]
---


## **Key Concepts**
- Namespaces group related types in C# and avoid name collisions.
- Using directives (`using ...;`) make types in a namespace available without full qualification.
- Unity and FMOD both expose APIs through namespaces that you reference from your scripts.

**Recap: Namespaces & Classes in Unity**
When you create a new Unity script, you’ll see using directives at the top—these specify namespaces. They let you access types from Unity’s API without fully qualifying them. Below that, each script defines a public class that usually inherits from `MonoBehaviour`, which provides lifecycle methods like `Start()` and `Update()`. `MonoBehaviour` lives in the `UnityEngine` namespace.

You can view the definition of classes like `MonoBehaviour` in Visual Studio using “Go To Definition,” which helps to reveal their structure and included namespaces.

Block-scoped and file-scoped namespaces:
```csharp
// Block-scoped (common in Unity projects)
namespace UnityEngine
{
    public class MonoBehaviour : Behaviour
    {
        // class contents
    }
}
```

File-scoped (C# 10+):
```csharp
namespace UnityEngine;

public class MonoBehaviour : Behaviour
{
    // class contents
}
```

## **Working with Namespaces**
Create a new script in Unity called `MyScript.cs` to explore namespaces.

If you remove a using directive (for example, `using UnityEngine;`), references like `MonoBehaviour` will no longer resolve and you’ll get compiler errors. You can also declare your own namespaces to organize custom scripts.

For example, using a traditional namespace declaration:
```csharp
namespace MyNamespace {
    public class MyClass { }
}
```
To use `MyClass`, either add `using MyNamespace;` to the top of another script or fully qualify it as `MyNamespace.MyClass`.

`MonoBehaviour` derives from the `Behaviour` class (also in `UnityEngine`). Use “Go To Definition” in your IDE to trace the inheritance chain and see which namespaces types come from.

## **FMOD Namespaces in Unity**
FMOD commands for game audio, like `PlayOneShot`, rely on namespaces just like Unity does. Example component:

```csharp
using FMODUnity;
using UnityEngine;

public class PlayEvent : MonoBehaviour
{
    [SerializeField] private string eventPath; // or use EventReference

    void Start()
    {
        // Positional one-shot
        RuntimeManager.PlayOneShot(eventPath, transform.position);
        // Or, to attach to a GameObject:
        // RuntimeManager.PlayOneShotAttached(eventPath, gameObject);
    }
}
```

Here:
- `FMODUnity` is the FMOD Unity integration namespace.
- `RuntimeManager` is a class within `FMODUnity`.
- `PlayOneShot`/`PlayOneShotAttached` are methods on `RuntimeManager`.


To see how these work, open the FMOD integration scripts in your project (for example, `RuntimeManager.cs`) and inspect how namespaces and classes are organized. Declaring `using FMODUnity;` lets you call `RuntimeManager.PlayOneShot(...)` without repeatedly writing the full namespace.

Go and find your Unity project’s `FMODUnity` folder (usually under `Assets/Plugins/FMOD/src`) to explore the FMOD classes and their namespaces.

### Understanding PlayOneShot
Common overloads you’ll use in Unity:

```csharp
// Positional one‑shot at a world position
RuntimeManager.PlayOneShot(string eventPath, Vector3 position);
RuntimeManager.PlayOneShot(EventReference eventRef, Vector3 position);

// One‑shot attached to and following a GameObject
RuntimeManager.PlayOneShotAttached(string eventPath, GameObject go);
RuntimeManager.PlayOneShotAttached(EventReference eventRef, GameObject go);
```

Notes:
- Fire‑and‑forget: these methods return `void`. You can’t stop or change parameters afterwards. For control, use `FMOD.Studio.EventInstance` or a `StudioEventEmitter`.
- Position vs attached: `PlayOneShot` uses a fixed `Vector3` at spawn time; `PlayOneShotAttached` follows the GameObject’s transform.
- EventReference vs string: `EventReference` is type‑safe and assignable in the Inspector; a string path is quick but error‑prone.

Example using an `EventReference` field:
```csharp
using FMODUnity;
using UnityEngine;

public class PlayEventRef : MonoBehaviour
{
    [SerializeField] private EventReference eventRef;

    void Start()
    {
        RuntimeManager.PlayOneShot(eventRef, transform.position);
        // Or follow this GameObject:
        // RuntimeManager.PlayOneShotAttached(eventRef, gameObject);
    }
}
```

## Example: When You Need Control

```csharp
// For parameter control, don't use PlayOneShot:
var instance = RuntimeManager.CreateInstance("event:/Music/Stinger");
instance.setParameterByName("Intensity", 0.8f);
instance.start();
// ... later, you can modify or stop it ...
instance.release();
```

## Key Takeaway

**The GUID overload is the "real" function** - the EventReference and string versions are just convenient wrappers that convert their input to GUID and pass it along. This is a common design pattern called the **Telescoping Pattern** or **Overload Chaining**.

**Bottom line:** PlayOneShot functions are perfect for simple one-off sounds that don't need runtime control.



### **Event Instances and Nested Namespaces**
FMOD exposes nested namespaces, such as `FMOD.Studio.EventInstance`:
- `FMOD` is a namespace.
- `Studio` is a nested namespace inside `FMOD`.
- `EventInstance` is a struct inside `Studio`.

Open up the definition of `EventInstance` in Visual Studio to see its members and methods. `EventInstance` is a value type (struct) representing a playable instance of an FMOD event. 

> Struct: A value type that holds data directly, unlike classes which are reference types.

```csharp
public struct EventInstance
{
    // Methods and properties for controlling the event instance
    public RESULT start();
    public RESULT stop(STOP_MODE mode);
    public RESULT setParameterByName(string name, float value);
    // ... more members ...
}
```

See if you can find methods like `start()`, `stop()`, and `setParameterByName()` in the definition.

If you use types from `FMOD.Studio`, add the appropriate using directives:

```csharp
using FMOD;
using FMOD.Studio;
```

Alternatively, fully qualify names (for example, `FMOD.Studio.EventInstance`).


**Streamlining Your Scripts**
Unity sometimes adds unused namespaces to your scripts by default. Visual Studio will gray out those not needed; clean them up to keep your code clear.

**Wrap-Up**
By understanding and leveraging namespaces you can:
- Organize code clearly and avoid name collisions.
- Use shorter, clearer code with `using` directives or fully qualified names when appropriate.
- Navigate Unity and FMOD APIs more confidently during audio implementation.

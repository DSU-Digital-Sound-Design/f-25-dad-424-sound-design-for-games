---
title: "The Basics of C# in Unity: From Variables to the Game Loop"
---

## Introduction 

This lesson introduces the fundamentals of C# programming within the Unity game engine. We will cover key concepts such as variables, data types, functions, and Unity's lifecycle methods (`Start` and `Update`). By the end, you will know how to create a simple script that manipulates variables and outputs information to the Unity Console.

---

## Create a New Script

In Unity, right-click in the Project window and select **Create > Scripting > MonoBehaviour Script**. Name it `Player`. Double-click the script to open it in your code editor (e.g., Visual Studio or Visual Studio Code). 

### Namespaces (the `using` lines)

The lines at the very top beginning with `using` are namespaces. They tell your script where to find types and APIs. For example, `using UnityEngine` gives access to Unity-specific classes like `MonoBehaviour` and components such as `Transform`. These lines end with semicolons, just like sentences end with periods.

`Transform` is a class that represents an object’s position, rotation, and scale in 3D space. It’s one of the most commonly used components in Unity. You can find it on any GameObject in the Inspector. 

### Classes and MonoBehaviour

Every C# script you create in Unity defines a class and, by default, names it `NewMonoBehaviourScript`. Rename it to `Player` to match the filename. The `Player` class inherits from `MonoBehaviour`, which is Unity’s base class that enables your script to plug into the engine’s lifecycle (e.g., `Start`, `Update`). Without inheriting `MonoBehaviour`, Unity wouldn’t recognize those lifecycle methods. Everything between the curly braces `{ }` is the class body where your data and behavior live.


---

## Variables (Fields): Storing the State of Your Game

In the `Player` class we'll add a few fields—these are variables declared at the class level. Each variable has a type, a name, and optionally an initial value. Here are the fields in our example. We'll add them one by one:

```csharp
public int Health = 5;
private float Speed = 0.5f;
// bool PlayerIsGrounded = true;
string Display = "Speed: ";
```

* `int` stores whole numbers. If you don’t assign a value, the default for `int` is 0.
* `float` stores decimal numbers. In C# for Unity, append `f` to mark a literal as a float (0.5f); otherwise it’s treated as a double and can cause type errors.
* `bool` can only be true or false. The default value is `false` if not set.
* `string` stores characters and words; always wrap the literal in quotes. Fields without an access modifier, like this one, are private by default.


> A note on access: `Health` is public, so it’s visible in the Inspector and to other scripts. `Speed` is private, so only this script can access it. A common pattern is to keep fields private and expose them in the Inspector with `[SerializeField]`, which preserves encapsulation as projects scale.

---

### Statements and comments

Each instruction typically ends with a semicolon (`;`). You can comment out a line with `//` or block out multiple lines with `/* ... */`—handy for testing or leaving notes.

```csharp
// This is a single-line comment
/* This is a
   multi-line comment */
int x = 10; // This is also a comment
``` 

---

## Unity’s Lifecycle Methods: Start and Update

Unity calls special methods on `MonoBehaviour` at defined times. These methods are declared with the `void` keyword, which means they don’t return a value.

* `Start` runs once on the first frame when the script becomes active. It’s perfect for initialization—in our script we set `Health` to `10` and immediately print it.
* `Update` runs once per frame while the script is active. It’s used for per-frame behavior like input handling, animation state, or—in this example—changing `Speed` every frame and logging it.


---

## Setting a Variable and Printing to the Console

Inside `Start`, we set `Health` to `10` and log it with `Debug.Log(Health)`:

```csharp
void Start()
{
    Health = 10;
    Debug.Log(Health);
}
```

Inside `Update`, we double `Speed` every frame with `Speed = Speed * 2` and log it with `Debug.Log(Display + Speed)`:

```csharp
void Update()
{
    Speed = Speed * 2;
    Debug.Log(Display + Speed);
}
```

---

## Debugging: Printing to the Console

`Debug.Log(...)` is your quickest way to see what’s happening. You can concatenate text and values with `+`, as in `"Speed: " + Speed`. Watch the Console tab in Unity to see those messages arrive in real time.

For performance, avoid spamming `Debug.Log` in shipping builds. Use it while developing, then reduce or gate logs behind conditions.

---

## Running the Script

To test your script, create a GameObject in your scene (e.g., an empty object or a character model), then drag the Player script onto it in the Inspector to add it as a component. Press Play in Unity.

You’ll see `Health` print once, then `Speed` doubling and printing every frame. Stop Play Mode to reset the values.


---

## The Finished Script

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    public int Health = 5;
    private float Speed = 0.5f;
    // bool PlayerIsGrounded = true;
    string Display = "Speed: ";

    void Start()
    {
        Health = 10;
        Debug.Log(Health);
    }

    void Update()
    {
        Speed = Speed * 2;
        Debug.Log(Display + Speed);
    }
}
```

---

## Quiz: Spot and Fix the C# Errors

Test your understanding! Each code snippet below contains a common C# error. Try to identify what's wrong and how to fix it before checking the solutions.

### Error #1
```csharp
int health = 100
Debug.Log(health);
```
**What's wrong here?** 
<details>
<summary>Click for solution</summary>

**Problem:** Missing semicolon after the first statement.
**Fix:** Add a semicolon after each statement.
```csharp
int health = 100;
Debug.Log(health);
```
</details>

### Error #2
```csharp
float speed = 5.5;
```
**What's wrong here?**
<details>
<summary>Click for solution</summary>

**Problem:** Missing 'f' suffix on float literal.
**Fix:** Add 'f' suffix to float literals to avoid type conversion issues.
```csharp
float speed = 5.5f;
```
</details>

### Error #3
Script file is named "Player.cs" but contains:
```csharp
public class PlayerController : MonoBehaviour
{
    // class content
}
```
**What's wrong here?**
<details>
<summary>Click for solution</summary>

**Problem:** Class name doesn't match filename.
**Fix:** Make sure the class name matches the filename exactly.
```csharp
public class Player : MonoBehaviour
{
    // class content
}
```
</details>

### Error #4
```csharp
int score;
Debug.Log("Score: " + score + 10);
```
**What's wrong here?**
<details>
<summary>Click for solution</summary>

**Problem:** Using uninitialized variable and incorrect string concatenation.
**Fix:** Initialize variables before use and use parentheses for math operations.
```csharp
int score = 0;
Debug.Log("Score: " + (score + 10));
```
</details>

### Error #5
```csharp
public class Player
{
    void Start() 
    { 
        Debug.Log("Game started!");
    }
}
```
**What's wrong here?**
<details>
<summary>Click for solution</summary>

**Problem:** Missing MonoBehaviour inheritance.
**Fix:** Inherit from MonoBehaviour to access Unity's lifecycle methods.
```csharp
public class Player : MonoBehaviour
{
    void Start() 
    { 
        Debug.Log("Game started!");
    }
}
```
</details>






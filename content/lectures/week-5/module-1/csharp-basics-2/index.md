---
title: "The Basics of C# (Part 2)"
---

# C# in Unity Part 2: Custom Functions, Conditionals, and Access Modifiers

This follow-up to the first lesson dives deeper into core C# concepts and how they shape behavior in Unity. Using the finished script below, we’ll cover creating custom functions, working with `if`/`else` statements and logical operators, and understanding access modifiers and attributes. These ideas build directly on the first lesson and provide the structure for more complex gameplay logic.

---

## Final Script for Part 2

```csharp
using UnityEngine;

public class Player : MonoBehaviour
{
    [HideInInspector]
    public int Health = 5;
    [SerializeField]
    private float Speed = 0.5f;
    protected bool PlayerIsGrounded = true;
    string Display = "Speed: ";

    void Start()
    {
        Health = 10;
    }

    void Update()
    {
        Speed = Speed * 2;
        // Debug.Log(Display + Speed);
    }

    public void MyNewFunction()
    {
        if (PlayerIsGrounded && Speed > 512f)
        {
            Health++;
            Debug.Log("Grounded speed boost! Health: " + Health);
        }
        else if (!PlayerIsGrounded && Speed > 512f)
        {
            Debug.Log("Player is airborne - no boost applied.");
        }
        else
        {
            Health--;
            Debug.Log("Health: " + Health);
        }
    }
}
```

---

## Creating Custom Functions

In Part 1 you worked with Unity’s built-in lifecycle methods `Start` and `Update`. Part 2 introduces custom functions that you define and call when needed.

* **Definition**: You create a function with the pattern `void MyNewFunction() { }`. The `void` keyword means the function does not return a value.
* **Calling a Function**: To execute it, you must call it from another method—such as inside `Update` or in response to an event. Here, `MyNewFunction` is public so other scripts or UI events can call it even though it isn’t triggered automatically. The function also checks `PlayerIsGrounded`, a `bool` field that subclasses can reuse because it is marked `protected`.

---

## Conditional Logic with If/Else

To control game flow based on conditions, C# provides `if` statements. Inside the parentheses you put a Boolean expression that evaluates to true or false.

### Comparisons and Operators

* `>` and `<` check if a value is greater or less than another.
* `==` checks equality, while `!=` checks inequality.
* Logical operators such as `&&` (and) or `||` (or) combine conditions, and `!` (not) flips a Boolean value.

### Implementation in the Script

In `MyNewFunction`:

```csharp
if (PlayerIsGrounded && Speed > 512f)
{
    Health++;
    Debug.Log("Grounded speed boost! Health: " + Health);
}
else if (!PlayerIsGrounded && Speed > 512f)
{
    Debug.Log("Player is airborne - no boost applied.");
}
else
{
    Health--;
    Debug.Log("Health: " + Health);
}
```

* If the player is grounded **and** moving faster than `512f`, their `Health` increases and the result is printed.
* If the player is airborne while still moving fast, the `else if` branch logs a different message.
* In all other cases the player loses one health point, and the new value is printed.

This structure demonstrates how to branch behavior based on dynamic values, a key practice for gameplay events like scoring, power-ups, or game-over checks.

> To test this function, call `MyNewFunction()` from within `Update()` (or hook it up to an event) and toggle `PlayerIsGrounded` between `true` and `false` in code while the game runs. View the Console window to see how the output changes as `Speed` increases and the grounded state flips.

---

## Understanding Access Modifiers

Access modifiers determine where variables and functions can be used:

* **public**: Accessible from other scripts and visible in the Unity Inspector unless hidden.
* **private**: Accessible only within the same class. By default, Unity does not show private fields in the Inspector unless you add `[SerializeField]`.
* **protected**: Accessible within the same class and any subclasses. Ideal for inheritance scenarios.

### Attributes

Attributes like `[HideInInspector]` and `[SerializeField]` fine-tune how variables appear in the Inspector:

* `[HideInInspector]` hides a public variable (like `Health`) from the Inspector while keeping it accessible to other scripts.
* `[SerializeField]` exposes a private variable (like `Speed`) to the Inspector so you can tweak it without making it public.

These tools help keep your scripts organized and prevent unintended changes.

---

## Key Takeaways

* Custom functions let you organize and reuse code effectively.
* `if`/`else` statements and logical operators are essential for decision-making in gameplay.
* Access modifiers and attributes give you control over variable visibility and script organization.
* Combining these concepts equips you to create interactive, maintainable Unity projects.

With these new tools, you can structure more complex player behaviors and prepare for advanced topics like integrating audio events or sophisticated gameplay systems.

---

### Task: Debug Practice Script

In this exercise, you’ll write a simple Unity script that prints messages to the Console. This will help you practice variables, methods, and Unity’s debugging tools.

#### Steps

1. Create a new C# script and name it `DebugPractice`.
2. Inside the script:
   * Add a `[SerializeField]` private string variable called `playerName`. Give it a default value like `"Alex"`.
   * In the `Start()` method, use `Debug.Log()` to print a welcome message that includes the player’s name. For example:
     `Welcome, Alex!`
   * In the `Update()` method, you’ll check if the player presses certain keys:
     * If the **spacebar** is pressed, print `"Jump!"` to the Console.
     * If the **Escape** key is pressed, print `"Quit Game"` to the Console.

#### How to Detect Key Presses

Unity lets you check for key presses using the **Input system**. The most common function is:

```csharp
if (Input.GetKeyDown(KeyCode.Space))
{
    Debug.Log("Jump!");
}
```

* `Input.GetKeyDown(...)` means “did this key get pressed this frame?”
* `KeyCode.Space` refers to the spacebar.
* You can replace `Space` with other keys, like `KeyCode.Escape` for the Escape key.
* See the [Unity Input documentation](https://docs.unity3d.com/ScriptReference/Input.GetKeyDown.html) for more details.

#### Example Script Structure

Here’s the basic outline (don’t copy-paste — try to write it yourself first):

```csharp
using UnityEngine;

public class DebugPractice : MonoBehaviour
{
    [SerializeField] private string playerName = "Alex";

    void Start()
    {
        // Print a welcome message
    }

    void Update()
    {
        // Check for spacebar
        // Check for escape key
    }
}
```

---

#### Goal

* When the game starts, you should see a welcome message in the Console.
* When you press the spacebar, the Console should say `"Jump!"`.
* When you press Escape, the Console should say `"Quit Game"`.


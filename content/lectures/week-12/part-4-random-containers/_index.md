Source: [(104) Game Audio with Unity and Wwise Part 4: Random Containers, Switches and Basic Scripting - YouTube](https://www.youtube.com/watch?v=UH7OEm_g9Mg&list=PLzlEBXWjqM97U5rHMERc82sTXRBoSB_Fu&index=4)

> Before we start make sure you have Visual Studio installed.

We're starting to get a lot of sounds in our project. Let's organize with with a _Virtual Folder_. Put your sounds in a folder named _Box_. Do the same in the events tab.

## Footsteps

### Wwise

We'll now learn how to add realistic sounding footsteps to our environment. In order to play different footstep sounds on different surface types we'll use _Trigger Areas_.

> Download footsteps sounds [here](https://dakotastateuniversity-my.sharepoint.com/:f:/g/personal/tate_carson_dsu_edu/EmZiG00llDBNlGLEr2ratX0BdfE1MBd35rH4VwmO4TxflQ?e=QFpoKs)

Drag and drop this folder onto the Actor-Mixer Hierarchy. When importing set the parent folder to be a _Random Container_. Add this random container to a folder called _Footsteps_.

Call the random container _Footsteps Grass_. Go into the source editor for each sample and trim the start and end points to remove any silences.

To add more variations to our footsteps we can add random varations in pitch. In the general settings tab of the random container find the pitch section. Click on the little circle and open the _Randomizer_. Alter the min and max offset.

Create an event called _Play_Footsteps_Grass_ to play your random container. Add the event to your soundbank and export.

### Unity

To add these footstep sounds we'll need to start scripting. Go find the _FirstPersonController_ script on the _PlayerCapsule_ and open it.

Find the `private void Update()` function. This runs every frame of the game and is used for interactivity.

Now, find the `private void Move()` function then inside the function look for the lines below:

```c#
if (_input.move != Vector2.zero)
{
    // move
    inputDirection = transform.right * _input.move.x + transform.forward * _input.move.y;
}
```

This code allows our player to move.

We're going to add some code to allow Unity to call our Wwise event when the player moves. Add the code below to the headers section of the code above _Player Grounded_.

```c#
[Header("Wwise Events")]
public AK.Wwise.Event myFootstep;
```

Save the code and Unity should automatically recompile the project. You should be able to see the header on the script and some red text that says _No Event is currently selected_.

Go back to this section of the code:

```c#
if (_input.move != Vector2.zero)
{
    // move
    inputDirection = transform.right * _input.move.x + transform.forward * _input.move.y;
}
```

Add a new line like below to _Post_ an event to trigger the Wwise event when the player moves.

```c#
if (_input.move != Vector2.zero)
{
    // move
    inputDirection = transform.right * _input.move.x + transform.forward * _input.move.y;
    myFootstep.Post(gameObject);
}
```

Now, click on the red text and select your _Play_Footsteps_Grass_ event. You'll hear that too many footsteps are playing at the same time because we're playing an event for every frame that we're moving. We'll need to edit the code again to limit how often the footsteps are played.

Add these two variables under your Wwise Events header:

```c#
private bool footstepIsPlaying = false;
private float lastFootstepTime = 0;
```

Initialize `lastFootstepTime` in the `Awake()` function

```c#
lastFootstepTime = Time.time;
```

Finally, edit the code from the move function to match below:

```c#
if(!footstepIsPlaying)
{
    myFootstep.Post(gameObject);
    lastFootstepTime = Time.time;
    footstepIsPlaying = true;
} else
{
    if(_speed > 1)
    {
        if (Time.time - lastFootstepTime > 100 / _speed * Time.deltaTime)
        {
            footstepIsPlaying = false;
        }
    }
}
```

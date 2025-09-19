---
title: "Software Setup Instructions"
---

# Software Setup Instructions

## 1. Install Unity Hub

- Download and install Unity Hub from the [Unity website](https://unity.com/download).
  - Unity Hub is a management tool for Unity projects and installations.
  - It allows you to manage multiple Unity versions and projects easily.  
- When you open Unity Hub for the first time, you will need to create a Unity ID or log in.

## 2. Install Unity Editor

- The Unity Hub will automatically start downloading the newest version of the Unity Editor (Unity 6.2). This may take some time depending on your internet speed, so do it before class!
- If it does not, you can manually add a version by clicking on the "Installs" tab and then "Add".
  
## 3. Create a Unity Project

- In Unity Hub, go to the "Projects" tab.
- Create a project with the following settings: 

![](new-project.png)

This will take a minute, so be patient.

## 4. Install the 3D Game Kit

- Open the Unity Asset Store in your web browser: [3D Game Kit](https://assetstore.unity.com/packages/templates/tutorials/3d-game-kit-115747).
- Click "Add to My Assets" and then "Open in Unity".
- This will open the Package Manager in Unity.
- Click "download" and then "import" to add the 3D Game Kit to your project.
- Its ok to overwrite any files if prompted.
- Install/update any dependencies if prompted.

When this window pops up click "Next" and then "Import".

![import](import.png)

The editor will take a minute to import all the assets and compile scripts.

## 5. Setting up the Scene

Finally, find the Project tab, then navigate to `Assets > 3DGameKit > Scenes` and double click on `Start` to open the scene.

![](open-scene.png)
Open image in new tab to see full size

To make the project more performant, go to `Edit > Project Settings > Quality` and set the quality to "Performance".

![](quality-setting.png)

> Unity threw compiler errors in `NavMeshLink.deprecated.cs` because old fields like `autoUpdate` and `bidirectional` no longer exist in the updated AI Navigation package. At the same time, duplicate assembly definition GUIDs caused conflicts between legacy and new NavMesh files. The fix was to delete the `Library/PackageCache/com.unity.ai.navigation` folder so Unity could pull a fresh, consistent version of the package, making sure only one copy of the navigation components remained in the project. This reset cleared both the missing symbol errors and the GUID conflicts.


Import TMP Essential Resources if prompted. If you miss this step, you can always go to `Window > TextMeshPro > Import TMP Essential Resources`.


## 6. Play the Scene

Now play the game! Click the play button at the top of the screen.

## 7. Remove Unity Audio and add FMOD

This game comes with audio already implemented in Unity, but we want to use FMOD instead. Go to `Edit > Project Settings > Audio` and uncheck "Disable Unity Audio".


Next, download the FMOD project with audio assets from the 3D Game Kit already included. You should already have FMOD installed from last week. If not, download it from the [FMOD website](https://www.fmod.com/download).

> [Download FMOD Project](3D-Game-Kit-FMOD-Project-BLANK-v2.00.00.zip)

Go ahead and "save project as" to rename the project to something you'll remember.

## 8. Integrate FMOD with Unity

Download the FMOD for Unity integration package from either the [Unity Asset Store](https://assetstore.unity.com/packages/tools/audio/fmod-for-unity-161631) or the [FMOD website](https://www.fmod.com/download#integrations).

If you use the asset store the process is the same as the 3D Game Kit. Click "Add to My Assets" and then "Open in Unity". This will open the Package Manager in Unity. Click "download" and then "import" to add the FMOD for Unity package to your project.

Follow the steps in the FMOD Setup Wizard to link your FMOD project to Unity.

The process includes removing the Unity audio source components and adding FMOD Studio Event Emitter components to the appropriate game objects. It also added an FMOD Listener component to the main camera and removed the Unity Audio Listener component.

Under the `FMOD` menu in Unity, go to `Edit Settings` and set the path to your FMOD project or built banks.

In FMOD Studio, build the banks by going to `File > Build` or pressing `F7`.  

Unity should automatically detect the changes and recompile. If not, just save something in FMOD Studio to trigger a recompile. Unity will also now see your FMOD events.
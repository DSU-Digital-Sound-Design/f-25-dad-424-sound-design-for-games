
## Step-by-Step Guide: Integrating Unity and Wwise

This guide provides a step-by-step walkthrough for integrating Unity with Wwise. Before you begin, make sure you have approximately 20 GB of free space available for the installation process.

### Installation Process

#### 1. Downloading and Installing Launchers

- **Unity Hub**: Download and install Unity Hub from the official [Unity download page](https://unity.com/download).
- **Wwise Launcher**: Download and install Wwise Launcher from the official [Audiokinetic download page](https://www.audiokinetic.com/en/download).

You will need to create user accounts for both Unity and Wwise if you don't already have them. These hubs are essential as they manage different versions of the software and allow you to launch Unity Games and Wwise audio projects.

#### 2. Installing Wwise

- **Check Compatibility**: Refer to the [Release Notes - Wwise Unity Integration 2022.1.1.8100.2644](https://www.audiokinetic.com/en/library/edge/?source=Unity&id=pg_releasenotes.html) to ensure compatibility between Wwise and Unity versions.
- **Wwise Installation**:
  - Launch the Wwise Launcher.
  - Install the latest version of Wwise by selecting the Authoring, SDK, and Samples packages.
  - Choose your operating system as the deployment platform.
  - Unselect all plugins to avoid unnecessary installations.
  - Click install.

#### 3. Installing Unity

- **Unity Installation**:
  - Open Unity Hub.
  - Navigate to the _Installs_ tab and click on _Install Editor_.
  - Install the Unity version suggested in the [Wwise Unity Integration release notes](https://www.audiokinetic.com/en/library/edge/?source=Unity&id=pg_releasenotes.html).
  - Download Visual Studio Devtools if required.
  - Choose support for your operating system as the deployment platform.
  - Monitor the editor's download progress in the downloads section of the Unity Hub.

### Creating a New Unity Project

**Project Setup**:
- Open Unity Hub and select _New Project_.
- Choose the _3D Core_ template.
- Set the editor version to the latest one you installed.
- Once installed, the new project should open automatically, displaying two _GameObjects_: one for the camera and another for the light. You may close the project after this step.

### Integrating Wwise into Your Unity Project

 **Integration Process**:
   - Return to the Wwise Launcher and select the Unity tab.
   - Locate your newly created Unity project.
   - Click on _Integrate Wwise Into Project_ for your Unity project.
   - Proceed without altering the default settings and complete the integration.
   - The Unity project should open automatically after integration. If it doesn't, use the Wwise Launcher to open it manually in Unity.

 **Verifying Integration**:
   - In Unity, notice the new _Wwise Picker_ tab alongside the _Project_ and _Console_ tabs.
   - The Wwise setup should have added a _WwiseGlobal_ object to your project, which contains the primary logic for Wwise.
   - Additionally, an _AkGameObj_ should now be attached to the main camera.

 **Finalizing the Setup**:
   - Go back to the Wwise Launcher and choose _open in Wwise_ to launch your Wwise project.
   - Ensure that the programs are properly connected by confirming that the red flashing text in Wwise has turned green.
   - Check the _Wwise Picker_ tab in Unity for new options that correspond to Wwise features.

<!-- **Source:** [(116) Game Audio with Unity and Wwise Part 1: Intro and Installation - YouTube](https://www.youtube.com/watch?v=OchYfH0wb0U&list=PLzlEBXWjqM97U5rHMERc82sTXRBoSB_Fu)

Now we will begin to learn how to integrate Unity and Wwise.

> Note: Wwise and Unity installations require a lot of space. Ensure you have around 20 GB of free space before starting the installation process.


# Installation

Both Unity and Wwise projects are run through launchers or hubs. We'll need to download and install the [Unity Hub](https://unity.com/download) and the [Wwise Launcher](https://www.audiokinetic.com/en/download). You'll need user accounts for both programs.

After these programs are both installed, launch them. From both launchers, you can launch Unity Games and Wwise audio projects. You can also manage editor versions of both programs. You may end up having multiple versions of Unity for different projects. This is an important feature to enable stability.

## Wwise

> See the [Release Notes - Wwise Unity Integration 2022.1.1.8100.2644](https://www.audiokinetic.com/en/library/edge/?source=Unity&id=pg_releasenotes.html) for the information on which version of Unity will work with the most updated version of Wwise.

Install the latest version of Wwise from the Wwise Launcher. Select the Authoring, SDK, and Samples packages. Choose your current OS as the deployment platform. Deselect all plug-ins and click install to install Wwise.

Click on the samples tab of the Wwise Launcher and install the latest version of the Wwise Adventure Game. On the next page, select _Unity Source Project_.

## Unity

Open up the Unity Hub, select the _Installs_ tab, and click on _Install Editor_. Install the version that is suggested here:

[Release Notes - Wwise Unity Integration 2022.1.1.8100.2644](https://www.audiokinetic.com/en/library/edge/?source=Unity&id=pg_releasenotes.html)

Click on _Unity Hub_ to open it in the Unity Hub. Download the Visual Studio Devtools if you need them. Select support for your OS for the deployment platform. You should be able to see the editor downloading in the downloads section of the Hub.

## Creating a new Unity project

In the Unity Hub, select _New Project_. Select the _3D Core_ template. Also, set your editor version to the latest one you have installed. Once this project is installed, it should open automatically. We now have a project with two _GameObjects_ for the camera and light. You can close the project now.

## Integrate Wwise Into a Unity Project

Now, return to the Wwise Launcher and select the Unity tab. You'll see all your installed projects here. Notice that you now have buttons to _Integrate Wwise Into Project_. Select this option for your recent Unity project. Don’t change any settings and select integrate. After you finish the integration, your Unity project should open automatically. If it doesn't open, go to the Wwise launcher and select _open in Unity_.

Notice the new _Wwise Picker_ tab next to the _Project_ and _Console_ tabs. The Wwise setup process added a WwiseGlobal object, which holds the main logic for Wwise. Finally, on the main camera, we have an _AkGameObj_.

Return to the Wwise launcher and select _open in Wwise_ to open your Wwise project. You should now see that the programs are connected and that the red flashing text has turned green. Also, in the _Wwise Picker_ tab, we have some new options corresponding to Wwise options. -->

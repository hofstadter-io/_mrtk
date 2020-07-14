# Unity MRTK Setup

This document covers how to setup a new Unity project with MRTK.
This is primarily directed at Hololens 2 development, however
adapting for another platform should be relatively easy.
MRTK is designed to deploy to all platforms and in most cases
you will need to add some packages and configuration... tbd.

### Software

- Visual Studio 2019
- Unity Hub
- Unity 2019.3f...
- MRTK libs

__Don't use NuGet, compatibility issues will arise!__

https://microsoft.github.io/MixedRealityToolkit-Unity/README.html

### Unity Project

##### 1. Create new 3D project from Hub

{image}

##### 2. Build Settings

1. Build Settings via `File > Build Settings` menu or `CTRL+Shift+B` shortcut
1. Select `Universal Windows Platform` and target device `HoloLens` and arch `ARM64`
1. Click `Switch Platform` and wait a bit
1. Click `Player Settings`
    1. go to the XR Settings
        1. Check supported (ignore depreciation, there is work towards supporting Unity's new render system)
        1. Select Windows Mixed Reality
        1. Depth Format 16 bit (for performance)
        1. Enable Depth Buffer Sharing (check!)
        1. Stereo Rendering Mode: Single Pass Instanced
    1. go to `TextMeshPro` and select `Import TMP Essentials`


##### 2. Add MRTK packages to your project

https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

Menu: `Assets > Import Package > Custom Package`

After selecting in import, there will be a progress bar and
another small window will popup to let you choose what to include.
Select "all" and "import" unless you know exactly what you want to include / exclude.
After this, there will be one (or more) MRTK settings dialogs. Again,
select all options unless you know what you are doing.
For the audio spacializer, if you don't see the MRTK one, select "none" for now,
it will be an option eventually. Unity may feel unresponsive at times, be patient.
Not all package imports have all dialogs.

- Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0
- Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0
- Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0
- Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0

You will want all of these in your first projects to make things easier. For example, you will be able to copy scenes and other items from the MRTK Examples.

To ensure everything looks right at this point.

- You should have a new `Mixed Reality Toolkit` menu item.
- Your Assets folder shold have 2 new folders, `MRTK` and `MixedRealityToolkit.Generated`.


##### Bonus, simple JSON handling

TotalJSON is a free package which makes working with JSON a breeze!
You can find it in the Unity app store. Simply download an import from there.

http://www.leguar.com/unity/totaljson/


### Scene and Profile setup

Now that Unity has all the things we need, we can create the initial scene setup.
We are going to use the MRTK Scene System because it's not much different to start
and it gives you the ability to create rich, interwoven scenes and content.

We will be making 2 main MRTK scenes and N content scenes.

- ManagerScene: holds the MRTK stuff and global objects and scripts
- LightingScene: MRTK manages a common lighting scene for all other scenes
- ContentScenes: All the other things you will make. You can load this in many combinations,
  create objects and move them between scenes or (typically) to the main scene.


##### 1. Add MRTK to the SampleScene

Then navigate to the menu and add: `Mixed Reality Toolkit > Add to Scene and Configure`

Now select the new `MixedRealityToolkit` in the scene hierarchy (left).
You should see a `MixedRealityToolkit` script on the right now.
Change the dropdown from `DefaultMixedRealityToolkitConfigurationProfile`
to `DefaultHololens2ConfigurationProlile`.

We are now going to:

- clone the top level profile
- setup scene manager
- clone the remaining nested profiles

##### 2. MRTK Configuration Profiles Prep

MRTK profiles are used to configure the system, which has many
interacting components, and enables the modularity in MRTK. 

Top level Profile:

- (left panel) click on "MixedRealityToolkit" in the scene hierarchy.
- (right panel) under the "MixedRealityToolkit" script, click "Copy & Customize"



##### 3. MRTK Scene Manager

The first thing we will do is setup the Scene Manager
because it will create it's own MRTK objects as well
and we need to clean up after this and before cloning.

```
Scene System [enabled]
    (you will see two new scenes)
```

The lower half of that script section (right) should now be available.
You can set "Target Scale" to any of the options, "Room" is a good default to start with.

- Move your MRTK assets to the DefaultManagerScene and remove the one's it added.
- Delete the default lighting in your SampleScene, add a cube
- Now, back in the Scene Manager configuration, make sure to click Update Cached Lighting Settings

##### 4. MRTK Configuration Cloning


Now we are going to traverse the Submenu on the bottom right,
recursively cloning the profiles. We do this so we can customize
any part of the system. If you don't need or want this for any piece,
you can omit that section.


Now for the actual cloning:

You will want to select a common prefix to replace the "New " suggested when cloning.
It is common to use the application name.
You may also wish to shorten "MixedRealityToolkit" to "MRTK" in your profile names.



https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SceneSystem/SceneSystemGettingStarted.html

This is the list to clone (items in parens are suggested config changes)

```  
Camera [enabled]
Camera > Camera Settings Providers
  (check the "Mixed Reality Capture Settings" > "Render from PV Camera" box)

Input [enabled] (skip if not working on input systems, there is a lot here)

Boundary [disabled] (for VR)
Teleport [disabled] (for VR)
Spacial Awareness [disabled] (generally for VR, advanced for MRTK currently but not for long)
  (this one is pretty intensive on the CPU in the HL2)

Diagnostics [enabled] (be sure to disable when shipping to prod)
```

### Adding content scenes

This is best done from the Project tab in my experience.

Any time you add a content scene:

- delete the default objects created with the new scene, possibly add labels
- make sure to add to the scene manager content scene configuration section

##### Example, adding a cube

1. In your `DefaultManagerScene` create a 3d cube.
2. Set the postition to `<0,0,1>` and scale to `<0.1, 0.1, 0.1>` and rotation to anything.


### Building and deploying

1. Build Settings via `File > Build Settings` menu or `CTRL+Shift+B` shortcut
1. Click `Build`, create a new folder `Build` and click `Select Folder`
1. The file explorer should open, click into the `Build Folder` and double click the `<project>.sln` file
1. Change `Debug -> Release` and arch to `ARM64`. You can turn debug back on when needed, and you will still see frame rate and other stats from MRTK.
1. You can now remote debug and deploy!

Note, the first builds will be longer in both. After that they seem keep some things cached.

### Connecting the HL2 to your dev machine

In order to debug or deploy, you will need to connect your HL2
to your dev system. You can apparently do this with a USB cable, but I have had difficulties here. There is also an open issue for the remote player in Unity, so until that is fixed we have to remote debug or deploy. I prefer deploy, it seems to run faster / have a shorter dev cycle.

This is how to connect via wifi.

1. Shared expriences on both ends
1. Wireless Display on Win10

Win10: Settings > Display > { Shared Experiences / Project to this PC }



### More Project Settings to configure


### CSharp Project, Unity, and VS Code




### References

- My original source: https://arvrjourney.com/build-your-first-hololens-2-application-with-unity-and-mrtk-2-3-0-5f431d8cca8
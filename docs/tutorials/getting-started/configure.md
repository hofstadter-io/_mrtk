# Project Configuration

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


##### 3. MRTK Configuration Cloning


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

Scene Manager [disabled] (for now)

Diagnostics [enabled] (be sure to disable when shipping to prod)
```


### More Project Settings to configure

???



---

- [Index](./readme.md)
- Prev: [Creating a new Unity+MRTK project](./create.md)
- Next: [Working with objects](./objects.md)

# Creating a new Unity + MRTK project

Start a new Unity project from scratch and get all the needed addons installed.

#### Starter Projects

You can clone these repos / dirs to start from a builderplate project.
The following is the result of following this Getting Started tutorial.

- [_mrtk/projects/starter](../../../projects/starter)

(see the readme there for how to setup)


## From Scratch

Follow these steps to setup a project from scratch.


### 1. Create new 3D project from Hub

- Open Unity Hub and click "new"
- Select 3D project (the plain one)
- Enter a name and create

### 2. Build Settings

These setup the build settings for HoloLens 2 development.

1. Build Settings via `File > Build Settings` menu or `CTRL+Shift+B` shortcut
1. Select `Universal Windows Platform` and target device `HoloLens` and arch `ARM64`
1. Click `Player Settings`
    1. go to the XR Settings
        1. Check supported (ignore depreciation, there is work towards supporting Unity's new render system)
        1. Select Windows Mixed Reality
        1. Depth Format 16 bit (for performance)
        1. Enable Depth Buffer Sharing (check!)
        1. Stereo Rendering Mode: Single Pass Instanced
    1. go to `TextMeshPro` and select `Import TMP Essentials`
1. Click `Switch Platform` and wait a bit

### 3. Add MRTK packages to your project

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


### 4. NuGet for Unity

You can use many NuGet packages within your Unity project.
Be careful though, not all packages are compatible.

To install the Unity NuGet client, download the latest release from
https://github.com/GlitchEnzo/NuGetForUnity and add import the package like the MRTK ones.


### 4. Bonus packages

Search for the following in the `NuGet > Manage Packages` prompt:

- `Fluxor` (Flux/Redux) https://github.com/mrpmorris/Fluxor
- `Newtonsoft.Json` (JSON handling) https://www.newtonsoft.ocm/json

(alternative) TotalJSON, Make working with JSON easy

TotalJSON is a free package which makes working with JSON a breeze!
You can find it in the Unity app store. Simply download an import from there.

http://www.leguar.com/unity/totaljson/

From the Unity menu bar: `Window > Asset Store` and then search for "TotalJSON"


---

- [Index](./readme.md)
- Prev: [Software Tools & Installation](./software.md)
- Next: [Configure your Unity+MRTK project](./configure.md)


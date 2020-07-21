# Building and deploying

The time is finally here! We can build and deploy our application to the HL2.

Read through this, and get to the point of running or deploying on HL2,
then go to the next section if you haven't already connected the HL2 to your computer.

### Building in Unity

First, we need to build the project with Unity. This will output a VS project.

1. Build Settings via `File > Build Settings` menu or `CTRL+Shift+B` shortcut
1. Click `Build`, create a new folder `Build` and click `Select Folder`

### Building in Visual Studio

Next, we need to build, debug, or deploy the VS project.
The file explorer should open after Unity is done.

1. Click into the `Build` Folder and double click the `<project>.sln` file
1. Change `Debug -> Release` and arch to `ARM64`. This is for performance. You can turn debug back on when needed, and you will still see frame rate and other stats from MRTK.
1. You can now remote debug and deploy!

Note, the first builds will be longer in both. After that they seem keep some things cached.

_Note 2, the first build should use `Debug > Start Without Debug` or `Ctrl+F5`
and be done at the same time you are ready to pair with your HL2 for the first time.
A pin needs to be entered the first time, but after this you can build, debug, and deploy at will._

We typically use the deploy path as this seems to be a bit quicker both to start up and on device.
Ideally, we would be remote rendering directly from Unity, but there's that bug...


---

- [Index](./readme.md)
- Prev: [Working with objects](./objects.md)
- Next: [Connecting and deploying to your device](./connecting.md)

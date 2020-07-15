# Building and deploying

### Building in Unity

First, we need to build the project with Unity. This will output a VS project.

1. Build Settings via `File > Build Settings` menu or `CTRL+Shift+B` shortcut
1. Click `Build`, create a new folder `Build` and click `Select Folder`

### Building in Visual Studio

Next, we need to build, debug, or deploy the VS project.
The file explorer should open after Unity is done.

1. click into the `Build` Folder and double click the `<project>.sln` file
1. Change `Debug -> Release` and arch to `ARM64`. You can turn debug back on when needed, and you will still see frame rate and other stats from MRTK.
1. You can now remote debug and deploy!

Note, the first builds will be longer in both. After that they seem keep some things cached.


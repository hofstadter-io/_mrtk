# Connecting to XR devices

In order to debug or deploy, you will need to connect your HL2 to your computer

You can apparently do this with a USB cable, but I have had difficulties here.
There is also an open issue for the remote player in Unity, so until that is fixed we have to remote debug or deploy.

### Connecting with the HL2 for development

In the HL2...

Find your IP by asking Cortana, "What's my IP address" (you may need to say her name beforehand)

Settings > Update & Security > For Developers

- Turn on developer mode
- Turn on Device portal

Now click the "Pair" button...

Now, go back to Visual Studio and select the dropdown (twice)

- Ensure under `<project> Debug Settings` you have the HL2 IP under `Debug > Machine Name`
- Click the "Start without Debug" and you should eventually see a prompt asking you to pair.

### Using the HL2 device portal

Navigate to the HL2 IP address `/devicepair.htm`

Go through the setup (username, password, pin)

Go to the Mixed Reality Capture section (under the first section)

### Connection HL@ with Miracast

This is better if you just want to stream your POV camera with the renderings.

1. Enable Shared expriences on both ends
1. Your Windows computer will be Wireless Display

Win10: Settings > Display > { Shared Experiences / Project to this PC }

HL2: Settings > System > Shared expreiences (make sure these are enabled)

HL2: From the main window, click the cast button in the bottom right.

Win10: You should see a prompt to allow the device, there may be a pin the first (every) time depending on how you setup Win10 Project to this Computer


### Congratulations, you are now ready to develop with MRTK and HoloLens 2!

You should now have all the tools, setup, and connections to develop
the next generation of applications with MRTK and HoloLens 2.

Don't forget MRTK supports almost all platforms out there, but
do keep in mind mixed reality has enough difference from virtual reality
that the experiences may not be right for the other platform.

(do watch Julia's video too, she talks about all the UX research and learnings they have built into MRTK) (see docs/references.md)

---

- [Index](./readme.md)
- Prev: [Building your MRTK app](./build.md)
- Next: [Use the Scene Manager!](./scenes.md)



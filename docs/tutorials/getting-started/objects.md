# Working with objects

We are now going to add a cube to your project
which you will be able to interact with in the
MRTK rotate, move, scale bounding box style.

### Adding our cube

In your `SampleScene` create a 3D cube.

Now, set the postition to `<0,0,1>`, rotation to `<60,30,0>`, and scale to `<0.1, 0.1, 0.1>`.
You can do this by selecting the cube in the scene hierarchy and then modifying the
transform section on the right.

This will make the cube a reasonable size and
place it in front of the user when your app starts.

### Object Components

Components are how we add rendering configuration
and scripts for behavior to our objects.
At this point, you should see the following components on the cube:

- Transform
- Cube (Mesh Filter)
- Mesh Renderer
- Box Collider
- Default (a shader)

### Adding components and scripts

There are a couple of components we want to add so that
we can work with our cube in the MRTK style and advice.

Now click the "Add Component" button (in the right panel, at the bottom with the cube selected)
and then start typing the name (this is a pattern in much of the Unity UI)
to quickly find the following components:

- `Audio Source`: Based on research around improving experience with lack of tactile feedback
- `NearInteractionGrabbable`: This makes it so we can touch our objects
- `Object Manipulator (Script)`: The improved MRTK interaction helper that defines what inputs (hands) can be used
- `Bounds Control (Script)`: This adds the controls to the bounding box to rotate, move, and scale
- `Rotation Axis Constraint (Script)`: Another MRTK helper to put limits on the rotations (optional)

Now that these are all added, we can start to configure them.


### Configuring the components and scripts

We will now configure our components to create an MRTK style cube.

_Note, for those configurations which look like an empty input box,
you can add the value by dragging and dropping the item or
clicking the tiny "+" button in the input box and searching._

`Mesh Renderer`: This should have been present already.

- Materials > Element0: click the tiny "+" and search for "ClippingBox" that will give the cube a glass like appearence.

`Audio Source`: requires no configuration, sound effects will be added else where.

`NearInteractionGrabbable`: check the "show tether" box


`Object Manipulator (Script)`: Adding sounds for manipulation events

- Under "Mainpulation Events" click the "+" button for the Started and Ended events
    - RuntimeOnly
    - Drag your audio source into the box below
    - Set the new dropdown to `AudioSource.PlayOneShot` 
    - Set the clip to `MRTK_Manipulation_Start` and `MRTK_Manipulation_End` (use the "+" and search for these)

`Bounds Control (Script)`: Setting up the bounding box and control points

- Target Object: the Cube, drag the cube in
- Bounds Override: Cube (Box Collider), drag the box collider in
- Behavior > Activation: "Activate By Proximity and Pointer"
- Visuals > (None (...) Inputs): We are reusing some configurations from an example, feel free to copy and rename.
    - (Click the tiny "+" button and search for these, the names should indicate which goes where)
    - (You'll be using "CoffeeCup1" for all of these, there will probably be 7 options all named the same except for the number)
    - ...BoxDisplayConfiguration
    - ...LinksConfiguration
    - ...ScaleHandlesConfiguration
    - ...RotationHandlesConfiguration
    - ...ProximityEffectConfiguration
    - uncheck the Hide Elements box
- Now for the audio, this will be the same as the last section
    - Start from the bottom and do all four, you can click the "+" on all four immediately to speed things up
    - dragging the audio source is a pain here, minimize all sections between or drag the audio to the bottom
    - the names should align with the event, much like above
    - if you click on one of the audio clips in the right panel, it should open the folder with them all in the project panel. This can make it easy to drag the remainder where they need to be.

`Rotation Axis Constraint (Script)`: Limits the rotation possibilities (optional)

Feel free to play around with this, you can omit or delete too,
it's mostly extra if you want to limit users from having the object rotate
in all sorts of ways at the same time.


### Done, make sure you save your project

We should now be able to run, build, and deploy the cube app.
Try pushing the play button in Unity. You can use the left-shift key to make a hand appear.
Use normal Unity contols to move it around and click to pinch gesture.

If you try to play the app in Unity, and the hand does not show up with the shift key,
stop and restart the player after:

- Select the `MixedReality Toolkit` in the scene hierarchy
- Select the `HandJointService` from it's children
- Ensure the "Show Preview in Scene View" is checked


---

- [Index](./readme.md)
- Prev: [Configure your Unity+MRTK project](./configure.md)
- Next: [Building your MRTK app](./build.md)

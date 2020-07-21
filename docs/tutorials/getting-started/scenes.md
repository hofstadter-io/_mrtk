# MRTK Scene Manager

This section will help you add MRTK Scene Manager to your project.
The next section "MRTK Tour" does not require this setup
and the following tutorial "Complex Scenes" is all about it.

_Generally, this is highly recommended for most application
so that you can create much more rich experiences for your users._


### Adding the MRTK Scene Manager

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

### Add an object to the DefaultSceneManager

Add an object to the DefaultSceneManager,
the "main" or "global" scene and context which is always running.
When your application starts, this is the scene launched which
controls the loading and unloading of other scenes.

Let's add a cube to this scene. If you've been following along, you may very well have on already!

If not, set the postition to `<0,0,1>` and scale to `<0.1, 0.1, 0.1>` and rotation to anything.

### Adding content scenes

This is best done from the Project tab in our experience.

Any time you add a content scene:

- delete the default objects created with the new scene, possibly add labels
- make sure to add to the scene manager content scene configuration section

Try adding two extra scenes, named how you like, Content# is not bad for now.
Add a different 3D object to each, also different from the DefaultSceneManager scene.
Sphere and capsule are good choices.

- Set both scales to `<0.1, 0.1, 0.1>`
- Set one position to `<-1,0,1>` and the other to `<1,0,1>`

You should now have 3 objects in the Unity editor.
If you build and deploy this application, you will only see one for now.

### Loading and unloading scenes

- script to work with scenes
- parameter to config from Unity, for now

After the "MRTK Tour" we will see how to
build complex scenes with menus that make
the experience feel seamless even though
it is composed of many scenes, scripts, and objects.




---

- [Index](./readme.md)
- Prev: [Connecting and deploying to your device](./connecting.md)
- Next: [Advance Setup and Config](./advanced.md)


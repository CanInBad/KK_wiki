---
title: Getting started with Character Modding
contributors:
  - Naelstrof
---

This is an iterative process and there's a lot of things that need to go
right for a full-fledged character to be added to the game.

While there is a lot to do, we can take it in steps, and not everything
needs to be done at once. You might want to start with [Installing the
KoboldKare SDK](Installing_the_KoboldKare_SDK "wikilink") if you haven't
yet.

## Get your hands on a 3D model

First you'll need a character, either you can make one or commission
one, but in the end you'll need a 3D character with the capacity to edit
it.

This tutorial will assume you have a game-ready, rigged and textured 3D
model within Blender like so.

<figure>
<img src="Blender_lilith.png" title="Blender_lilith.png" />
<figcaption>Blender_lilith.png</figcaption>
</figure>

### Ensure the model is facing the correct direction

Blender exports FBX files as -Y being the forward direction.

<figure>
<img src="Lilith_facing_direction.png"
title="Lilith_facing_direction.png" />
<figcaption>Lilith_facing_direction.png</figcaption>
</figure>

Pay attention to the gizmo in the upper right, it shows which way the
character should be facing (the -Y direction).

You may also need to Apply All Transformations so that both the Armature
and the meshes are neutrally rotated (0 rotation on all axis) facing -Y.

## Import the character into Unity

Unity doesn't import Blend files for characters very well, we need more
fine control than that.

### Select both the Body and Armature, then export them together as an FBX with the following settings

<figure>
<img src="Blender_export_fbx_settings.png"
title="Blender_export_fbx_settings.png" />
<figcaption>Blender_export_fbx_settings.png</figcaption>
</figure>

Namely we need to make sure that Apply Scalings is set to FBX Units
Scale, and that Add Leaf bones is turned off.

It's also nice to have the export targeting a folder within the
KoboldKare Assets for quick model iteration.

### Change the fbx model import settings within Unity, using the inspector

Legacy Blendshape Normals: \[x\]

Normals: Import

Generate Lightmap UVs: \[x\]

<figure>
<img src="Unity_fbx_import_model_tab.png"
title="Unity_fbx_import_model_tab.png" />
<figcaption>Unity_fbx_import_model_tab.png</figcaption>
</figure>

### Create Humanoid Avatar

The model we imported must have a Humanoid avatar in order to work with
KoboldKare, this can be done on the Rig tab of the import settings in
the inspector.

<figure>
<img src="Lilith_humanoid_avatar_tab.png"
title="Lilith_humanoid_avatar_tab.png" />
<figcaption>Lilith_humanoid_avatar_tab.png</figcaption>
</figure>

Select Create From This Avatar, then hit apply.

### Configuring the Humanoid Avatar

Hit Configure on the humanoid avatar, and ensure that all the bones are
set up in a way that makes sense.

<figure>
<img src="Lilith_humanoid_avatar_configure.png"
title="Lilith_humanoid_avatar_configure.png" />
<figcaption>Lilith_humanoid_avatar_configure.png</figcaption>
</figure>

You can find extra information on configuring avatars from the Unity
Manual here: [Unity Manual
ConfiguringtheAvatar](https://docs.unity3d.com/Manual/ConfiguringtheAvatar.html)

### Setting up Materials

KoboldKare uses standard metallic PBR maps for its shaders, however it
also has some extra features that are optional that I'll try to cover.

Create fresh materials by right-clicking in the Project tab and click
"Create-\>Material" for each material necessary for your character.

For the Body of your character, you'll want to use the [Kobold
Shader](Kobold_Shader "wikilink"). Fill out the maps that you have,
leave DecalColorMap blank as that's used for decals.

<figure>
<img src="Lilith_kobold_shader.png" title="Lilith_kobold_shader.png" />
<figcaption>Lilith_kobold_shader.png</figcaption>
</figure>

Eyes optionally can be done with [Vilar's EyeV2
Shader](Vilar's_EyeV2_Shader "wikilink"), which is fairly complicated.
Though you can get a wide variety of eye types with it.

<figure>
<img src="Lilith_eye_shader_config.png"
title="Lilith_eye_shader_config.png" />
<figcaption>Lilith_eye_shader_config.png</figcaption>
</figure>

With your materials created, set them up on the Materials tab of your
character's FBX importer:

<figure>
<img src="Lilith_fbx_import_materials.png"
title="Lilith_fbx_import_materials.png" />
<figcaption>Lilith_fbx_import_materials.png</figcaption>
</figure>

## Turning an imported FBX into a playable character

Now that the model is usable within Unity itself, we can start to setup
the character to be a playable one.

### Creating the prefab

We don't want to work on the model directly, so first we create a parent
empty gameObject, place the fbx at the center of it, and turn it into a
prefab by dragging it into the Project tab.

<figure>
<video src="CreatingLilithPrefab.mp4" title="CreatingLilithPrefab.mp4"
controls=""><a href="CreatingLilithPrefab.mp4">Video</a></video>
<figcaption>CreatingLilithPrefab.mp4</figcaption>
</figure>

### Adding the Character Descriptor

With the root of the prefab selected, or with the prefab selected in the
Project tab, click "Open" under the inspector.

<figure>
<img src="Lilith_open_prefab.png" title="Lilith_open_prefab.png" />
<figcaption>Lilith_open_prefab.png</figcaption>
</figure>

Then with the root of the prefab selected within the hierarchy, add a
new Character Descriptor component from within the inspector.

<figure>
<img src="Configured_lilith_character_descriptor.png"
title="Configured_lilith_character_descriptor.png" />
<figcaption>Configured_lilith_character_descriptor.png</figcaption>
</figure>

You'll want to configure the Collider settings to match the torso and
head of the character.

Also set the Body Renderers list to all LOD0 renderers of the character,
if you don't know what LOD0 means, simply put all the renderers in.

### Configuring the bare-minimum

In order for dicks to be attachable to the character, you must manually
add a Crotch attach point.

Simply create an empty on the hip, and position it roughly here.
Z-forward, Y-up.

<figure>
<img src="Lilith_crotch_attach_point.png"
title="Lilith_crotch_attach_point.png" />
<figcaption>Lilith_crotch_attach_point.png</figcaption>
</figure>

Sorry there's no way in the current build to preview what dicks look
like when they're attached to it. See this
[issue](https://github.com/naelstrof/KoboldKare/issues/224) for checking
if this has been fixed or not.

You'll also need to create nipple locations. You can simply create
empties near where the nipples are. This time Y-Forward, for no
particular reason, sorry!

<figure>
<img src="Lilith_nipple_configuration.png"
title="Lilith_nipple_configuration.png" />
<figcaption>Lilith_nipple_configuration.png</figcaption>
</figure>

Make sure to add each empty to the Milk Lactators, if you have more than
two nipples, you can add all of them!

## Testing it in game

Next up, we need to set up a very basic Unity Addressables Asset Group
in order to have KoboldKare recognize it as a playable character. This
is very easy.

1. Select the prefab within the project tab.

2. With your character prefab selected, check "Addressable" within the
inspector.

<figure>
<img src="Addressable_setup_lilith.png"
title="Addressable_setup_lilith.png" />
<figcaption>Addressable_setup_lilith.png</figcaption>
</figure>

3. Click Select next to the Addressable address in order to open up the
Asset Groups.

4. Add a new label to the addressable, we want to specify a character
as a "PlayableCharacter".

<figure>
<img src="Addressable_playable_character_lilith.png"
title="Addressable_playable_character_lilith.png" />
<figcaption>Addressable_playable_character_lilith.png</figcaption>
</figure>

5. Finally move it to a unique group, treat each group like an
individual "mod" bundle.

<figure>
<img src="Addressable_move_Lilith_to_new_group.png"
title="Addressable_move_Lilith_to_new_group.png" />
<figcaption>Addressable_move_Lilith_to_new_group.png</figcaption>
</figure>

6. Feel free to use whatever address you like for your character,
though KoboldKare currently keys characters by their prefab name.
Meaning that this character will always be named "LilithPrefab" until
you change the name of the prefab.

7. Finally, load the MainMenu scene (Found in
KoboldKare/Assets/Scenes/MainMenu.unity), as you should be able to
spawn-in your character within the options!

<figure>
<img src="Lilith_working_in_game.png"
title="Lilith_working_in_game.png" />
<figcaption>Lilith_working_in_game.png</figcaption>
</figure>

## Where to go from here

While we managed to get the character in-game, there's a lot missing
still. On the bright side we can implement each missing feature
iteratively, and even check out how it looks at each step.

Some of these steps are not required, though I highly recommend them:

- [Setting up JigglePhysics](Setting_up_JigglePhysics "wikilink")

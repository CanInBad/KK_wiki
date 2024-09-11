---
title: Creating a modded map
contributors:
  - HolyBanana
  - Naelstrof
  - Goat
---

This article assumes you have finished [Installing the KoboldKare
SDK](Installing_the_KoboldKare_SDK "wikilink").

## Overview

KoboldKare maps are Unity scenes. They require a few specific elements
in order to function properly.

A Game Manager prefab and an Objective Manager/Scene Descriptor object.
The Game Manager prefab is maintained by naelstrof and contains most of
the necessary components to create a map.The Objective Manager, as it's
known in the Main Map, is a game object that has attached scripts.
![](Objective_Manager_Object.png "Objective_Manager_Object.png") At the
time of writing there is not a centrally maintained prefab for this. It
contains the following scripts:

- Objective Manager
- Photon View
- Scene Descriptor
- Play Area Enforcer
- Music Manager
- Day Night Cycle
- Orbit Camera Pivot Basic

In addition to these components within the scene, you'll need three
asset files created in Unity and one image to use as the map select
image.

The three assets each contain a single script. Used scripts are as
follows:

- PlayableMap
- AudioPack
- ExternalCatalogSetup  

The next sections will cover the basics of culminating the above into a
playable map.

## Work In Progress

Open up the KoboldKare SDK and create a new scene.

Tip: You can create a new scene from File \> New Scene. You can also
import a custom scene, but this guide does not cover that.

In your Unity project view, navigate to KoboldKare\Prefabs. Drag the
GameManager prefab directly into your Hierarchy.

Now create a new empty Game Object and name it "Scene Descriptor". It
will be used to house the script mentioned in the overview. This name is
not strictly required, but having consistency is *nice*.

Select the game object and add the following scripts.

- Objective Manager
- Photon View
- Scene Descriptor
- Play Area Enforcer
- Music Manager
- Day Night Cycle
- Orbit Camera Pivot Basic

Now create a basic terrain. All terrain should be in the "World" layer
in your Inspector.

Any water on your map should be in the "Water" layer.

Lastly, decide your spawn position and create a new empty Game Object
there. The object name is not critical, but for the same of consistency,
name it "PlayerSpawn". This object must have the "PlayerSpawn" tag in
the Inspector.

Now that you have a spawn point, select your Scene Descriptor object,
then go to the Scene Descriptor script. Press the plus button next to
Spawn Locations to create a new position in the array. Drag and drop the
PlayerSpawn game object into the created position.

Your work in the Unity scene is done! Save your scene to it's own folder
and move on below.

Select your scene and click "Addressable" in the Inspector and then the
Select button that appears.

Your map will be under the Default Local Group. Click the label drop
down and select "PlayableMap". Now right click on the asset in the list
and select Move Addressables to New Group with the default option.

In the same folder you saved your scene, right click in the project view
and go to Create \> Data , then create a "PlayableMap" and an
"AudioPack".

In the same folder, right click and Create \> Addressables \> New
External Catalog

## Workshop upload Wizard

Open Unity Editor, and from the top menu, select "Tools" \> "KoboldKare"
\> "Upload Steam Workshop Mod". This will launch the wizard. You should
see this window.
![](Screenshot_2023-03-28_161513.png "Screenshot_2023-03-28_161513.png")

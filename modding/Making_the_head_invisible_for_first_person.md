---
title: Making the head invisible for first person
contributors:
  - Naelstrof
---

The game by default puts the camera between the eyes specified within the Rig Configuration of your model.

<div align="center">
   <img src="../images/making-the-head-invisible-for-first-person/HeadVisible.png" alt="HeadVisible.png" width="50%" /><br/>
   <sup>HeadVisible.png</sup>
</div>

Parts inside of the head can be visible from the first person camera, to prevent this we need the following to be set up:

1.  The Vertex Color of the head needs to have 0 alpha.
2.  The head needs to be using the Kobold shader.
3.  Finally, the Renderer needs to be specified in the Character Descriptor.

## Setting the Vertex Color of the head to zero

Blender by default doesn't support setting alpha Vertex Colors, though with the addon [Vertex Color Master](https://github.com/andyp123/blender_vertex_color_master) we can set it.

First we need a vertex group that has 1 weight for the body, and 0 weight for the head. This is what will tell the game to make the head invisible.

<div align="center">
   <img src="../images/making-the-head-invisible-for-first-person/Kobold_bodyMask.png" alt="Kobold_bodyMask.png" width="80%" /><br/>
   <sup>Kobold_bodyMask.png</sup>
</div>

Then we can use [Vertex Color Master](https://github.com/andyp123/blender_vertex_color_master) to transfer the vertex group into the alpha of the vertex colors using this menu in Vertex Paint mode.

<div align="center">
   <img src="../images/making-the-head-invisible-for-first-person/BodyMaskTransferToAlpha.png" alt="BodyMaskTransferToAlpha.png" width="80%" /><br/>
   <sup>BodyMaskTransferToAlpha.png</sup>
</div>

## Ensure the material is using a Kobold shader

This is easy, just make sure the renderer that contains the head is using a Kobold shader, you can select it and use the drop down to change shaders. This might already be set up proper.

<div align="center">
   <img src="../images/making-the-head-invisible-for-first-person/KoboldMaterial.png" alt="KoboldMaterial.png" width="80%" /><br/>
   <sup>KoboldMaterial.png</sup>
</div>

If the material doesn't let you change shaders, then make a new material in the project tab, set it to use the Kobold shader, then drag and drop it on your character's head.

## Specify the renderer in the Character Descriptor

It may already by specified here, but it's required for the game to detect it as something that needs the alpha to be read for visibility.

<div align="center">
   <img src="../images/making-the-head-invisible-for-first-person/KoboldBodyRendererSpecified.png" alt="KoboldBodyRendererSpecified.png" width="80%" /><br/>
   <sup>KoboldBodyRendererSpecified.png</sup>
</div>

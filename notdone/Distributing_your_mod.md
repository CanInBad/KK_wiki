---
title: Distributing your mod
contributors:
  - Naelstrof
---

So now you have some assets that work in editor, and you want to share
them with your friends!

## Prerequisites

### Create the asset groups

You want an asset group that contains all your various additions to the
game. You can find asset groups under the Window-\>Asset
Management-\>Addressables-\>Groups.

<figure>
<img src="Lilith_and_surfmap_asset_groups.png"
title="Lilith_and_surfmap_asset_groups.png" />
<figcaption>Lilith_and_surfmap_asset_groups.png</figcaption>
</figure>

Here I have two mods I want to distribute, SurfMap, and Lilith. I could
distribute them together if I wanted as a single mod, but for this
demonstration I'll keep them separate.

They both already work in editor, without them being a "real" mod. This
is because Unity Addressables hot-loads them without any extra
interaction. The real game will need a bundled up package to load it
though.

### Install the build modules

You also need to install the Windows Build Support module, Mac Build
Support module, and the Linux Build Support module. You can skip the
build module for the system you're on as it comes by default with Unity.

As for the others, you can install them via Unity Hub by clicking on the
gear of the KoboldKare's version of unity and clicking "Add modules".

<figure>
<img src="Add_Modules_button.png" title="Add_Modules_button.png" />
<figcaption>Add_Modules_button.png</figcaption>
</figure>

Then selecting all the modules, and hitting Install after.

<figure>
<img src="Build_support_modules.png"
title="Build_support_modules.png" />
<figcaption>Build_support_modules.png</figcaption>
</figure>

### Creating an External Catalog Setup

Each mod is going to need a unique External Catalog Setup, you can
create one within the project tab with Create-\>Addressables-\>new
External Catalog.

<figure>
<img src="External_catalog_setup.png"
title="External_catalog_setup.png" />
<figcaption>External_catalog_setup.png</figcaption>
</figure>

Make sure you set the Asset Group list to the asset group you expect to
be loaded when the mod loads. You also need to name it by filling out
the Catalog Name field. You can leave BuildPath and Runtime Load Path
alone as they'll be filled out by the uploader.

### Steam account

You must have a Steam account that owns KoboldKare to create mods, as
mods use the workshop for version control and automatic downloading!

Don't worry, you don't need a Steam account to use the mods, only to
create them!

## Building the mod

Armed with our External Catalog, and multi-platform build support, we
can use the Upload Steam Workshop Mod wizard to build it into a
KoboldKare mod. You can access this wizard through
Tools-\>KoboldKare-\>Upload Steam Workshop Mod.

<figure>
<img src="Upload_steam_workshop_mod.png"
title="Upload_steam_workshop_mod.png" />
<figcaption>Upload_steam_workshop_mod.png</figcaption>
</figure>

Now all we need to do is make the wizard happy by solving each problem
listed in the Status.

1.  Specify the external mod you wish to build.
2.  Fill out the info the best you can.
3.  Hit Build

This first build needs to build everything in koboldkare to work
properly. This can take a VERY long time! (Up to around 6 hours!)

Subsequent builds should be much much faster (several minutes).

Please don't distribute the raw built mod without uploading, as it won't
have a proper steam workshop ID, which is used for automatic acquisition
for joining players.

## Uploading the mod

With all the information filled in, and the mod is built, you should be
able to upload it by clicking the upload button in the wizard.

If the mod is a fresh upload, it'll create a new workshop item under
your account and assign its ID to the mod in your local directory.

Otherwise it'll submit an update to the mod.

## Outsourcing Distribution

After uploading the mod to the workshop, your mod will now have a valid
workshop ID, and the mod found locally in your persistent data folder is
now something that's safe to distribute to users outside of steam. You
can simply zip it up and send it to your friends.

They'll be able to locally install the mod, and users joining their
online games will be able to automatically download the mod from Steam
workshop!

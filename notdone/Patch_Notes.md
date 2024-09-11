---
title: Patch Notes
contributors:
  - Toad
  - CanInBad
---

A Copy of patch notes from Naelstrof. Note that this is a rote copy of
the Steam update page and lacks any incidental updates that often occur
between, substantial as they might be. </br>The [KoboldKare
Discord](https://discord.gg/kZqhYQA) has more recent, informal notes.

## September 18, 2021

<https://store.steampowered.com/news/app/1102930/view/5208965764563903575>  
**First foray into open-source!**  
This took a long longer than I expected, though this is the first build
that has zero paid assets in it!

- Despite the majority of the work being spent ripping out paid assets,
  there's still quite a few changes that I'd love to share:

Steam Audio: Instead of messing with my home-grown reverb system,
KoboldKare now uses Steam Audio for some awesome realtime audio
reflections and reverb. This does take a decent amount of CPU, and can
be easily disabled in the \* Audio options menu.

- Raymarched goop: All fluids now use an analytical raymarching
  algorithm to really make things goopy and sloppy, it still needs an
  optimization pass and can be disabled by setting Goop Quality to 0
  under the Graphics Options.
- Custom Terrain system: KoboldKare uses a custom brush-based terrain
  that fully supports very dense grass and even decals! Paint the whole
  world and make a huge mess!
- New stores: A hardware store, a gardening store, and a construction
  building enter the city. All with functioning stock to buy!
- Item rework: No more "egg boxes", you work straight with eggs now.
  Flasks have been replaced by more thematically appropriate gardening
  tools, and there's a dedicated item for milking kobolds now. New
  models for all seeds!

You can change an NPC kobold's inventory by simply throwing equipment at
them!

- Penetration refactor: This is definitely not the last rework, but now
  penetrators can enter any hole (oral), go all-the-way-through, has
  proper oviposition, tentacles, and is generally faster and more
  stable. Definitely makes everything rubbery and stretchy though, hope
  yall like it!
- Multiplayer now has text chat! Press enter to yip and yap with other
  players.
- Better controller support: Menus are now traversable and browsable
  with just a gamepad, and keybinding hints in-game switch to gamepad
  equivalents to help with learning the controls.
- Added buckets, they function as a lower-level watering can, but also
  are great for storing lots of fluids.
- Physics-based animations are no longer flimsy, because ragdoll limbs
  actually have rotation forces now. Definitely needs a bit more dialing
  in though.
- Decals no longer create seams on models if your graphics card supports
  Conservative Rasterization.
- Added an onahole to ZanyZtuff, you can finally jerk other kobolds off,
  or share it with them!
- Player Preference rework: There was a series of bugs that was caused
  by the old json player preference system. All user options will be
  reset and stored in the registry now for simplicity. On the bright
  side options are super clean and easy to work with as a developer!
- Jiggle physics fixes, they work at any framerate, and no longer flip
  out when trying to "catch up" during hitches.
- Temporarily disabled kobold imposters, try not to make too many
  meanwhile please!!
- New map: after testing the large scale map, I've come to the
  conclusion that it wasn't working out! It scoped the project up
  majorly without much of an upside. The map is now smaller and easier
  to work with, it's lacking polish currently but as the project goes on
  the areas will be small but packed with tons of detail and purpose.
- Lighting adjustments, more ambient light, better use of ACES, and a
  new Brightness graphics slider for those who have different kinds of
  monitors.

## June 1, 2021

- Fixed dicks from cumming out their own balls (whoops!)
- I smartened up the serialization of photon prefabs, and accidentally
  broke plants from spawning fruit. This has been fixed!
- Some equipment stacks now (tail bags, bracelets, and tail collars).
  This might be temporary as I figure out how the equipment UI is going
  to work.
- Saving is finally back! It's probably a bit buggy still, though it's
  reusing photon's cached events. If saving is broken, then so is
  joining a multiplayer game! This is a big step in the game, as the
  saving system is entirely generic. I shouldn't have to update/touch it
  again and it should work up until the game is complete (as all the
  work goes into making sure photon can fast-forward the game's state
  for multiplayer).
- You can start a multiplayer game from a save. Though it might act a
  bit funny if the save is from a multiplayer game. Connecting players
  won't know to repossess their kobolds and they'll get copied as they
  join.
- Big audio rework, uses physmaterial to lookup sounds to play. There's
  hard/soft/footstep/scrape sound databases that depend on which object
  hits what. There's around 40 new sound effects, smash stuff together,
  step on stuff, ragdoll! There's going to be some tweaks on it to get
  it dialed in. Sex animations play far too many ragdoll sounds at the
  moment.

## May 20, 2021

<https://store.steampowered.com/news/app/1102930/view/3041597566487645160>

- Terrain and grass was vastly optimized, terrain details no longer
  render in reflection probes or Mirrors. This was an improvement of
  30ms during reflection probe updates. And slight performance increase
  on mirrors. Terrain will have some mismatching layers while we clean
  up some of these broad optimizations.
- Jigglebones and softbody physics now run on a partial fixed timestep,
  should keep them looking consistent at low framerates.
- Graphics memory footprint reduced by around 400mb by deleting
  unnecessary shaders.
- Decal system rework and optimization, I had an epiphany when I
  realized GPU's automatically solve memory fragmentation problems.
  Don't optimize when you don't have to! Now it's stupid simple and
  stupid fast to decal basically everything in the game. (Except
  terrain, terrain is impossible to decal due to how hardcoded they are
  into Unity...)
- Added a seed extractor! It barely works, but it serves its purpose
  well enough as I focus on some other aspects.
- Added seeds and plant types for every type of fruit, most of them are
  stand-ins, though they work! I bet you can figure out where you get
  the seeds.
- Items now have big indicators that help you find them in grass or in
  trees, finding fruit has never been easier!
- Reduced the scale of lots of the farm so it's a little more sane, it's
  probably going to take a few more passes to get the scale of things
  dialed in.
- Physics animations now use derivatives of the animation curves to
  figure out their velocities. They're much more sharply animated now--
  though the hands still flop around. This'll probably be tweaked for
  quite a bit more until I get happy with it.
- Fixed GenericInflatables from being unable to translate or rotate
  jiggleboned bodies (balls now properly drop when they get bigger).
- This is a big one: Kobolds can now have equipment, and they have
  equipment slots. All dildos are now equippable dicks.
- Customization options from the main menu has been pared down,
  customization is now primarily a gameplay and loot feature. If options
  have been removed that you wanted, you'll have to find the
  corresponding customization feature within gameplay.
- 4 new kobold dildos, all being equipment that can just be plopped on
  by any Kobold that tries to "use" them.
- Construction hardhat, and nipple piercings as equipment. Currently
  cosmetic, though it opens the path to lots of other kinds of cosmetic
  customization!
- All equipment can be found as loot by exploring the world for chests.
  Keep an eye out for them!
- Penetrators' shader has been upgraded to do some bezier curve
  adjustments to make them look malleable, and to correct for
  misalignment. This also allowed for physics constraints to be
  loosened, it looks and feels pretty good. Though probably will be
  iterated on continually as I learn more about it.
- Networking refactor: It's only half way done, but I realized I
  probably shouldn't be over-optimizing things by writing custom events
  and managing the cache myself. Most of everything has been converted
  back into basic Pun observables and RPC calls. Player configuration is
  now done through Pun's PlayerCustomProperties feature. The few things
  that haven't been refactored are still pretty unstable. (Animation
  stations, and attachables like flasks). Over the next couple days it
  should get better and better as I get more familiar.

And that's it for now! Something to keep note of is that generated
kobolds also have the pared down generation, and they have no way to
equip different equipment currently. This will be fixed very soon, but
for now you'll have to live with just being able to customize your
playable kobold.

## March 31, 2021

<https://store.steampowered.com/news/app/1102930/view/3005564330485862179>

- This month was a big push for open-source!
- Unity upgrade from the 2019 LTS to the 2020 LTS! This comes with a
  variety of benefits.
- Screen-space Ambient Occlusion is back, enabled by default in the
  Graphics Settings.
- Dynamic Bones asset has been replaced completely. This new in-house
  jiggle bone system has trouble with completely inverting bones
  sometimes. Though allows for squash and stretch!
- VertExmotion asset has been replaced completely. The new in-house
  softbody physics is simpler and more efficient.
- DoozyUI asset has been completely replaced, this includes icons,
  button click sounds, animations, and other things. UI is much more
  static now, though still works!
- Amplify Imposters was completely replaced by simple hand-made
  imposters. They have much less fidelity, but they can be open-sourced!
- Map has been replaced with another work in progress by Firgof! This
  one uses Unity's built-in terrain which we're still getting used to.
  Things might be unoptimized for a while as we figure things out. Make
  sure your computer meets the recommended specs on the store page!
- Player movement rework, now it's proper source b-hopping! Channel your
  phoon to go fast. A speedometer was included to help me debug it, and
  it'll stick around for a short time.
- Complete ragdoll physics rework. I spent a lot of time flipping random
  switches on the black-box that is Unity's physics system. I learned a
  good number of things, and ragdoll physics have been improved
  immeasurably!
- With the new improved ragdoll physics, animations are now physics
  driven! There's a bit of tweaking left to do, but in general any
  physics mishaps can be fixed by (or caused by) a proactive player!
- Players with dicks now only get marginal slowdown from bumping into
  their own.
- Feet now IK to the ground, it can look really goofy sometimes, but in
  general grounds kobold in the world.
- Shadows no longer have seams in them, at the cost of having a bit more
  shadow acne. This was important with the number of structures that
  were affected by the shadow normal bias.
- Dicks have staged flaccidity now, going from packed -\> floppy -\>
  erect. All done with generic monobehaviours. New dicks can have much
  more complex configurations!
- Flared Equine was replaced with one done by the lovely uniform_vixen
  on Twitter.
- I know I say this every other patch, but penetration physics were
  reworked yet again. Re-thought from the ground up, it includes fun
  stuff like solving things in an orbit, and does some cheating to
  purposefully stabilize most configurations. (This also had to be done
  to support non-centered penetrative shapes.)
- Some VFX cleanup: splashes, goop, strands, and fluids were all touched
  up on.
- Optimized a number of scripts, realized a lot of scripts that don't
  need to run very often should NOT run on FixedUpdate-- this leads to
  vicious cycles of trying to catch up on lost time by over-running
  expensive code.
- Added VSync, and target frame rate options under Graphics.
- Freecam now hides the UI.

We're still not quite at being able to open-source the game, but we're
certainly a lot closer!

## February 28, 2021

<https://store.steampowered.com/newshub/app/1102930/view/3041589956031902369>
Here's the patch notes for all the changes in February:
![](Pineapple.png "Pineapple.png")

- Kobolds can face directions during an animation, it's really bad for
  NPCs but players can nod and look places while playing animations.
- Fixed a large number of memory leaks. (Derivatives no longer uses
  Linq, strands allocate all memory needed up front, reusing physics
  collisions, no longer pass array copies for grabs, adjusted how
  components

are searched for usables.)

- NPC kobolds no longer have hover-hands, hover hands are still
  networked for players.
- Complete reworking of inflatable systems, every kobold body part is
  driven from internal reagent containers.
- Dicks use this same inflatable system to get hard.
- Dicks actually source their cum from balls now (they cheat a tiny bit
  to at least get something out each time they pulse).
- Balls can get bigger based on how much pineapple was consumed.
- Balls and boobs both regenerate their reagents each night.
- More network syncing. (fruit no longer gets stuck, all use events are
  cached and played back properly on first join.)
- Added the new pawnshop, it's a full underground area with some stuff
  to buy! It has yet to have a progression system.
- Debris was added to the farm plot, gotta clear it in order to make
  room for new plants!
- Really big bombs can be purchased from the pawnshop.
- Some networking fixes so certain reagent combos no longer cause
  infinite explosions.
- There is now a 15% chance for it to rain each day.
- Added a low quality cloud option (just some 2d clouds) so that they
  can thicken when it rains.
- Ragdolls are actually synced now, this can cause them to slide around
  a bit but in general they're synced.
- Finally actually included the ErrorScene, a blank scene that loads
  when you get disconnected or when you try to join/create a multiplayer
  game from an offline mode.
- More props and map geometry is possible to cover in decals now. Paint
  the world!
- Kobolds can now spawn with hemipenes.
- The script that handles body proportions was optimized! Spawning 30
  kobolds no longer freezes the game for 40+ seconds.
- Dildos can grow by spraying them with eggplant juice or growth
  reagent.
- Dialogue with NPCs has been disabled temporarily as it gets reworked.

## February 2, 2021

<https://store.steampowered.com/newshub/app/1102930/view/3040462341834120431>
Here's the patchnotes for all the changes in January:

- Got clouds working again, they only enable if you're using DirectX,
  Metal, or Vulkan. Since OpenGL seems to have a race condition on the
  rendering causing some tearing.
- Wrote a custom constraint for the precision grabber so that it doesn't
  mess up as much. Now things are less physically accurate, but things
  actually move and rotate consistently now.
- Animations! A first pass of animations were added that can be
  initiated by pressing Use on Kobolds near a valid location. There's
  still lots of problems with it determining which kobold fits which
  animation best (or if they fit whatsoever), but in general it works
  and is really fun if you don't mind kobolds doing strange things.
- Penetrator physics were adjusted to work with the animation system
  better. Penetratees now cheat to just be in the "right" spot. Makes
  characters look really gooey and flexible, but I think it's worth it
  to keep penetrations looking valid each frame.
- Completely threw Unity's Animation Rigging package in the garbage. It
  didn't scale with character's limbs and was generally very expensive
  to turn on and off. Replaced it with a from-scratch IK system that
  knows how to deal with characters of random proportions and sizes.
  This is only used during Animations, and probably still needs a bit of
  tweaking.
- Big optimization pass, after seeing a user with a KoboldKare
  executable needing 13 GB of memory; I spent a long time hunting down
  and squashing unnecessary memory allocations. This not only makes
  KoboldKare take less memory to run, but also prevents the Garbage
  Collector from kicking in as often. Game is much smoother and faster
  now! In general the game went from allocating 10kb PER FRAME to only
  allocating 40 bytes or so each frame. Slight framerate improvement too
  (less GC allocations means less ms spent on allocating).
- Goopy strands were optimized, and in the process I found out they were
  deleting themselves too early, they now stretch until they snap, then
  properly fade out after snapping before self-destructing.
- Kobolds now spawn with a random amount of fat.
- Player kobolds can now adjust their ball size and chubbiness within
  the multiplayer options.
- Finally, I've modularized how inflatable kobold parts work-- and made
  them entirely dependent on reagent containers. This comes with a
  variety of benefits:

<!-- -->

- - Kobold's now have more containers: Belly, breasts, balls,
    subcutaneous, and penetrators.
  - Each container has a set of listeners that drive different aspects
    of the Kobold.
  - For example a Kobold getting hard would require them to pump fluid
    into it. The listener will see this and drive the proper blendshapes
    and activate the correct monobehaviors with a slick animation curve.
  - A Kobold digesting ice cream might turn it into fat and store it in
    the subcutaneous container, a listener will see the fat and drive
    some fattening blendshapes and adjust softbody physics.
  - These inflation listeners are unhooked from the metabolization
    timestep, so they can react instantly to changes that the player
    makes. This means spraying water at a kobold would instantly have an
    effect on their belly, rather than waiting the 1-2 seconds for the
    metabolization tick.
  - Kobolds are now just a set of penetrators, penetratees, and reagent
    containers grouped into categories. This can lead to kobolds with
    multiple sets of penetrators, unique reactions to certain chems, and
    opens the door to make it easy to add all sorts of other kinds of
    creatures.

There's a few things that are totally broken while I fix up interactions
to work with these new modular systems. Just try to keep flasks away
from breasts while I try to fix it over the next couple days!

## January 1, 2021

<https://store.steampowered.com/newshub/app/1102930/view/2942506324962091506>
![](banana.png "banana.png")

- Completely reworked the reagent system, it now supports heat, potency,
  and serialization for multiplayer networking. (Though right now heat
  and potency aren't used yet.)
- Added a banana fruit, it has potassium. Careful! (See
  [Items#Liquids](Items#Liquids "wikilink") for how they work\]\]
- Added the ability to customize your Kobold within Options.
- Options are saved as a JSON again, this is so lower powered laptops
  can change the settings without launching the game.
- Added support for integrated GPUs. Game launches with Vulkan, Metal,
  Direct3D11, and OpenGL options. (See [APIs](APIs "wikilink") for basic
  info)
- Temporarily disabled clouds, they'll come back when I figure a
  graphics api agnostic way to render them.
- Temporarily disabled two of the extra camera angles, going to replace
  it with a more robust 3rd person camera soon when animations come
  around.
- Created a new procedural skybox.
- Added multiplayer! This was a long time coming, but I'm comfortable
  enough with the structure of the game to add it!

## December 2, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2905348457009766785>

- Soft-body physics in the mirror work now.
- Usable system rework, pretty much anything that's usable has icons and
  drag-and-drop conditions for being usable.
- New fatten blendshape for Kobolds-- like, really really fat.

<figure>
<img src="ice.png" title="ice.png" />
<figcaption>ice.png</figcaption>
</figure>

- Added a new craftable chem: Icecream! Requires milk and ice, makes
  kobolds fat (see above). <strong>It has since been renamed to
  milkshake.</strong>
- Added subtractive blending to the decal system. Any fluid that's
  majorly water will actually wash decals now, rather than paint them
  neon blue!
- Kobolds have much broader color expression now, almost pure white and
  black kobolds can exist.
- Kobolds now express themselves as male or female a bit better-- with a
  blendshape that broaden/squares or softens/rounds. It's analogue so
  any kobold can have any combination.
- Added working showers, faucets, bathrooms, drawers, fridges, ovens!
  This will be expanded upon later for some more unique interactions!
  (See [Locations#House](Locations#House "wikilink"))
- Fluid volume painting: You can paint kobolds by dipping them into a
  tub full of chems. The shower also washes them off!
- You can precisely measure and mix chems in the tub, then store the
  resulting fluids into a flask.
- Night-time no longer deals damage, it now instead accumulates monster
  shadow hands that drag you and anything left outside into darkness.
  Running inside quickly quells the monster! Stay safe! (See
  [Dangers](Dangers "wikilink") for more basic info\]\]

## October 28th, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2935744583747934182>

This month I've been trying to pave way for full blown multiplayer--
This has so far been a really good decision because it's forcing me to
clean up how objects interact, and clean up the structure of things. My
code is getting cleaner and easier to work with as I approach actual
multiplayer readiness.

With lots of new players in mind, I finally tried addressing the fact
that the game has really weird controls. I watched a fair number of
people play the game, and they all would try the same things at first--
So I tried to transform my controls to work with what these players
tried! (see [Movement](Movement "wikilink"))

I also finally got Localization in the pipeline, luckily I have a lot of
friendly users who helped me with the translations-- I haven't got
credits ready in the game yet so I might as well post it here:
TabbyCatface: Russian, Ukrainian Translation Slowboii and Kujawiaczek:
Polish Translation Snaked Snake: German Translation LynxModernWitcher:
French Translation Adept Lughir: Dutch Translation

The rest of the languages are machine-translated, if you're interested
in helping with the translation, join the KoboldKare discord!
<https://discord.gg/WGff3rR> (and poke me)

Anyway, here's the patch notes for this month:

- Added localizations for many languages, dialogue is still in the works
  though.
- UI rework, well more like suddenly there's UI. Should help with
  figuring out the controls!
- Press F to ragdoll.
- The "advanced grab" is now buried under a context button (currently
  shift). This button immediately detaches the mouse and lets you aim
  and grab stuff. It also shows some helpful UI buttons you can press so
  you know you can rotate, freeze, and push/pull with it. (See
  [Movement](Movement "wikilink"))
- Controller inputs should now work properly, they still can't drive the
  UI, but it's possible to play with them now (with a bit of
  difficulty). (See [Movement](Movement "wikilink"))
- Casino prototype is in, it's looking really good! Some places inside
  might look empty because I had to temporarily disable the games.
- Ragdoll adjustments and polish, they're still prone to clipping, still
  look dead, and sometimes their bones seem to unhinge-- but for the
  most part they've improved a lot!
- I've enabled Developer Mode for the build, this is to let players give
  more meaningful bug-reports. It can open an annoying debug console
  though, click on it to close it!
- Mirror no longer has an incorrect oblique clipping plane.
- Switched to indirect lighting for baked lighting for just a slight
  improvement in the baked lighting.
- Added a dynamic reflection probe that updates every 3 seconds, it can
  cause some weird artifacts, but in general it makes nights look nicer
  and the environment reflections more convincing.
- Attachables no longer apply any physics (goodbye oscillating
  kobold-flask abominations...)
- Hitboxes on penetrators have been refined, though if they're extremely
  large they'll still "magnet" into things. Smaller ones require much
  more specific aim and purpose.
- Male kobolds can make eggs now, this might not stick around once more
  chems are added though.
- Kobolds ragdoll when thrown, or when their feet are grabbed.

The advanced grab change is something that I've been thinking about for
a long time. It used to be bound to the primary mouse button, and
permanently affixed to the center of the screen. This caused a lot of
confusion though because in practice it was secondary, or even tertiary
to the primary game loop. The first thing any player does as they play
the game is try to water the egg, and the advanced grab isn't useful at
all for that.

And because it was fixed to the center of the screen, it made any sexual
interaction really jarring as you had to shake your entire head with the
motions. So I've decoupled it from the screen, and buried it behind a
context button which switches how your mouse works. The decoupling lets
you shake kobolds and penetrators without making yourself sick, and the
context button allows for me to pop up a bunch of ui to help players
learn how it works. Let me know what you all think about it!

I'll be spending the next couple days updating the patreon, twitter, and
steam page to reflect the changes. Next month I'll hopefully actually be
working on some multiplayer integrations.

## Septemnber 30, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2879447052620472863>

Last month I was discovering a lot of users were completely unable to
play the game, some of them even had VR-ready modern hardware!

I made the difficult decision to downgrade to Unity's URP pipeline. This
means no more volumetric lights, ambient occlusion, and some other fancy
effects.

However, this means even integrated, and mobile hardware can suddenly
play the game reasonably! It took a while but I think I'll be sticking
to URP for a while.

- Casino temporarily removed to make room for the new one (soon).
- Replaced decal system with an "infinite" decal system. Make a huge
  mess!

URP doesn't have a built-in decal solution. I don't actually care about
the individual fidelity of each decal, so what I do is re-use the
lightmap atlases to map some textures to the world. This allows you to
paint the entire world with decals!

- Remade the majority of shaders to work within URP, this required some
  reduction in interpolators so most shaders should be a fair bit more
  efficient!
- The switch to URP allows for real-time reflection probes, I render one
  every 3 seconds and blend to it. Allows for much more accurate
  reflections (especially during night).
- The player is now completely a Kobold, spawns with random stats just
  like any other Kobold. Can even get pregnant, have sex, drink potions,
  and do anything else a Kobold can do.

This was a really big systemic change which pretty much broke
EVERYTHING. I really rushed to get this patch out by the end of the
month, so there's probably a lot of broken things I haven't gotten to
yet. Please be patient as I clean it up!

- Penetrators now don't couple immediately on touch if they're not in
  range of the nearest hole. This means there's no more tripping over
  them. (This was especially frustrating as a player kobold).
- Temporarily disabled AI for the transition into online
  multiplayer-capable systems.
- Fixed the math on rotating props you're holding with R, it should make
  sense from any direction and perspective now. Still needs a bit of
  smoothing to look nice, but it's very functional at the moment.
- Disabled procedural texture generation, this tech was far too
  unstable, slow, and made it difficult to test multiplayer. It probably
  won't come back either, people nowadays don't care about downloading
  an extra 200mb or so anyway.

Patch notes isn't super long since majority of my time this month was
spent switching to URP. Though next month I'm going to have something
extremely exciting to show, might have something to do with online
multiplayer but no promises!

## August 31, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2867058981746371373>

- New genitalia variations (equine flared, tapered).
- You can now freeze grabs by holding m1 then pressing m2.
- Tails can be grabbed and pinned just like any other limb now.
- Added various sound effects, UI prompts to help indicate which buttons
  can be pressed.
- Kobolds now start flaccid, messing with them in any way will get them
  excited.
- Two new soundtracks, also music fades out when you go to bed now.
- Added a "reset all to default" button in the graphics menu.
- Added pregnancy! It's still early in development, though you can
  totally start breeding kobolds finally.
- Recreated all tree assets because the old ones had incorrect normals,
  also got them to properly noise blend so pop-in is less noticeable.
- Replaced custom skybox with HDRP's new fancy procedural skybox. This
  includes stars, and more convincing mornings and evenings.
- Night time actually dips the usually static ambient lighting now too.
  Nights are actually dark now!
- The hand visual that appears when hovering now actually touches and
  moves soft-body physics (you can now touch the boobies).
- Added a reagent scanner that can be used to analyze container's
  reagents. Really useful for the upcoming set of new reagents.
- Kobolds now can vary in contrast and brightness.
- Lots of tiny bugfixes and stability patches.

## August 6, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2744334079857865963>

Here's the changelog of all the stuff I did in July, I tried to keep it
to only interesting stuff, so I've glossed over lots of bugfixes.

This month was mainly to stabilize and polish, starting August I think
I'm ready to do another broad stroke of content!

- Online Substance texture generation, this reduces build size and
  allows me to craft much more detailed worlds! (Though increases load
  times significantly.)
- Reworked penetration physics.
- Kobolds can now have randomized dick shapes (only has two for now).
- Arousal mechanics for male Kobolds, gotta shake em a bit to get them
  excited.
- Many graphics options were actually bugged and not changing their
  quality correctly (only High or Off), now all options work correctly.
- Depth of Field, Panini Projection, and Fov options were added.
- Grabbed objects now turn transparent (if able to) again.
- Now there's nipple approximation for attachables, so boob attachments
  work better.
- Grabbed "weapons" now aim at the cursor rather than forward. This
  helps a lot when multi-firing flasks.
- Input bindings are now serialized and can be changed through a text
  file within the game's userdata folder.
- Reworked softbody colliders and settings, they still need a bit of
  tweaking, but butts should jiggle more and bellies jiggle more
  consistently.
- Pumping, plapping, and sliding sounds for penetrators.
- Disabled dynamic resolution (should prevent some graphics cards from
  crashing as often).
- Kobold hue shift! Kobolds right now spawn with a random hue, in the
  future their hue will be restrained to Kobold species.
- Fixed a UI overlay that was breaking Reshade functionality, only
  useful to Reshade users but worth mentioning! (Thank you LuxIsBored!)

## June 30, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2520276100964116263>

Sorry I've been so quiet about this update, most of my time was spent
trying to home-grow my own behavior tree system for AI. (Technical post
to be found on Patreon.) I also spent a lot of time developing a
conversation system and dealing with a bunch of bugs that were slightly
outside of my control. Anywho I still managed to get some stuff done and
I think it's ready to show!

New Features:

- A dialogue system! The super market sheep now has dialogue and a tiny
  completable quest (Press E to talk). <strong></strong>
- Small button prompts appear near the cursor when you're near
  contextual actions.
- Kobolds now all have their own player controller, and can walk around,
  do actions, jump, and are still very dumb. They'll get smarter as
  development continues...
- Kobolds will path home when night falls, this currently doesn't happen
  during the time-skip so you'll still have to gather them up if you're
  going to skip the day.
- Unity update to the 2020 beta! This might fix some crashing issues for
  some people. (This also makes it so animation overrides work again).
- Music is now used very sparingly, still needs work but now it doesn't
  just loop the 7 tracks or so over and over.
- Some minor graphical improvements (floating dust is more dense, soft
  body physics are more synchronized with character movement, walking
  dust is now visible (again), some minor character retopology and
  weight painting).
- New flamingo character for the casino, doesn't have any dialogue or AI
  yet, but will soon! (<strong>EDIT: As of Jan. 6, 2021, the flamingo
  has been previously removed with the promise of return.</strong>)

Optimizations: Most logic that doesn't need to run every-frame now
doesn't, this includes soft-body physics, penetrator/penetratees
animation updates, AI, and the music manager.

## May 30, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2227539604675244882>

New Features:

- House has been replaced by some brushwork, it looks a bit nicer but
  still isn't finished.
- Basic brushwork for a city has been put in place, it's still a WIP but
  it should give some stuff to explore and an idea of how some city
  buildings might work.
- Two new characters have been made and put into idle poses in their
  respective buildings. (NPC interactions coming soon!)
- Audio reverb zones have been set up, different rooms and building
  locations should have a noticeable difference in audio reverb.
- Many textures have been replace with procedural textures, they still
  aren't generating at runtime, but as soon as a bug in Substance's
  Unity plugin is fixed, we'll be able to have a LOT more high-res
  textures without taking up lots of data.
- Fruits all now have random sizes and contain coherent amounts of
  juices.
- Kwicc n' Thicc has been replaced by a generic super store, the store
  re-stocks each day with a certain amount of goods.
- New main menu, it doesn't have any tessellated geometry or any complex
  parts. This should make it easier for lower-power hardware to at least
  reach the options.
- Penetration physics are now fully physical, this means knots "pop",
  and more complex physics interactions can be had. Needs a bit more
  work still, but the physics seems to come up with reasonable
  solutions.
- The day night cycle is now linear (before nights used to be about 25%
  of a full day) This should allow users to stay up later without being
  surprised at the speed increase.
- Kobolds now have random proportions! They can be really short/stocky
  with a big butt, or really lanky and top-heavy. It's all random!
- Timed the day change during the fade-out so it's harder to tell the
  game froze while generating kobold proportion meshes.
- Decals can now affect the player.

Optimizations:

- Kobold proportion generation has been threaded.
- Reduced max world decals from 1024 to 256, should help people who had
  low fill-rate speeds.
- Animations are now played on physics, this makes them a bit more
  jittery but it's also required for the physics to work well.
- Replaced lots of hand-crafted materials with procedural ones, I have
  yet to reap the full benefits from this but instead of having around
  four 2k texture maps per prop (~20mb), there'll be a single 16kb file
  that generates the textures on runtime. This'll let me use a LOT more
  textures, and a lot more detailed textures without impacting
  hard-drive space soon.

## April 13, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2212898452337930173>

New Features:

- You can now attach nozzles to fruit and use them like flasks to
  extract their fluids.
- Mac support! Mac users can finally play the game on their machines.
  All future updates will include Mac versions, though the Mac build
  won't have grass until some geometry shader business is figured out.

Optimizations:

- Resource based optimization for Kobolds. IK, softbody physics, and
  detailed collisions are only enabled for the 5 closest Kobolds. This
  allows for many many more Kobolds to be active simultaneously!
- Nearby physics objects are now also using this resource optimization
  system. Only 5 of the nearest physics objects will have interpolation
  or continuous hit detection enabled.
- Soft body collisions now have a limit of 5 per Kobold (25 total).
  Before it was unlimited and caused a cascade of calculations whenever
  a bunch of Kobolds got clumped up.

Tweaks:

- Eggs only need 1.2 units of fluid instead of 2 to get to the next
  stage.
- Melon juice metabolization now results in 3.7 units of milk split
  evenly between breasts instead of 1.
- Player's hand is now more centered when grabbing things.
- Strength of player's hold was softened near the center so that giant
  piles of Kobolds freak out less.

## April 7, 2020

<https://store.steampowered.com/newshub/app/1102930/view/2092426528684852248>

- Eggplants no longer turn into melons on save/load.
- Macro Kobolds get properly saved and loaded now.
- Added a tiny tutorial for picking things up, you can't get outside
  without completing it!
- Re-implemented goopy strands, this will be a temporary effect as I
  implement more systems to only make it goopy when it makes sense.
- Fixed rebinding UI not working when playing the game.
- Planted kobolds no longer automatically grow to their next stage
  without being watered. You have to water them each day!
- Black fade-in is no longer tied to if the game is paused or not.
- Re-organized the UI so the most important binds are at the top.
- Linux build is now up-to-date with the Windows one!
- Upgraded HDRP to 7.3.1, this should increase stability for some.
- I believe I fixed the Steam Overlay bug that was causing freezes. Let
  me know if you still freeze with it on!

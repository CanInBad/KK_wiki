---
title: FAQ
contributors:
  - Toad
---

See [Patch Notes](Patch_Notes) for more information of changes over time.

> [!IMPORTANT]
> It is very much outdated


A community guide to known 'flaws', 'bugs', and/or FAQs. **This is likely to be out of date pending review due to previous Wiki issues.**

## FAQ

*A significant amount of bugs are fixed rapidly as they are found, so this list is short.*

### Where did saves go and when will they come back?

- Saves are currently in the works! They are available in the latest steam and itch.io builds, but are still in progress.

### There are these choices when I start the game from steam, which one do I choose?

- For windows, You can choose Vulkan, Direct3D 11, or GLCore. The default is Direct3D 11
- For Mac, you can choose Metal or GLCore. The default is Metal
- For more information see [APIs](../done/APIs)

### Did you know you can fly by ___

- Yes, see [Movement#Flight](../done/Movement#Flight)

### Where do I report log errors or game problems?

As long as you have stayed opted into the anonymous feedback, The developer will get them automatically. The Discord 'Feedback' channel also is a good place to discuss problems. A log file is also made with a few extra details.

> [!NOTE]
> Logs can be found at `%appdata%\..\LocalLow\Naelstrof\KoboldKare`, it is called `Player.log`  
> If you do not have extension enabled it will just appear as `Player.log`

### I want a new thing! Where do I ask for it?

Requests are best made on the discord, but also check out [Suggestions](../notdone/Suggestions) for an unofficial list of suggestions, items in progress, and items that have been turned down.

## Specific Game behaviors

There are some special traits to this game right now

### Size

- Any particular asset can only be up to 10x the starting size
- Growth is logarithmic: Growth is more dramatic at the beginning and slows down the bigger the asset.
- A combination of 2000 units of reagent, or ~100 fruits, will max out your size stat.

#### Magnum Dong

- Gigantic dongs sometimes make kobolds unapproachable/unmovable without being speared.
- All sizes of kobold are subject to a good dicking. They are flexible to no end.

#### Multiplayer

- Multiplayer player sync is not perfect.
  - Ragdolls are never exactly aligned
  - Dick position is not exactly aligned. Traditionally becomes bigger of a problem with a bigger dick.
  - Flasks can desync when attached to a nipple, either because you see the flask attached to your nipple or others see it on yours but not both.
  - Items have ownership, so when someone leaves or quits, the items they 'owned' disappear with them. This is particularly noticeable when the player who started a server leaves, because at that point the majority if not all items and noc kobolds will de-spawn, including unpurchased items.


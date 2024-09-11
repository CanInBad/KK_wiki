---
title: Installing mods without steam ownership
contributors:
  - CanInBad
---

This guide will only affect windows users (for other operating systems,
I haven't test yet. as well as the optional tool which is windows only)

# Prerequisites

- steamcmd - <https://developer.valvesoftware.com/wiki/SteamCMD>
- **OPTIONAL**: Link Shell Extension -
  <https://schinagl.priv.at/nt/hardlinkshellext/linkshellextension.html>  
  or knowledge how to use `mklink /J`

# Downloading mods

1.  open steamcmd and log on with anonymous account - `login anonymous`
2.  type `workshop_download_item 1102930 `<workshopid>, replace
    <workshopid> with the id of the workshop.  
    **For example**: Playable Goodra has workshop id `2978419063` so it
    will be `workshop_download_item 1102930 2978419063`
3.  Locate where it downloaded to (the location can be found in the
    output on steamcmd) and either follow the next step or move/copy
    them to `%appdata%\..\locallow\naelstrof\koboldkare\mods`

# Linking directories

### Link Shell Extension

0.  have Link Shell Extension
1.  if you already done downloading a item off workshop then in your
    <steamcmd-directoryhere>`\steamapps\workshop\content\` should have
    `1102930` folder
2.  right click the `1102930` folder and click on **Pick Link Source**
3.  navigate to `%appdata%\..\locallow\naelstrof\koboldkare\` and delete
    `mods` folder
4.  right click empty space and hover on **Drop As...** \> click on
    **Junction**
5.  rename freshly dropped `1102930` folder to `mods`

this process can be reversed on the pick link source step

### mklink /J

<li>

run CMD as adminstrator

</li>

<li>

navigate yourself to steam's or steamcmd's workshop directory
<steamcmd-directoryhere>`\steamapps\workshop\content\1102930` using cd

<li>

run `mklink /j %appdata%\..\locallow\naelstrof\koboldkare\mods .`, what
this will do is create junction with the `1102930` as original file and
the `mods` folder in appdata is link

</li>

</ol>

congratz, you now can just update in the steam/steamcmd and it will
reflect the loaded mods

# Viewing workshop items

You need a steam account and open
<https://steamcommunity.com/app/1102930/workshop/> in your browser  
Please note that you have to "enable" **MATURE CONTENT FILTERING** on
your account <https://store.steampowered.com/account/preferences>

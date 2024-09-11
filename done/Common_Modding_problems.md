---
title: Common Modding problems
contributors:
  - Naelstrof
---

## Mod works in Editor, but doesn't work in Game

There's a couple of things that can cause this, and the only way to determine what's wrong is by launching the game, loading the mod, then check the Player.log.

You can find the Player.log on Windows at  
`%appdata%\..\LocalLow\Naelstrof\KoboldKare.`

### RemoteProviderException: Invalid path in AssetBundleProvider

```log
RemoteProviderException: Invalid path in AssetBundleProvider:
'E:/SteamLibrary/steamapps/common/KoboldKare/KoboldKare_Data/StreamingAssets/aa\StandaloneWindows64\6b3b77d3a31c8284895a2874b268f945_monoscripts.bundle'
```


A common error is that the `<GUID>_monoscripts.bundle` has changed names. This can happen if your **Local Default Group (Default)** Addressable Asset group has changed GUIDs.

You should use `git` to reset the state of the **Local Default Group (Default)** and rebuild your mod, this should correct the name.

## Mod fails to build

Misconfigured addressables can cause some issues with the build process, unfortunately a lot of it is a black-box with obtuse error messages, and might require some blind tinkering to get working again.

### Index was out of range. Must be non-negative and less than the size of the collection.

```
Index was out of range. Must be non-negative and less than the size of the collection. Parameter name: index
```
We struggled to find the exact cause of this issue, however this process seemed to fix it:

1.  Use git to reset all Addressable files (RMB → discard changes within github desktop), including removing new addressable asset groups you've made.
2.  Double check that your Addressable Asset Groups are back to default, somehow added groups can linger as "missing reference" and must be deleted manually.
3.  Use CTRL + D to duplicate any assets that are included in your mod as an addressable, then delete the original (to shuffle GUIDs).
4.  Re-create the addressable asset group, the external catalog. Set them up.
5.  ENSURE that you re-specify playable map's "Scene" Addressable Asset Reference Scene parameter.  
    I believe this is actually the cause of the issue, as I believe it doesn't update automatically when groups/names/guids update. Re-specifying it after recreating everything should make sure it has a valid link.

One or more of these steps are probably unnecessary, but it was the exact process we did to fix the issue and it worked okay.

## Fork note: per-stack favourites

This fork contains an experimental per-stack favourite system originally developed for PR #183 against GTNewHorizons/InventoryBogoSorter.

The feature allows stacks to be marked as favourites so player-inventory sorting skips those stacks and leaves them in place. It also includes a visible favourite overlay, tooltip text, hotbar support, keybind support, and multiplayer display of another player’s favourite marker.

This implementation stores the favourite marker directly on the `ItemStack` using NBT. That was intentional: the goal was for the favourite to follow the actual stack through normal and modded movement paths such as dragging, shift-clicking, dropping, picking up, transfers, and other inventory interactions. A per-player slot-based implementation would instead become a slot-lock system and would need extra handling to avoid the favourite state drifting when stacks move.

The upstream PR was rejected because the project does not want this information stored on `ItemStack` NBT. I am keeping this fork as-is for reference/use, but I will not be continuing development on this feature.

If someone wants to pick this up and rework it into a non-NBT / per-player data implementation as requested in PR #183, they are free to do so. No credit to me is required.


# Inventory Bogosorter

This is aims to replace the popular Inventory Tweaks mod.

### Why?

Inventory Tweaks API is very limited. It doesn't work well with modular gui libraries like ModularUI. It also has desync bugs, since it is client side only.

### Why rewrite and not just fork?

The Inventory Tweaks code is very unpleasant to work with. I rather write my own clean mod.

---

## Features

- sorting of player inventories in (almost) all modded GUI's (default key is middle mouse button)
- sorting of many modded inventories
- sort buttons for each sortable inventory
- configuring of sort rules (open config with K by default)
- automatically switching out tools wich are about to break
- automatically refill broken tools or used up items
- scroll through vertical slots above a hotbar slots while holding ALT
- several key shortcuts to move items:
  - CTRL + LMB: transfers a single item
  - CTRL + RMB: transfers a single item into an empty slot
  - Space + LMB: transfer the whole inventory
  - ALT + LMB: transfers all items of the same type
  - Space + Q: throws the whole inventory into the world
  - ALT + Q: throws all the items of the same type into the world

## TODO's

- sorting profiles
  - bind certain profiles to a certain block? (might be difficult)
  - radial menu to quickly choose profile
  - choose profile for ae2 and jei
- configurable sort sound
- animation?


### Credits
Dropoff Feature - https://www.curseforge.com/minecraft/mc-mods/dropoff - https://github.com/SCP002/DropOff/tree/1.7.10
Usage Ticker - Quark - https://github.com/VazkiiMods/Quark/blob/1.14/src/main/java/vazkii/quark/client/module/UsageTickerModule.java

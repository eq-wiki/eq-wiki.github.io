order: 4
description: Hyprland Keybinds for eqSh
keywords: docs, desktop, equora, quickshell, hyprland, eqsh, keybinds, linux
author: enviction
image: ../assets/eqsh.svg
title: Keybinds
sidebar_title: Keybinds
summary: Hyprland Keybinds

To assign eqsh actions to keybinds you can use this format

bind = `mod`, `key`, global, eqsh: **`action_name`**

EqSh is designed to be used with a keyboard, which is why it has a lot of actions:

| Action | Description |
| --- | --- |
| widgets | Toggles Widget Edit Mode |
| sigrid | Toggles Sigrid AI Assistant |
| launchpad | Toggles Launchpad |
| lock | Locks the screen |
| unlock | Unlocks the screen (Not recommended) |
| toggleNotchActiveInstance | Toggles the Notchs active instance, opening or closing it |
| toggleNotchInfo | Toggles the Notchs informative mode |
| notificationCenter | Toggles the Notification Center |
| notificationCenterOpen | Opens the Notification Center |
| notificationCenterClose | Closes the Notification Center |
| controlCenterBluetooth | Opens the Bluetooth Menu |
| controlCenter | Opens the Control Center |
| screenshot | Opens the Screenshot Menu |
| screenshotRegion | Opens the Screenshot Region Selector |
| screenshotEntireScreen | Takes a screenshot of the entire screen |
| settings | Opens the Settings |
| spotlight | Opens the Spotlight |

Now this is quite annoying to implement, so we already did it for you:

```text
bind = $mainMod Control, Q, global, eqsh:lock
bindl= $mainMod Control, M, global, eqsh:unlock
bind = $mainMod Control, P, global, eqsh:launchpad
bindl = $mainMod SHIFT,   5, global, eqsh:screenshot
bindl = $mainMod SHIFT,   3, global, eqsh:screenshotEntireScreen
bindl = $mainMod SHIFT,   4, global, eqsh:screenshotRegion
bind = $mainMod Control, W, global, eqsh:widgets
bindl = $mainMod Control, S, global, eqsh:sigrid
bind = $mainMod, Space, global, eqsh:spotlight
bind = $mainMod Control, R, global, eqsh:settings
bind = Shift, XF86Fn, global, eqsh:controlCenter
bind = Control, XF86Fn, global, eqsh:controlCenterBluetooth
bind = $mainMod Shift, H, global, eqsh:toggleNotchActiveInstance
bind = $mainMod Shift, Y, exec, pkill qs
bind = $mainMod Shift, Y, exec, pkill quickshell
```

!!! warning ""
    **Hey!**  
    If you want even more Keybinds and other Hyprland configs you can find them [here](https://github.com/eq-desktop/hyprland-config).
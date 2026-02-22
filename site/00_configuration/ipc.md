order: 3
description: IPC Calls and Commands for eqSh
keywords: docs, desktop, equora, quickshell, hyprland, eqsh, ipc, linux
author: enviction
image: ../assets/eqsh.svg
title: IPC
sidebar_title: IPC
summary: IPC Calls and Commands

## IPC Calls and Commands

You can use `au funcs` to see all available functions and commands.

If you want to call a function or command, use `au ipc` with the namespace, function or command name and the arguments you want to pass.

!!! note "Example:"
    `au ipc eqlock lock`

!!! info ""
    **Note:**
    Some of these commands need further explanation. At the bottom of this page, you can find information about them.

### IPC Calls

| Target | Function | Description |
| --- | --- | --- |
| spotlight | toggle() | Toggle spotlight |
| systemDialogs | **Deprecated** (use modal instead) newDialog(appName, icon_path, title, description, accept, decline, commandAccept, commandDecline, customStyle) | Create a new dialog |
| widgets | editMode() | Toggle edit mode for widgets |
| notificationCenter | toggle() | Toggle notification center |
| eqlock | lock() | Lock the screen |
| eqlock | isLocked() | Get the current lock state |
| eqlock | unlock() | Unlock the screen |
| settings | toggle() | Toggle settings |
| notch | closeAllInstances() | Close all notch instances |
| notch | instance(code) | Create a new notch instance |
| notch | activateInstance() | Activate the currently open notch instance |
| notch | informInstance() | Activate the Inform Mode of the currently open notch instance |
| notch | closeInstance() | Close the currently open notch instance |
| popup | openPopup(iconPath, app, title, description, timeout, aargs) | Open a new popup |
| launchpad | toggle() | Toggle launchpad |
| controlCenter | openWifi() | Open the wifi settings |
| controlCenter | open() | Open the control center |
| controlCenter | openBluetooth() | Open the bluetooth settings |
| controlCenter | close() | Close the control center |
| sigrid | toggle() | Toggle sigrid |
| doNotDisturb | toggle() | Toggle do not disturb |
| doNotDisturb | enable() | Enable do not disturb |
| doNotDisturb | disable() | Disable do not disturb |
| wallpaper | change(path) | Change the wallpaper |
| modal | instance(appName, title, description, actionsJsonPath, iconPath, useIcon) | Create a new modal instance |
| music | getData() | Get the current music data |
| music | next() | Go to the next music track |
| music | previous() | Go to the previous music track |
| music | togglePlay() | Toggle the music playback |
| screenshot | toggle() | Toggle screenshot |
| display    | brighter() | Make the display brighter |
| display    | dimmer() | Make the display darker |

## Advanced IPC Calls

- [Modal](../01_development/modal.md)
    - Create Dialogs, yes/no questions, User Input, and more
- [Notch](../01_development/notch.md)
    - Useful information and shell extensions without distracting the user
- [Popups](../01_development/popup.md)
    - Banner and Toast Notifications that don't distract the user but still get their attention
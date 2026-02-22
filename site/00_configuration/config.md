order: 1
description: Developer-focused documentation for eqSh configuration, hot-reload JSON, appearance, notch apps, docks, and more.
keywords: docs, desktop, equora, quickshell, hyprland, eqsh, setup, linux
author: enviction
image: ../assets/eqsh.svg
summary: Developer-focused Configuration Documentation

# Configuration

This page documents the **eqSh runtime configuration system** (eRCS).  
All configuration is defined in **JSON**, backed by strongly-typed **QML [`JsonObject`](https://quickshell.org/docs/v0.2.0/types/Quickshell.Io/JsonObject/)s**.

This document is **developer-focused** and maps **directly** to the internal QML config objects.

If you want something simpler take a look at the [Customizing](/02_customization/customizing/) page.

!!! info ""
    **Note:**  
    You can edit settings via the built-in application, or use the `au set` CLI command. Changes are hot-reloaded live.

## Config File Location

```text
~/.config/aureli/config.json
```

* Changes are **watched live**
* Invalid keys are ignored
* Missing keys fall back to internal defaults
* The file is rewritten when adapters update

## Top-Level Structure

```json
{
  "account": {},
  "general": {},
  "appearance": {},
  "bar": {},
  "notch": {},
  "dock": {},
  "launchpad": {},
  "dialogs": {},
  "notifications": {},
  "osd": {},
  "screenEdges": {},
  "lockScreen": {},
  "wallpaper": {},
  "widgets": {},
  "screenshot": {},
  "misc": {},
  "sigrid": {}
}
```

Each section corresponds **1:1** with a QML `JsonObject` component.

## `account`

User and device identity.

!!! note "Note:"
    The `activationKey` is a Joke Key. It is **not** required to run eqSh.

| Key                 | Type   | Default Value           | Description                        |
| ------------------- | ------ | ----------------------- | -----------------------------------|
| `activationKey`     | string | `"060-XXX-YYY-ZZZ-000"` | Activation / license key           |
| `serialNumber`      | string | `"FHGOU82OWLDG"`        | Device serial                      |
| `name`              | string | `""`                    | User display name (first and last) |
| `deviceName`        | string | `"MacBook Air"`         | Device label                       |
| `deviceDescription` | string | `"Retina, 13", 2019"`   | Hardware description               |
| `firstTimeRunning`  | bool   | `true`                  | First boot flag                    |
| `avatarPath`        | string | `~/.face`               | Path or `file://` URL to avatar    |

## `general`

Global system behavior.

| Key            | Type   | Default Value | Description                       |          |       |
| -------------- | ------ | ------------- | --------------------------------- | -------- | ----- |
| `darkMode`     | bool   | `true`        | Dark mode                         |          |       |
| `autoDarkMode` | bool   | `false`       | Automatic dark/light switching    |          |       |
| `reduceMotion` | bool   | `false`       | Reduce animations                 |          |       |
| `appleNames`   | bool   | `true`        | Marketing names (Tahoe vs Tahiti) |          |       |
| `deviceLevel`  | string | `"desktop"`   | `desktop`                         | `laptop` | `low` |
| `language`     | string | `"en_US"`     | Locale (`en_US`, `de_DE`, …)      |          |       |

## `appearance`

| Key                  | Type  | Default Value | Description                                          |
| -------------------- | ----- | ------------- | -----------------------------------------------------|
| `iconColorType`      | int   | `1`           | `1=Original`, `2=Mono`, `3=Tinted`, `4=Glass`        |
| `dynamicAccentColor` | bool  | `true`        | Auto accent extraction                               |
| `multiAccentColor`   | bool  | `true`        | Multiple accents (Makes calender widgets accent red) |
| `glass`              | int   | `0`           | Glass mode (0–7)                                     |
| `glass_Color`        | color | `#202369ff`   | Used when glass = Custom (7)                         |
| `accentColor`        | color | `#2369ff`     | Primary accent                                       |

## `bar`

| Key                      | Type   | Default Value                                                                       | Description                            | |
| ------------------------ | ------ | ----------------------------------------------------------------------------------- | -------------------------------------- |-|
| `enable`                 | bool   | `true`                                                                              | Enable bar                             | |
| `height`                 | int    | `30`                                                                                | Bar height (px)                        | |
| `color`                  | color  | `#01000000`                                                                         | Background                             | |
| `useBlur`                | bool   | `false`                                                                             | Blur background                        | |
| `fullscreenColor`        | color  | `#000`                                                                              | When app is fullscreen                 | |
| `monochromeTray`         | bool   | `true`                                                                              | Monochrome tray icons                  | |
| `animateButton`          | bool   | `false`                                                                             | Animate app button                     | |
| `buttonColorMode`        | int    | `1`                                                                                 | `0=color`, `1=accent`, `2=transparent` | |
| `buttonColor`            | color  | `#22ff0000`                                                                         | Used if mode = 0                       | |
| `hideOnLock`             | bool   | `true`                                                                              | Hide on lockscreen                     | |
| `hideDuration`           | int    | `125`                                                                               | Animation duration                     | |
| `rightBarItems`          | list   | `["systemTray","wifi","battery","search","bluetooth","controlCenter","ai","clock"]` | Item order                             | |
| `batteryFormat`          | string | `"%p%"`                                                                             | Battery format                         | |
| `batteryFormatChargin`   | string | `"*%p%"`                                                                            | Charging format                        | |
| `batteryMode`            | string | `"pill"`                                                                            | Display mode                           | `pill`, `percentage`, `number`, `number-pill`, `percentage-pill`, `bubble` |
| `defaultAppName`         | string | `"Equora"`                                                                          | When no window focused                 | |
| `dateFormat`             | string | `"ddd, dd MMM HH:mm"`                                                               | Date format                            | |
| `autohide`               | bool   | `false`                                                                             | Autohide bar                           | |
| `autohideGlobalMenu`     | bool   | `false`                                                                             | Hide global menu                       | |
| `autohideGlobalMenuMode` | int    | `1`                                                                                 | `0=drag`, `1=hover`                    | |

## `notch`

| Key                     | Type   | Default Value | Description                       |
| ----------------------- | ------ | ------------- | --------------------------------- |
| `enable`                | bool   | `true`        | Enable notch                      |
| `camera`                | bool   | `true`        | Fake camera inside notch          |
| `islandMode`            | bool   | `false`       | Dynamic Island mode               |
| `backgroundColor`       | color  | `#000`        | Background                        |
| `color`                 | color  | `#fff`        | Foreground                        |
| `radius`                | int    | `30`          | Corner radius                     |
| `height`                | int    | `28`          | Height                            |
| `margin`                | int    | `2`           | Outer margin                      |
| `minWidth`              | int    | `175`         | Minimum width                     |
| `maxWidth`              | int    | `400`         | Maximum width                     |
| `onlyVisual`            | bool   | `false`       | Disable interaction               |
| `openOnHover`           | bool   | `false`       | Hover opens                       |
| `openHoverMs`           | int    | `125`         | Hover delay                       |
| `hideDuration`          | int    | `125`         | Duration after hover until hide   |
| `fluidEdge`             | bool   | `true`        | Cutout corners                    |
| `fluidEdgeStrength`     | real   | `0.6`         | Strength 0–1                      |
| `signature`             | string | `""`          | Idle text                         |
| `signatureColor`        | color  | `#fff`        | Signature color                   |
| `autohide`              | bool   | `false`       | Hide when unused                  |
| `interactiveLockscreen` | bool   | `false`       | HIGH RISK: interactive lockscreen |

## `dock`

| Key             | Type   | Default Value   | Description               |
| --------------- | ------ | --------------- | ------------------------- |
| `enable`        | bool   | `true`          | Enable dock               |
| `position`      | string | `"bottom"`      | `bottom`, `left`, `right` |
| `autohide`      | bool   | `false`         | Autohide                  |
| `autohideDelay` | int    | `2000`          | Delay (ms)                |
| `showAnimation` | bool   | `true`          | Animate Showing           |
| `scale`         | int    | `1`             | Scale factor              |
| `radius`        | int    | `25`            | Corner radius             |
| `color`         | color  | `#634a4a4a`     | Background                |
| `border`        | color  | `#ff4a4a4a`     | Border                    |
| `apps`          | list   | `...`           | App IDs / eq: entries     |

## `launchpad`

| Key            | Type | Default Value | Description        |
| -------------- | ---- | ------------- | ------------------ |
| `enable`       | bool | `true`        | Enable launchpad   |
| `fadeDuration` | int  | `500`         | Fade duration (ms) |
| `zoom`         | real | `1.05`        | Zoom on open       |

## `dialogs`

| Key                      | Type  | Default Value | Description     |
| ------------------------ | ----- | ------------- | --------------- |
| `enable`                 | bool  | `true`        | Enable dialogs  |

## `notifications`

| Key               | Type  | Default Value | Description             |
| ----------------- | ----- | ------------- | ----------------------- |
| `backgroundColor` | color | `#ff111111`   | Notification background |

## `osd`

| Key         | Type  | Default Value | Description                     |
| ----------- | ----- | ------------- | ------------------------------- |
| `enable`    | bool  | `true`        | Enable                          |
| `color`     | color | `#40000000`   | Background                      |
| `animation` | int   | `1`           | `1=scale`, `2=fade`, `3=bubble` |
| `duration`  | int   | `200`         | Animation time                  |

## `screenEdges`

| Key      | Type   | Default Value | Description |
| -------- | ------ | ------------- | ----------- |
| `enable` | bool   | `true`        | Enable      |
| `radius` | int    | `20`          | Radius      |
| `color`  | string | `"black"`     | Edge color  |

## `lockScreen`

| Key                   | Type   | Default Value                                          | Description         |
| --------------------- | ------ | ------------------------------------------------------ | ------------------- |
| `enable`              | bool   | `true`                                                 | Enable lockscreen   |
| `fadeDuration`        | int    | `500`                                                  | Fade time           |
| `useFocusedScreen`    | bool   | `true`                                                 | Use focused monitor for ui |
| `mainScreen`          | string | `"eDP-1"`                                              | Fallback screen for ui     |
| `interactiveScreens`  | list   | `["eDP-1","DP-1"]`                                     | Allowed screens for ui     |
| `dateFormat`          | string | `"dddd, MMMM dd"`                                      | Date format         |
| `timeFormat`          | string | `"HH:mm"`                                              | Time format         |
| `showName`            | bool   | `true`                                                 | Show user name      |
| `showAvatar`          | bool   | `true`                                                 | Show avatar         |
| `avatarSize`          | int    | `50`                                                   | Avatar size         |
| `userNote`            | string | `""`                                                   | Custom note         |
| `usageInfo`           | string | `"Touch ID or Enter Password"`                         | Hint text           |
| `blur`                | real   | `0`                                                    | Blur                |
| `blurStrength`        | real   | `1`                                                    | Blur strength       |
| `clockZoom`           | real   | `1`                                                    | Zoom on lock        |
| `clockZoomDuration`   | int    | `300`                                                  | Zoom animation      |
| `dimColor`            | color  | `#000000`                                              | Dim color           |
| `dimOpacity`          | real   | `0.1`                                                  | Dim opacity         |
| `zoom`                | real   | `1`                                                    | Overall zoom        |
| `zoomDuration`        | int    | `0`                                                    | Zoom duration       |
| `useCustomWallpaper`  | bool   | `false`                                                | Override wallpaper  |
| `customWallpaperPath` | string | `~/.local/share/equora/wallpapers/Sequoia-Sunrise.png` | Path                |

## `wallpaper`

| Key             | Type   | Default Value                                      | Description      |
| --------------- | ------ | -------------------------------------------------- | ---------------- |
| `enable`        | bool   | `true`                                             | Enable           |
| `desktopEnable` | bool   | `true`                                             | Enable desktop drag to select |
| `path`          | string | `~/.local/share/equora/wallpapers/Tahoe-City.jpeg` | Image path       |
| `folder`        | string | `~/.local/share/equora/wallpapers/`                | Wallpaper folder for wallpaper picker |
| `color`         | color  | `#000000`                                          | Fallback color   |
| `colors`        | list   | See QML defaults                                   | Preset colors for wallpaper picker    |

## `widgets`

| Key               | Type   | Default Value | Description      |
| ----------------- | ------ | ------------- | ---------------- |
| `enable`          | bool   | `true`        | Enable widgets   |
| `radius`          | int    | `25`          | Corner radius    |
| `cellsX`          | int    | `16`          | Grid width       |
| `cellsY`          | int    | `10`          | Grid height      |
| `location`        | string | `"Berlin"`    | Weather location |
| `useLocationInUI` | bool   | `true`        | Show location    |
| `tempUnit`        | string | `"C"`         | `C` or `F`       |
| `wobbleOnEdit`    | bool   | `false`       | Edit animation like on iOS   |

## `screenshot`

| Key      | Type | Default Value | Description        |
| -------- | ---- | ------------- | ------------------ |
| `enable` | bool | `true`        | Enable screenshots |

## `misc`

| Key           | Type | Default Value | Description       |
| ------------- | ---- | ------------- | ----------------- |
| `showVersion` | bool | `false`       | Show eqSh version |

## `sigrid`

| Key                    | Type   | Default Value                                                | Description   |
| ---------------------- | ------ | ------------------------------------------------------------ | ------------- |
| `key`                  | string | `""`                                                         | API key       |
| `model`                | string | `"gemini-2.5-flash"`                                         | Model name    |
| `systemPromptLocation` | string | `~/.local/share/equora/eqsh/config/sigrid_system_prompt.txt` | Prompt file   |
| `options.type`         | string | `"google"`                                                   | Provider type |

## Notes for Developers

* This schema is **authoritative** — generated from QML
* All values are **runtime-bound**
* IPC can mutate most values live
* Unknown keys are preserved but ignored

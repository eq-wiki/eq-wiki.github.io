order: 2
description: Developer-focused documentation for the Aureli CLI, IPC bridge, runtime control, and configuration tooling.
keywords: docs, cli, aureli, eqsh, quickshell, hyprland, linux, ipc
author: enviction
image: ../assets/eqsh.svg
summary: Developer-focused CLI Documentation

# Command Line Interface (CLI)

This page documents the **Aureli CLI tool** (`aureli`).
It acts as a **runtime controller**, **IPC bridge**, and **configuration editor** for the Aureli desktop.

The CLI is designed for:

* Developers scripting Aureli behavior
* Runtime control & debugging
* JSON config mutation
* Launching internal UI components
* Managing Aureli lifecycle
* Managing Aureli Plugins

The CLI communicates with Aureli through:

* **Quickshell execution**
* **Runtime IPC calls**
* **Direct JSON config edits**

---

## Binary

```bash
au [command] [options]
```

You can override the Aureli installation path:

```bash
au -l /custom/path run
```

Default:

```text
~/.local/share/equora/eqsh
```

---

## Runtime Paths

| Path                           | Purpose                              |
| ------------------------------ | ------------------------------------ |
| `~/.local/share/equora/eqsh`   | Aureli installation                  |
| `~/.config/aureli/config.json` | Runtime config                       |
| `~/.config/aureli/runtime`     | Running instance metadata (PID etc.) |

# Core Commands

## `run`

Start Aureli.

```bash
au run
```

| Option  | Description                   |
| ------- | ----------------------------- |
| `--dev` | Runs in foreground (dev mode) |

Behavior:

* Prevents double launch
* Executes eqSh via Quickshell
* Detached by default

## `plugin`

| Command      | Alias      | Description                   |
| ------------- | ---------- | ----------------------------- |
| install      | i          | Install a plugin                |
| uninstall    | rm         | Uninstall a plugin              |
| list        | l          | List installed plugins          |
| meta        | m          | Get plugin meta                 |
| update      | u          | Update a plugin                |
| new        | n          | Create a new plugin              |
| load        |            | Load a plugin from a directory    |
| compile    | c          | Compile a plugin                |

```bash
au plugin [command] [options]
```

## `quit`

```bash
au quit
```

Force kills Aureli using SIGKILL.

---

## `restart`

```bash
au restart
```

Sequence:

1. Kill running instance
2. Relaunch eqSh

---

## `lock`

```bash
au lock
```

Locks the screen.

---

## `update`

```bash
au update
```

Git pulls eqSh repo.

---

## `install`

Installs Aureli from GitHub.

```bash
au install
```

## Plugin

## `installWallpapers`

Installs the default Aureli Wallpapers.

```bash
au installWallpapers
```

## Configuration Commands

## `set`

```bash
au set bar.height 40
```

Supports automatic type casting:

| Input        | Stored As |
| ------------ | --------- |
| `42`         | int       |
| `3.14`       | float     |
| `true/false` | bool      |
| other        | string    |

Nested paths use dot notation:

```bash
aureli set appearance.accentColor "#ff00ff"
```

Hot-reload occurs via eqSh file watchers.

## `get`

```bash
au get bar.height
```

Special:

```bash
au get all
```

Lists top-level sections.

---

## `reset`

Delete a config key.

```bash
au reset bar.height
```

Reset everything:

```bash
au reset --all
```

⚠ Requires restart.

# UI Control Commands

These toggle or spawn UI systems.

| Command               | IPC Target          |
| --------------------- | ------------------- |
| `settings`            | Settings window     |
| `launchpad`           | App grid            |
| `notification_center` | Notification center |

---

## Dialogs

Create system dialog:

```bash
au dialog <app> <icon> <title> <desc> <accept> <decline> <cmdA> <cmdD> <style>
```

Bridges to:

```text
systemDialogs.newDialog
```

---

## Notch Apps

### Create

```bash
au new_notch_app MyApp.qml "Music"
```

### Destroy

```bash
au destroy_notch_app
```

---

# IPC Bridge

## Generic IPC

```bash
au ipc <method> [args...]
```

Example:

```bash
au ipc eqlock lock
```

## Show IPC Functions

```bash
au funcs
```

Lists exposed IPC endpoints.
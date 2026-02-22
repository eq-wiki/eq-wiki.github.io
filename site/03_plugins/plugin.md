order: 1
title: Your First Aureli Plugin
sidebar_title: First Plugin

So you want to make an Aureli plugin? Here's how to get started.

A plugin is a modular piece of functionality for Aureli. It can provide widgets, services, or integrate with the system. All Aureli plugins are described using a **Kavo file**, usually called `plugin.kvo`.

---

## Plugin Structure

At the core of every plugin is a `plugin.kvo` file. Here's an example:

```kavo
plugin "aureli-base" {

    meta {
        name: "Base Aureli System"
        version: "0.1.0"
        api: "Elephant-1"
        description: "This is the Base plugin for all Aureli Widgets"
        author: "Eq Desktop"
    }

    @import "Weather.kvo"

    widget {
        meta {
            name: "Image"
            id: "image"
        }
        onRender() {
            import QtQuick
            import Quickshell.Widgets
            import qs.ui.controls.primitives
            import QtQuick.Layouts
            import QtQuick.Controls
            import qs.ui.controls.providers
            import qs.ui.controls.auxiliary.widget
            import qs.config
            import qs
            WidgetItem {
                id: root
        
                ClippingRectangle {
                    anchors.fill: parent
                    anchors.margins: 4
                    radius: 22
                    color: "transparent"
                    CFI {
                        id: bg
                        anchors.fill: parent
                        colorized: false
                        fillMode: root.options?.fill || true ? Image.PreserveAspectCrop : Image.PreserveAspectFit
                        source: root.options?.source || ""
                    }
                }
            }
        }

        onPlacement(data) {
            data.allow()
        }
    }

}
```

### Breaking It Down

1. **`plugin "id"`**
   This declares the plugin and its internal ID. The ID is used for installing, updating, and managing the plugin with `au plugin`.

2. **`meta`**
   Every plugin must have meta information:

   * `name` — Display name of the plugin
   * `version` — Plugin version
   * `api` — The Aureli API it targets
   * `description` — What the plugin does
   * `author` — Who made the plugin

3. **`@import`**
   Allows importing other Kavo files or plugin modules.

4. **`widget`**
   Declares a widget provided by the plugin. Widgets have:

   * `meta` — Name and internal ID
   * `onRender()` — What the widget displays
   * `onPlacement(data)` — Rules for placing the widget

---

## Creating a New Plugin

To create a new plugin, you can use the CLI:

```bash
$ au plugin new
```

It will prompt you for:

* Plugin Name
* Plugin Id (internal ID)
* Author
* Version
* API
* Description
* Directory to create the plugin (`.` for the current folder or a new name)

It will scaffold a folder with a `plugin.kvo` file ready to edit.

---

## Loading a Plugin from a Directory

If you already have a plugin folder locally and want to load it into Aureli:

```bash
$ au plugin load ./MyPlugin
```

This copies the folder into Aureli’s `plugins` directory.

---

## Installing a Plugin from Git

You can also install a plugin directly from a repository:

```bash
$ au plugin install https://github.com/username/myplugin.git
```

The CLI will:

1. Clone the plugin into a temporary folder
2. Read the `plugin.kvo` meta
3. Check if a plugin with the same ID is already installed
4. Install it into Aureli’s plugin folder if everything is fine

---

## Uninstalling a Plugin

Remove a plugin by its ID:

```bash
$ au plugin uninstall my-plugin
```

This deletes the plugin folder from Aureli.

---

## Updating a Plugin

Update a plugin (if it’s a git repository) using:

```bash
$ au plugin update my-plugin
```

The CLI performs a `git pull --ff-only` in the plugin’s folder.

---

## Listing Installed Plugins

To see all installed plugins:

```bash
$ au plugin list
```

Example output:

```
 · Base Aureli System — Eq Desktop
 ├ Id: aureli-base
 └ Enabled: enabled
```

---

## Viewing Plugin Meta

To view plugin metadata without installing:

```bash
$ au plugin meta https://github.com/username/myplugin.git
```

Example output:

```
Information for 'MyPlugin' Plugin:
Name: MyPlugin
Version: 0.1.0
API: Elephant-1
Description: A simple plugin example
Author: You
```

---

## Tips & Tricks

!!! info "Plugin IDs must be unique"
Aureli identifies plugins by their internal ID. Two plugins with the same ID cannot be installed simultaneously.

!!! info "Scaffolding saves time"
Using `au plugin new` ensures your plugin has the proper structure and meta information.

!!! info "Editable Widgets"
Widgets can use `root.options` to access configurable properties, allowing your plugin to be flexible.

This guide covers everything to **get started building and managing Aureli plugins**. Once you’ve mastered this, you can explore creating more complex widgets, services, and integrations with Aureli’s ecosystem.
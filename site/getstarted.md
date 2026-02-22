order: 2
description: Step-by-step guide to traversing the eqSh Wiki
keywords: docs, desktop, equora, quickshell, hyprland, installation, eqsh, setup, linux
author: enviction
image: ./assets/eqsh.svg
title: Get started
summary: Don't know where to start? Read this.

## What is eqSh?

**eqSh** is a Quickshell-based shell designed for **Hyprland**, built as a single, coherent system rather than a collection of independent components (waybar, rofi, awww).  

It exposes **JSON configuration** and a **powerful IPC layer** for developers to extend and automate the desktop.

eqSh is designed to be

- Scriptable
- Hackable
- Predictable
- Minimal in dependencies
- Stable for long-running environments

## Getting Started

Start here:

1. [**Installing eqSh**](/install/)
2. [**Understanding the Runtime**](/runtime/)
3. [**Configuration Basics**](/00_configuration/config/)
4. [**Your First Notch App**](/01_development/notch/)
5. [**Using IPC from Scripts**](/ipc/)

Each section includes:

- Clear explanations
- Minimal examples
- Practical use cases

Below you can also see a **list of everything this wiki cover**.

## Documentation Scope

This wiki covers

- [**Configuration**](/00_configuration/config/)
    - JSON schema and defaults
    - Hot-reloading behavior

- [**Notch Applications**](/01_development/notch/)
    - Writing custom notch apps in QML
    - Lifecycle, timeouts, and animations
    - IPC-driven notch instances

- **Dialogs & Popups**
    - System dialogs
    - Custom dialog layouts
    - Accept / decline callbacks
    - Styling and theming

- **Notifications**
    - ...

- **IPC Interface**
    - Available IPC endpoints
    - Calling eqSh from scripts
    - Integrating external tools

- **Theming**
    - styles
    - spacing
    - colors

- **Development & Debugging**
    - Logs and runtime state
    - Restarting components
    - Safe iteration workflows

## Who This Wiki Is For

- Developers extending eqSh
- Users writing custom tooling
- People integrating eqSh into workflows
- Anyone curious about the internals

You do **not** need to be a Quickshell expert to get started. This wiki assumes minimal prior knowledge and builds up from first principles.

## Contribution Guidelines

This wiki evolves alongside eqSh.

- Documentation PRs are welcome
- Examples should be minimal and focused
- Prefer clarity over cleverness

If it’s not understandable after one read, it needs work.

## License

eqSh is released under the **Apache-2.0 License**.  
All documentation follows the same spirit: open, inspectable, and modifiable.

## Have fun!

eqSh is not meant to hide complexity, it’s meant to **make it approachable**

This wiki exists to help you understand, extend, and shape the shell.

Let’s build something solid.
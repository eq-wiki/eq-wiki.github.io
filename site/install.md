order: 3
description: Installing eqSh, the Quickshell-based shell for Hyprland
keywords: docs, eqsh, desktop, linux, equora, quickshell, hyprland, install
author: enviction
image: ./assets/eqsh.svg
summary: Installing eqSh has never been easier


You can install eqSh using the [eqSh CLI](https://github.com/eq-desktop/cli).

!!! info "Pre-requisites"
    Don't forget to have python installed on your system.

/// tab | Curl Installation
```bash
$ curl -fsSL https://eqsh-wiki.github.io/get | bash
```
---
///
/// tab | Manual Installation
```bash
$ git clone https://github.com/eq-desktop/cli.git
$ cd cli/
$ ./install.sh
```
Then run the install command:

```bash
$ au install
```
---
///

Afterward, you can launch eqSh using the `au run` command.
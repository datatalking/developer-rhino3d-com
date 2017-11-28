---
title: Rhino Installer Engine
description: This guide is a brief introduction to the Rhino Installer Engine.
authors: ['Brian Gillespie', 'Will Pearson']
author_contacts: ['brian', 'will']
sdk: ['General']
languages: ['All']
platforms: ['Windows', 'Mac']
categories: ['Fundamentals']
origin: http://wiki.mcneel.com/developer/rhinoinstallerengine/overview
order: 6
keywords: ['developer', 'rhino', 'installer']
layout: toc-guide-page
---


## Overview

The Rhino Installer Engine simplifies distribution, installation, and updating of plugins for Rhino for Windows (on both 32- and 64-bit) and Rhino for Mac.

## How It Works

A Rhino Installer Package is a zip file with an *.rhi* extension (or a *.macrhi* extension on Mac).  The *rhi* file can contain directory structures, and can include more than one version of a plugin (for Windows).

There are no file structure or naming requirements.

For example...

    Marmoset.rhi/
    ├── Rhino WIP/
    │   └── Marmoset.rhp
    └── Rhino 5.0/
        ├── x86/
        │   └── Marmoset.rhp
        └── x64/
            └── Marmoset.rhp

...works just as well as...

    Marmoset.rhi/
    ├── Marmoset_rhinowip.rhp
    ├── Marmoset_rhino5_x86.rhp
    └── Marmoset_rhino5_x64.rhp

On Windows, the Rhino Installer Engine examines each plugin and extracts the plugin GUID, Title, Version, and appropriate SDK version numbers.  It also examines each Rhino installed on the computer.

On Windows, the Rhino Installer Engine supports installing AnyCPU plugins written in .NET and will register them with both 32- and 64-bit Rhino 5.  On Mac, the Rhino Installer Engine - and Rhino itself - only support 64-bit installation.

On Windows, each plugin is compared to each installed version of Rhino.  The newest compatible plugin is registered with the corresponding version of Rhino.

## Limitations

- The Rhino Installer Engine will copy files from the *rhi* archive, and will register the plug ins it finds. No other execution is done.
- Currently, it is not possible to digitally sign *rhi* files in order to verify the source of *rhi* files.
- The Rhino Installer Engine is available with Rhino 5 and later.

---

## Related Topics

- [Plugin Installers (Windows)]({{ site.baseurl }}/guides/rhinocommon/plugin-installers-windows)
- [Plugin Installers (Mac)]({{ site.baseurl }}/guides/rhinocommon/plugin-installers-mac)

---
title: "Some Nifty Niceties"
description: Get to know some of the suggested apps to add alongside your Linux desktop.
author: keiaa
date: 2025-05-12 22:26:00 +0800
categories: [Notes, XFCE]
tags: [xfce, linux, unix, foss, open-source]
---

## Baobab

As we use our devices, our files accumulate and take up greater space by time. [Baobab](https://apps.gnome.org/Baobab/) helps you keep track of your disk usage and specifically identify how much space do your files and directories take.

If it's not your type, I suggest taking a look at [`ncdu`](https://dev.yorhel.nl/ncdu). It stands for NCurses Disk Usage, and is a counterpart that runs in a text-mode user interface.

## Catfish

If you're looking for something, chances are it's best done with [Catfish](https://docs.xfce.org/apps/catfish/start). It is a simple search utility powered by Python and GTK3.

All searches are done relative to the directory chose in the location selector. In the sidebar, you may filter and further narrow down your search. Under the settings view, you may choose which directories to exclude from your search.

## Celluloid

If you'd like something simple for your media consumption needs, there is [Celluloid](https://celluloid-player.github.io). It is a simple GTK frontend for `mpv`. According to the project, it aims to be easy to use while maintaining high level of configurability.

It supports `mpv` configuration files as is. It supports playlists, MPRIS2, and loudness normalization. If you prefer using a GStreamer wrapper, I suggest looking at [Parole](https://docs.xfce.org/apps/parole/introduction).

## File Roller

[File Roller](https://gitlab.gnome.org/GNOME/file-roller) helps you manage your archives easily. It supports a wide range of file types such as, but not limited to `.7z`, `.cab`, `.dmg`, `.jar`, `.tar`, `.zip`, and `.rar`.

If you are not comfortable with its graphical interface, I suggest looking at [Engrampa](https://wiki.mate-desktop.org/mate-desktop/applications/engrampa/) and [Xarchiver](https://github.com/ib/xarchiver).

## GNOME Calculator

As you may have noticed, XFCE does not come with a graphical calculator, by default. [GNOME Calculator](https://apps.gnome.org/Calculator/) does come in handy to fill that gap. It supports advanced, financial, and programming modes. 

If you are uncomfortable with GNOME and `libadwaita`, I suggest `mate-calc` and `qalculate` as alternatives. You may also use the `xcalc` utility with the `x11-apps` or use widely available command-line utilities.

## Micro

For your ample text editing needs, [`micro`](https://micro-editor.github.io) saves the day. It is a terminal-based editor, such as the likes of `vim`, `nano` and `emacs`. Despite being rather intimidating, it should be pretty easy to use given the mouse support and relatively sane keybind settings.

Micro supports greater customization through json and Lua if you'd like to configure the editor further. It also supports a full-blown plugin system powered by Lua.

## Pika Backup

[Pika](https://apps.gnome.org/PikaBackup/) lets you do backups the easy way. It allows you to create local and remote backups, as well as set an interval. According to the project, it is designed to save your personal data and does not support complete system recovery.

## Timeshift

> Timeshift is not a backup tool. See [Pika](#pika-backup).
{: .prompt-warning }

Just to be on the safe side, you'd probably like to take a snapshot of your system in case anything goes wrong. [Timeshift](https://github.com/linuxmint/timeshift) is the tool for that. It provides a functionality similar to the System Restore feature in Windows or the Time Machine tool in Mac OS.

You can use it to take incremental snapshots of your file system at regular intervals, which can then be restored later to undo all changes in the system.

## XFCE4 Docklike Plugin

As you may have noticed, launchers and window buttons are separate in XFCE, unlike Cinnamon, GNOME, and KDE. This can easily be circumvented with [`xfce4-docklike-plugin`](https://docs.xfce.org/panel-plugins/xfce4-docklike-plugin/start). It supports pinning on dock, thumbnail previews, and forcing icon sizes.

Follow below instructions to install it on your system.

**Ubuntu**

```bash
sudo add-apt-repository ppa:xubuntu-dev/extras
sudo apt update && sudo apt install xfce4-docklike-plugin
```

**Fedora**

```bash
sudo dnf install xfce4-docklike-plugin
```

**Arch Linux**

```bash
yay -S xfce4-docklike-plugin-git
```

**Building from source**

```bash
tar xvf xfce4-docklike-plugin-<version>.tar.xz && cd xfce4-docklike-plugin-<version>
meson setup build 
meson compile -C build 
sudo meson install -C build
```

## XFCE4 Panel Profiles

The XFCE Panel is configurable to a great extent and it is nice to play around it.

[`xfce4-panel-profiles`](https://docs.xfce.org/apps/xfce4-panel-profiles/start) is a nifty tool to backup, restore, and set panel profiles in XFCE. This is accessible through the topmost view of XFCE's panel preferences when installed. It allows you to save current panel configuration to local storage and export it. You may also import others' panel profiles or go with a preset installed with the package.

## XFCE4 Terminal

XFCE Terminal is a lightweight and easy to use terminal emulator application.

It has multi-tab and drop-down support. It is based on the [Vte terminal widget library](https://gitlab.gnome.org/GNOME/vte/), which offers a well-developed base and excellent Unicode support. If you are experiencing problems with the terminal rendering speed, you may disable anti-aliasing for the terminal font.
---
title: "Some Nifty Niceties"
description: Get to know some of the nice software that works well with XFCE.
author: keiaa
date: 2025-05-12 22:26:00 +0800
categories: [Notes, XFCE]
tags: [xfce, linux, unix, foss, open-source]
---

## Catfish

If you're looking for something, chances are it's best done with Catfish. It is a simple search utility powered by Python and GTK3.

![Main Catfish Window](https://docs.xfce.org/_media/apps/catfish/catfish_window_annotated.png?cache=&w=700&h=470&tok=54502f){: width="700" height="470" .normal }

<sup>A screenshot of Catfish by the [XFCE Development Team](https://xfce.org). Image licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).</sup>

All searches are done relative to the directory chose in the location selector (1). In the sidebar (4), you may filter and further narrow down your search. Under the settings view (3), you may choose which directories to exclude from your search.

## XFCE4 Docklike Plugin

![XFCE4 Docklike Plugin Switch](https://docs.xfce.org/_media/panel-plugins/xfce4-docklike-plugin/xfce4-docklike-plugin-switch.png?cache=&w=375&h=205&tok=83a2d0){: width="375" height="205" .right }

<sup>A screenshot of XFCE4 Docklike Plugin by the [XFCE Development Team](https://xfce.org). Image licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).</sup>

As you may have noticed, launchers and window buttons are separate in XFCE, unlike Cinnamon, GNOME, and KDE. This can easily be circumvented with `xfce4-docklike-plugin`. It supports pinning on dock, thumbnail previews, and forcing icon sizes.

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

![XFCE4 Panel Profiles Window](https://docs.xfce.org/_media/apps/xfce4-panel-profiles-window.png){: width="360" height="434" .right }

<sup>A screenshot of XFCE4 Panel Profiles by the [XFCE Development Team](https://xfce.org). Image licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).</sup>

`xfce4-panel-profiles` is a nifty tool to backup, restore, and set panel profiles in XFCE. This is accessible through the topmost view of XFCE's panel preferences when installed. It allows you to save current panel configuration to local storage and export it. You may also import others' panel profiles or go with a preset installed with the package.

## XFCE4 Terminal

XFCE Terminal is a lightweight and easy to use terminal emulator application.

![XFCE4 Terminal](https://docs.xfce.org/_media/apps/xfce4-terminal/terminal-multiple-tabs.png){: width="646" height="430" .right }

<sup>A screenshot of XFCE4 Terminal by the [XFCE Development Team](https://xfce.org). Image licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).</sup>

It has multi-tab and drop-down support. It is based on the [Vte terminal widget library](https://gitlab.gnome.org/GNOME/vte/), which offers a well-developed base and excellent Unicode support. If you are experiencing problems with the terminal rendering speed, you may disable anti-aliasing for the terminal font.
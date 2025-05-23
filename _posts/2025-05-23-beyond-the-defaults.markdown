---
title: "Beyond the Defaults"
description: Here's a sneak peek. For when "good enough" just isn't gonna cut it.
author: keiaa
date: 2025-05-12 22:59:00 +0800
categories: [Notes, XFCE]
tags: [xfce, linux, unix, foss, open-source]
---

You know XFCE is a gem for customization—tinkering with themes, icons, and fonts is practically a rite of passage. But what if you've done all that, and that nagging feeling still whispers, "Is this *all* there is?" Oh, dear comrade, you've only just scratched the surface.

## GTK CSS

If you have some background in coding or web development, you'll find desktop customization surprisingly intuitive. You can use Cascading Style Sheets (CSS) to finely customize nearly every visual component of your desktop, beyond what your current theme does. For those new to CSS, a comprehensive introduction can be found in this [guide](https://www.w3schools.com/css/).

> GTK supports CSS properties and shorthands as far as they can be applied in the context of widgets, and adds its own properties only when needed. All GTK-specific properties have a -gtk prefix.

To illustrate the practical application of GTK CSS, I would like to share a snippet from my `/home/$USER/.config/gtk-3.0/gtk.css`. I use it to apply a bit of a padding to my Whisker Menu, which may look a bit densely packed by default.

```css
#whiskermenu-window treeview {
  padding: 3px;
}
```

It is important to note that based on above quote, GTK does add their specific properties in the context of widgets. Further details on these GTK CSS properties can be seen in the official [GTK Docs article](https://docs.gtk.org/gtk4/css-properties.html).

## Panel Styling

You may also apply custom CSS directly to the panel for more custom configurations. Typically, most setups choose to style individual panel components to either complement the active theme or adopt a distinct appearance.

Again, to show an example, here's a snippet from my `gtk.css`. This specifically addresses my workspace switcher.

```css
#pager-3 grid {
	background-color: rgba(255,255,255,0.05);
	margin: 4px;
	border-radius: 3px;
}
#pager-3 button {
	padding: 3px;
	margin: 5px;
	background-color: transparent;
}
#pager-3 button:hover {
	background-color: rgba(255,255,255,0.05);
}
#pager-3 button:checked {
	box-shadow: none;
	background-color: #1f9ede ;
	color: #FFF;
}
```

For a more sophisticated example, **Meyza's setup** offers an excellent reference, which you can examine [here](https://github.com/meyzatech/gtk.css-xfce). Similarly, **diws** provides an in-depth customization [guide](https://github.com/meyzatech/gtk.css-xfce) on this topic. Further details on Xfce panel theming are available in the official [Xfce Docs article](https://docs.xfce.org/xfce/xfce4-panel/theming).

Given Xfce's modular architecture, you have the flexibility to replace `xfce4-panel` with alternative panel solutions, such as [`polybar`](https://github.com/polybar/polybar) or [`tint2`](https://github.com/semplice/tint2). While a detailed exploration of these options falls outside the scope of this post, you may refer to the following repositories for further resources.

- [Aditya's Polybar themes](https://github.com/adi1090x/polybar-themes)
- [Addy's Tint2 theme collections](https://github.com/addy-dclxvi/tint2-theme-collections)

## Xfwm4 Theme Editing

When themes don't cut it, the easiest choice is to edit them. Better yet, create a new one if you know how to. According the the Xfce documentations, Xfwm4 uses a pixmap-based theme engine using images in [`.xpm`](https://en.wikipedia.org/wiki/X_PixMap) format. These themes are searched for in the following directories:

- `/home/$USER/.themes/`
- `/usr/share/themes/`
- `/usr/local/share/themes`

Included in a standard `xfwm4` theme is a `themerc`. It serves as the core configuration blueprint for an Xfwm4 theme. Unlike GTK CSS which styles the content *within* application windows, `themerc` is specifically responsible for defining the appearance and behaviour of the window's "frame" - its title bar, borders, and control buttons.

For a comprehensive example, **Addy's collection** offers an excellent reference, which you can examine [here](https://github.com/addy-dclxvi/xfwm4-theme-collections). Further details on Xfwm4 theming can be found in its official [Xfce Docs article](https://wiki.xfce.org/howto/xfwm4_theme).

## Qt App Styling

Given that XFCE primarily utilizes the **GTK widget toolkit**, applications built with **Qt** are often noticeably inconsistent with a uniformly themed GTK desktop. While I generally recommend favoring GTK-based applications for their seamless integration with XFCE, there are certainly instances where using a specific Qt application becomes a necessity.

Though I have not really delved much into these applications and don't have much to say about it, I suggest checking **Kvantum**. This SVG-based theme engine for Qt offers extensive customization capabilities, allowing for deep visual integration with your desktop. Further details on its setup and usage can be found in its official [installation guide](https://github.com/tsujan/Kvantum/blob/master/Kvantum/INSTALL.md).

## Other resources

This section compiles additional resources highly relevant to advanced XFCE theming, intended to further assist readers.

- [Addy's GTK theme collection](https://github.com/addy-dclxvi/gtk-theme-collections)
- [Mehedirm's Miserable Xfce setup](https://github.com/mehedirm6244/Miserable_Xfce)
- [Mehedirm's Serenade video demonstration](https://www.youtube.com/watch?v=gfmeCiskZwM)
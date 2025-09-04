---
title: "Beyond the Defaults"
description: Here's a sneak peek. For when "good enough" just isn't gonna cut it.
author: keiaa
date: 2025-05-12 22:59:00 +0800
categories: [Notes, Xfce]
tags: [xfce, linux, unix, foss, open-source]
---

You know Xfce is a gem for customization—tinkering with themes, icons, and fonts is practically a rite of passage. But what if you've done all that, and that nagging feeling still whispers, "Is this *all* there is?" Oh, dear comrade, you've only just scratched the surface.

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

### GTK Inspector

While directly editing `gtk.css` files provides greater customization, identifying the precise elements to target can be challenging. This is where the GTK Inspector becomes a helpful tool for anyone delving into advanced GTK CSS theming. The GTK Inspector is a developer utility that allows you to examine the structure and properties of any running GTK application in real-time. When activated, it presents a comprehensive view of the widget hierarchy, which enables you to:

- **Identify Widget Names and Classes**: Pinpoint the exact CSS class names or IDs associated with specific buttons, menus, panels, or other UI components. This is crucial for writing targeted CSS rules.
- **Inspect Applied Styles**: See which CSS rules are currently affecting a selected widget, including their origin and precedence. This helps you understand why an element looks the way it does.
- **Live Edit CSS**: Experiment with CSS changes directly within the Inspector. You can modify rules and see the visual impact immediately which greatly accelerates the iterative process of theme development without needing to save files and restart applications.
- **Explore Properties and Signals**: Beyond styling, it offers insights into widget properties and signals, which can be useful for deeper understanding of GTK applications.

> You may have to enable the associated keybinding first.<br>`gsettings set org.gtk.Settings.Debug enable-inspector-keybinding true`
{: .prompt-tip }

To launch the GTK Inspector for most applications, you typically start the application with the `GTK_DEBUG=interactive environment` variable (e.g., `GTK_DEBUG=interactive xfce4-panel`). Alternatively, within a running GTK application, you can press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd> or <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>D</kbd> to bring it up, depending on the GTK version and application. Further details on it can be found in the official [GNOME Developer Documentation article](https://developer.gnome.org/documentation/tools/inspector.html).

### Other styling considerations

Beyond the direct manipulation of `gtk.css` for a specific theme or user overrides, several other factors influence the overall appearance of GTK applications on your desktop. Understanding these can help you achieve a more refined and consistent aesthetic:

> There may be some properties deprecated in newer versions of GTK. In such case, customizing the `gtk.css` is preferred as an alternative approach.
{: .prompt-warning }

- **Manual Configuration Files**: While graphical tools simplify theme selection, GTK settings can also be specified directly in configuration files, such as `.gtkrc-2.0` or `.gtkrc-xfce`. However, it's worth noting that desktop environments and individual applications may sometimes override these manual settings.
- **Dark Theme Variants**: Some GTK 3 themes include a dark variant. However, this variant is typically only activated by default when an application explicitly requests it.
- **Widget and Icon Resizing**: For users with smaller screens or those who prefer a more compact interface, GTK allows for easy resizing of icons and other widgets, offering a way to adjust the density of the UI.
- **Targeting Themes with GTK_THEME**: If you wish to apply a specific theme to only certain applications or for testing purposes without changing your global desktop settings, the GTK_THEME environment variable can be utilized.

For a more comprehensive understanding of these aspects and detailed instructions on manual configuration, you may refer to the official [Arch Linux Wiki - GTK](https://wiki.archlinux.org/title/GTK) article.

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

For a more sophisticated example, **Meyza's setup** offers an excellent reference, which you can examine [here](https://github.com/meyzatech/gtk.css-xfce). Similarly, **diws** provides an in-depth customization [guide](https://github.com/diws1/xfce-rice) on this topic. Further details on Xfce panel theming are available in the official [Xfce Docs article](https://docs.xfce.org/xfce/xfce4-panel/theming).

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

Given that Xfce primarily utilizes the **GTK widget toolkit**, applications built with **Qt** are often noticeably inconsistent with a uniformly themed GTK desktop. While I generally recommend favoring GTK-based applications for their seamless integration with Xfce, there are certainly instances where using a specific Qt application becomes a necessity.

Though I have not really delved much into these applications and don't have much to say about it, I suggest checking **Kvantum**. This SVG-based theme engine for Qt offers extensive customization capabilities, allowing for deep visual integration with your desktop. Further details on its setup and usage can be found in its official [installation guide](https://github.com/tsujan/Kvantum/blob/master/Kvantum/INSTALL.md).

## Fine-Tuning the Xfwm4 Compositor

The `xfwm4` window manager also incorporates a built-in compositor responsible for various visual effects on your Xfce desktop. Fine-tuning this compositor allows for precise control over several elements which should contribute significantly to the overall aesthetic and perceived fluidity of the user interface.

Delving into the compositor's settings enables users to:

- **Adjust Opacity**: Control the transparency levels of inactive windows, dialogs, or even the active window, providing a subtle visual distinction and allowing desktop elements beneath to remain partially visible.
- **Refine Shadows**: Precisely configure the appearance of window shadows, including their size, offset, and opacity. This level of detail ensures shadows complement your chosen theme without appearing overly dominant or too subtle.
- **Control Fading and Animations**: Customize the fade-in and fade-out effects for windows when they are opened, closed, or minimized/restored. Adjusting these parameters can create a more pleasing and less abrupt visual transition.

These adjustments are typically accessible through the Xfce "Window Manager Tweaks" settings panel under the "Compositor" tab. Further information about the compositor can be found in the [Arch Wiki - Xfwm](https://wiki.archlinux.org/title/Xfwm) and the [Xfce Docs - wmtweaks](https://docs.xfce.org/xfce/xfwm4/wmtweaks#compositor) article.

## Enhanced Compositing with Picom

> If you would like to configure a gaming-oriented setup or you are experiencing screen tearing in your Xfce desktop, Picom may just be the thing for you.
{: .prompt-tip }

While Xfwm4 includes a functional built-in compositor, users seeking better visual effects or finer control over their desktop's rendering often opt to replace it with an external compositor like [Picom](https://github.com/yshui/picom). It is a standalone compositor for Xorg that offers a significantly expanded feature set and greater flexibility, making it a popular choice for those aiming for a highly customized visual experience.

To integrate Picom with Xfce, the first crucial step is to **disable the built-in Xfwm4 compositor** through the "Window Manager Tweaks" settings panel. Once disabled, Picom can be launched automatically upon session start (e.g., by adding it to Xfce's Autostart applications). Further customization is then performed by editing Picom's configuration file, which you may learn more about in [Arch Wiki - Picom](https://wiki.archlinux.org/title/Picom).

## A Closer Look at Your Fonts

Beyond merely selecting a desired typeface, the visual quality of text on your Xfce desktop is significantly influenced by font rendering configurations. This process dictates how font characters are drawn on the screen, down the finest details.

### Font Hinting

> Font hinting is primarily significant on low resolution displays, and much less so for newer, higher-res ones.
{: .prompt-info }

Hinting is the process of adjusting the display of an outline font to align with the pixel grid, making characters appear sharper, especially at smaller sizes or lower resolutions. XFCE usually offers different hinting styles (e.g., None, Slight, Medium, Full). As you notch it upwards, it will get more aggressive as it forcibly changes the original shapes of the glyphs.

On some setups, LCD hinting may result in better fonts. However, this may not work on all systems. You may learn more about this two concepts in the following resources:

- [Font hinting - Wikipedia](https://en.wikipedia.org/wiki/Font_hinting)
- [Hinting - Fonts Knowledge](https://fonts.google.com/knowledge/glossary/hinting)
- [Xfce4 Settings: Appearance](https://docs.xfce.org/xfce/xfce4-settings/appearance#fonts)

### Font Anti-Aliasing

Anti-aliasing (often abbreviated to AA) is a technique to smooth the jagged edges of graphical elements, making them appear less pixelated and more sharp from afar. This is similarly prevalent in computer video games.

You may read more about anti-aliasing in its [Wikipedia article](https://en.wikipedia.org/wiki/Spatial_anti-aliasing).

### Subpixel Rendering

Subpixel rendering is an advanced font rendering technique designed to enhance text clarity, particularly on LCD displays. Unlike conventional anti-aliasing, which operates at the whole-pixel level, subpixel rendering leverages the individual red, green, and blue subcomponents of each pixel. Therefore, its implications are greatly independent ftom the effects of anti-aliasing.

By strategically illuminating these subpixels, it can effectively increase the horizontal resolution of text, resulting in visibly sharper and smoother character outlines. This method significantly improves the legibility of fonts, especially at smaller sizes, by reducing perceived blurriness and making edges appear more defined.

You may read more about subpixel rendering in [Darel Rex Finley's article](https://alienryderflex.com/sub_pixel/).

### What About It?

Xfce provides you sane defaults in this end (i.e., enabled AA, slight hinting, RGB subpixel rendering) and it is advised to keep them unless you have very specific needs. However, you may like to check on the subpixel rendering configuration whether this matches your monitor's orientation.

Furthermore, these font rendering options do carry performance implications, though their impact can vary in magnitude across different systems. Should you observe performance issues, such as noticeable delays when menus or dialogs appear, the Xfce Wiki recommends disabling all font rendering enhancements.

However, disabling these features will likely result in illegible and visually unappealing fonts. To mitigate this, the Xfce Wiki suggests using [Luxi Sans](https://www.fontsquirrel.com/fonts/luxi-sans). From personal experience, I also recommend `fonts-vlgothic` and `fonts-inter` as viable alternatives.

## Adding Desktop Widgets

If you have used MacOS or Windows before, you may have used widgets of kinds. Maybe you have used Rainmeter too. Or maybe you come from Plasma. Their implementations are neat. How about bringing them to Xfce?

### Conky

![Conky Novoselic](https://raw.githubusercontent.com/addy-dclxvi/conky-theme-collections/master/preview-novoselic.jpg){: width="800" height="450" .normal }

<sup>Addy's Novoselic theme for Conky. Content licensed under GPL-3.0.</sup>

[Conky](https://github.com/brndnmtthws/conky) is a highly configurable system monitor that draws information directly onto the desktop background, often appearing as an overlay without a traditional window frame. Its strength lies in its extensive customization capabilities as it allows users to define exactly what information is displayed, its formatting, and its precise placement, enabling seamless integration with bespoke desktop themes.

To use it on your desktop, you may refer to their [Wiki](https://github.com/brndnmtthws/conky/wiki) for setup instructions. Alternatively, you can manage all things related to Conky with [Conky Manager](https://launchpad.net/~tomtomtom/+archive/ubuntu/conky-manager). For a comprehensive example, **Addy's collection** offers an excellent reference, which you can examine [here](https://github.com/addy-dclxvi/conky-theme-collection).

### ElKowars Wacky Widgets

![Eww Dashboard](https://raw.githubusercontent.com/adi1090x/widgets/refs/heads/main/previews/dashboard.png){: width="800" height="450" .normal }

<sup>Aditya's Dashboard widgets for eww. Content licensed under GPL-3.0.</sup>

[ElKowars Wacky Widgets](https://github.com/elkowar/eww) (often abbreviated to eww) focuses on providing a collection of modular, often uniquely styled widgets. These widgets can display various pieces of information or provide quick access to functions, and are designed with a strong emphasis on visual distinctiveness and user-defined customization.

For more details about Eww, you may refer to their documentation [here](https://elkowar.github.io/eww/).

## Justice For All

![Justice For All Xfce](https://raw.githubusercontent.com/addy-dclxvi/conky-theme-collections/master/preview-sidepanes.jpg){: width="800" height="450" .normal }

<sup>A preview of Addy's Justice For All. Content licensed under GPL-3.0.</sup>

In this section, I would like to feature and appreciate [Addy's Justice For All](https://www.reddit.com/r/unixporn/comments/85a436/xfce_on_gnulinux_both_terminal_gui_deserve/). It features a clean, pastel-themed Xfce desktop, complemented by Addy's [Sidepanes](https://github.com/addy-dclxvi/conky-theme-collections/tree/master/sidepanes), [Circela](https://github.com/addy-dclxvi/xfwm4-theme-collections/tree/master/Circela/xfwm4), [Fantome](https://github.com/addy-dclxvi/gtk-theme-collections/tree/master/Fantome), and [Launchy](https://github.com/addy-dclxvi/tint2-theme-collections/tree/master/launchy).

## Sweet Starlit Serenade

![Serenade Xfce](https://raw.githubusercontent.com/mehedirm6244/Miserable_Xfce/refs/heads/Serenade/data/slide.gif){: width="800" height="450" .normal }

<sup>A preview of Mehedirm's Serenade. Panel by EWW, app launcher by Findex.</sup>

In this section, I would like to feature and appreciate [Mehedirm's Serenade](https://github.com/mehedirm6244/Miserable_Xfce/tree/Serenade). It features a well-rounded, consistent Xfce desktop, largely complemented by Lavanda Tokyonight, Picom, and EWW.

---

[View page source](https://github.com/keiaa-75/xfce-notes/blob/main/_posts/2025-05-23-beyond-the-defaults.markdown)
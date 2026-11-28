# Glass

The frosted glass material and where it is used. Part of
[the visual design](README.md).

Status: started. The material, where it is used and what is behind it are
set. What each toolkit can draw is still to be researched.

## Design

- **Frosted glass is the design language.** Surfaces look like frosted
  glass: what is behind them shows through, blurred and softened.
- **Apple's Liquid Glass is the main inspiration,** as seen in the
  current versions of iOS and macOS. The look is clean and light.
- **It is the same in every client,** including on Linux, Android and the
  web, where the platform does not provide the material and we draw it
  ourselves.
- **It has a light and a dark form.**
- **The glass is thin and clear, with a bright edge.** What is behind a
  surface is blurred and its colour shows through strongly. A thin light
  edge and a soft shadow lift the surface. There is no bent light at the
  edges and there are no moving highlights. This is "More glass" on
  [the material board](examples/material-board.html).
- **Our own backdrop is strong in colour,** so that the glass has
  something to show.
- **Our own backdrop moves.** Its fields of colour drift slowly, and it
  reacts to the assistant, such as while it listens or speaks. With
  reduced motion it is still or only drifts. See [motion](motion.md).
- **In dark the backdrop is calmer.** Its colour is about half as strong
  as in light, on a darker base, so that secondary text on thin glass
  stays readable. This is "Calmer dark backdrop" on
  [the dark text board](examples/dark-text-board.html).
- **The desktop launcher is clear glass:** about half see-through, so the
  desktop behind it is clearly there. This is "Clear glass" on
  [the launcher board](examples/launcher-board.html).
- **The glass itself is neutral.** It has no colour of its own. Colour
  comes from what is behind it and from the
  [accent](colour.md).
- **Glass is for what floats above the content:** bars, the launcher,
  sheets, menus, cards and controls. The content itself, such as a long
  list, a log or a page of text, is plain: it has no blur and lets only a
  little of the backdrop's colour through. This keeps text readable and
  keeps long lists fast.
- **Text on glass is kept readable without thickening the glass.**
  Secondary text is firmer than on a plain surface. A coloured word, such
  as a status or a link in the accent, never sits straight on glass: it
  sits in a small solid chip. The backdrop of the Graphite accent is
  drawn from its grey, not from its near black or near white. This is
  "Thin glass, firmer text" on
  [the readability board](examples/readability-board.html).
- **A device that is too slow for the blur shows a simpler form:** a flat
  translucent tint in the same colour and shape, without the blur. It is
  the same look with less effect, not another theme.
- **The device's accessibility settings are followed.** With reduced
  transparency or increased contrast set on the device, glass becomes
  solid.
- **The low-power screen of a tablet has no glass.** It is black, with
  dim content on it. See
  [phone and tablet app](../technical/clients/mobile.md).

## What is behind the glass

Glass only looks like glass when there is something behind it. A glass
panel over a plain white page looks like a plain white panel.

| Where | What is behind the glass |
|---|---|
| The desktop launcher | Whatever is behind its window: the person's desktop and open applications, blurred. Where a desktop cannot provide this, our own backdrop |
| A household tablet | A wallpaper, such as a family photo, shown in full while no assistant is active. When an assistant is active, our own backdrop takes its place as the stage for the character. See [assistant visuals](assistant-visuals.md) |
| Everywhere else | Our own backdrop: a soft field of colour that takes the [accent](colour.md), the same on every device |

## What it costs

Blurring what is behind a surface is work for the device, on every frame
in which that content moves. Three places are at risk:

- The desktop client must appear within 100 ms and stay fast over long
  lists. See [desktop](../technical/clients/desktop.md).
- A household tablet is second-hand and may be old. See
  [phone and tablet app](../technical/clients/mobile.md).
- The voice page runs in the browser of a tablet too old for the app. See
  [voice page](../technical/clients/web-voice.md).

A client that cannot afford the blur shows the simpler form of the
material.

## Verified and assumed

Verified on 28 November 2026, by calculation from the token values, over
the strongest part of our own backdrop for every accent:

- With "Thin glass, firmer text", main text on glass has a contrast of at
  least 8.6 to 1 in light and 4.7 in dark. Coloured words in solid chips
  have at least 5.0 in light and 5.4 in dark.
- Secondary text on glass has at least 5.8 in light. In dark it has at
  least 7.0 with the calmer backdrop; it was 3.8 before.
- In the launcher over a desktop that is not ours, main text falls to
  2.6 in dark over a white window, and to 4.6 in light over a black one.

Verified on 28 November 2026, from the toolkits' own documentation:

- Slint draws a blur behind a rectangle from version 1.19, with two of
  its renderers only. It blurs and does not raise the colour.
- Jetpack Compose draws it with the Haze library, under the Apache 2.0
  licence, on Android 12 and later. On Android 11 and earlier the library
  draws a flat tint in its place.
- CSS draws it with `backdrop-filter`.
- A window can ask for the desktop behind it to be blurred on Wayland
  through the `ext-background-effect-v1` protocol, which KDE, GNOME,
  Hyprland, COSMIC and niri support, and Sway does not. Slint's window
  library does not use this protocol yet.
- On Windows 11 and macOS the `window-vibrancy` library, under the MIT
  and Apache 2.0 licences, asks the system for the effect.

Assumed:

- SwiftUI draws the material with its own materials.
- The blur is fast enough on an old tablet and within the 100 ms of the
  launcher. Nobody has measured this.
- X11 can blur behind a window only under KDE.

## Open questions

- Who sets the wallpaper of a household tablet: an admin, in the admin
  panel? Is it one picture, or several that change?
- Can a wallpaper also be set on a personal phone, in the settings window
  of the desktop client, or in the admin panel, or do those always show
  our own backdrop?
- How does the backdrop react to the assistant: does it follow the sound
  of the voice, or change with the state, such as listening and
  speaking?
- With reduced motion, is the backdrop still, or does it drift slowly?
- Does the backdrop also move on an old tablet and in low-power mode?
- Can a person set how see-through the glass is? The owner named this as
  a possibility.
- The launcher shows the real desktop, which can be any colour. Does the
  launcher's glass become thicker by itself when what is behind it is
  very bright or very dark, so that its text stays readable?
- From the research: on Linux the launcher asks for the blurred desktop
  through the new Wayland protocol with a small piece of our own code,
  and shows our own backdrop wherever the desktop cannot blur, such as
  under Sway and on most of X11. Agree?
- From the research: an Android tablet on Android 11 or earlier shows the
  flat tint, not the blur. Agree?

To research:

- How fast the blur is on an old tablet and in the launcher, measured on
  real devices.

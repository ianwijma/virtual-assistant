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
- **The strength is a clear blur with a bright edge.** What is behind a
  surface is blurred and its colour shows through. A thin light edge and
  a soft shadow lift the surface. There is no bent light at the edges and
  there are no moving highlights. This is "Glass" on
  [the direction board](examples/direction-board.html), between "Frost"
  and "Liquid".
- **The glass itself is neutral.** It has no colour of its own. Colour
  comes from what is behind it and from the
  [accent](colour.md).
- **Glass is for what floats above the content:** bars, the launcher,
  sheets, menus, cards and controls. The content itself, such as a long
  list, a log or a page of text, is plain. This keeps text readable and
  keeps long lists fast.
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
| A household tablet | A wallpaper, such as a family photo. It is shown in full while no assistant is active. When an assistant is active, the glass surfaces appear over it |
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

Assumed, needing research to confirm:

- Slint, Jetpack Compose, SwiftUI and CSS can each draw a blurred,
  translucent surface fast enough for the clients above.
- A launcher window on Linux can show the blurred desktop behind it on
  both X11 and Wayland.

## Open questions

- Who sets the wallpaper of a household tablet: an admin, in the admin
  panel? Is it one picture, or several that change?
- Can a wallpaper also be set on a personal phone, in the settings window
  of the desktop client, or in the admin panel, or do those always show
  our own backdrop?
- Does our own backdrop move slowly, or is it still?
- How see-through is the desktop launcher? Several strengths are on
  [the launcher board](examples/launcher-board.html).
- Can a person set how see-through the glass is? The owner named this as
  a possibility.
- Which of the designs on
  [the material board](examples/material-board.html) is the look: as
  first drawn, more glass, calmer, or closer to Apple's?

To research:

- What Slint, Jetpack Compose on older Android, SwiftUI and CSS can each
  draw: blur behind a surface, and at what speed.
- Whether the launcher window can show the blurred desktop behind it on
  Linux, on X11 and on Wayland.

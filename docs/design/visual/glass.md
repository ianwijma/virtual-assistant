# Glass

The frosted glass material and where it is used. Part of
[the visual design](README.md).

Status: started. The direction and where glass is used are set. How
strong the effect is, and what is behind it, are open.

## Design

- **Frosted glass is the design language.** Surfaces look like frosted
  glass: what is behind them shows through, blurred and softened.
- **Apple's Liquid Glass is the main inspiration,** as seen in the
  current versions of iOS and macOS. The look is clean and light.
- **It is the same in every client,** including on Linux, Android and the
  web, where the platform does not provide the material and we draw it
  ourselves.
- **It has a light and a dark form.**
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

## What glass needs

Glass only looks like glass when there is something behind it. A glass
panel over a plain white page looks like a plain white panel. So the
material comes with a second choice: what is behind it. The candidates
are in the questions below and on
[the direction board](examples/direction-board.html).

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

- How far does the glass go: a plain frosted blur, or the full effect
  with bent light at the edges and moving highlights? The full effect is
  the most recognisable as Apple's, and the most work to draw outside
  Apple's devices. The direction board shows three strengths.
- What is behind the glass: our own soft colour backdrop, a wallpaper
  the person chooses, the colour of the active assistant, or the real
  desktop behind the launcher? These can differ per client.
- May a person choose the backdrop? A theme cannot be chosen; is a
  wallpaper a theme?
- Is the glass clear and neutral, or does it carry a tint of the accent
  colour?

To research:

- What Slint, Jetpack Compose on older Android, SwiftUI and CSS can each
  draw: blur behind a surface, bent light, and at what speed.
- Whether the launcher window can show the blurred desktop behind it on
  Linux, on X11 and on Wayland.

# Glass

The frosted glass material and where it is used. Part of
[the visual design](README.md).

Status: the direction is set. How far it goes is open.

## Design

- **Frosted glass is the design language.** Surfaces look like frosted
  glass: what is behind them shows through, blurred and softened.
- **Apple's Liquid Glass is the main inspiration,** as seen in the
  current versions of iOS and macOS. The look is clean and light.
- **It is the same in every client,** including on Linux, Android and the
  web, where the platform does not provide the material and we draw it
  ourselves.
- **It has a light and a dark form.**

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

A client that cannot afford the blur needs a simpler form of the same
material. Whether that is acceptable is a question below.

## Verified and assumed

Assumed, needing research to confirm:

- Slint, Jetpack Compose, SwiftUI and CSS can each draw a blurred,
  translucent surface fast enough for the clients above.
- A launcher window on Linux can show the blurred desktop behind it on
  both X11 and Wayland.

## Open questions

- Where is glass used: on every surface, or only on what floats above
  the content, such as bars, the launcher, sheets and cards? Apple uses
  it only for the floating layer and keeps the content itself plain.
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
- May a device that is too slow for the blur show a simpler material,
  such as a flat translucent tint? This would be the same look in
  colour and shape, without the blur.
- Does the look follow the device's settings for reduced transparency
  and increased contrast, by making the glass more solid?
- What does glass look like on the black, dimmed screen of a tablet in
  low-power mode?

To research:

- What Slint, Jetpack Compose on older Android, SwiftUI and CSS can each
  draw: blur behind a surface, bent light, and at what speed.
- Whether the launcher window can show the blurred desktop behind it on
  Linux, on X11 and on Wayland.

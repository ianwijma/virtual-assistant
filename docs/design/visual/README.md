# Visual design

How the system looks and feels. The vision and principles are in
[the overarching design](../README.md).

Status: started. The high-level choices are made. The design language is
being written.

## What is being designed

One look for every screen the system has:

| Screen | Where it runs | What it must suit |
|---|---|---|
| [Desktop client](../technical/clients/desktop.md) | A launcher over the desktop, and a settings window | Speed, keyboard use, long lists |
| [Phone app](../technical/clients/mobile.md), personal | A person's phone | Touch, notifications, a quick talk to an assistant |
| [Phone app](../technical/clients/mobile.md), household | A tablet in a room, in kiosk mode | Reading from across a room, anyone using it, guests included |
| [Admin panel](../technical/clients/web-admin.md) | A browser | Many settings, logs and timelines |
| [Voice page](../technical/clients/web-voice.md) | A browser, often an old tablet | An assistant's character and a chat |
| [Described screens](../technical/a2ui.md) | Inside every client | Screens that an assistant composes |

## Decided

- **One look everywhere.** The experience is the same across the desktop
  client, the phone and tablet app, the admin panel and the voice page,
  and in any screen added later.
- **Recognisable as ours.** The design is distinctive, so that anyone can
  tell it is this product.
- **Frosted glass is the design language.** Apple's Liquid Glass is the
  main inspiration. See [glass](glass.md).
- **One set of design tokens** is the single source: colour, type, spacing,
  motion and assistant visuals. The theme for each platform is generated
  from it (Slint, SwiftUI, Jetpack Compose and CSS).
- **Described screens follow it too.** [A2UI](../technical/a2ui.md)
  catalog components use the same tokens.
- **Assistants have a visual.** Each assistant is a character with its own
  look. See [assistants](../technical/voice/assistants.md).
- **The product name** is chosen together with this work. "Virtual
  Assistant" is a working title.

## A fresh start

The identity starts fresh. Nothing visual is reused from the earlier voice
assistant: not its characters, not its colours, not its surfaces.

## Our own look, everywhere

Every client has our own look. No client imitates the look of the desktop
or the phone it runs on, and there is no theme that does. This replaces
the desktop brief's request to mimic the host desktop by default.

This holds on Apple's devices too. The look is inspired by Apple's, but it
is our own, and it is the same on Linux, Android and the web.

## Light and dark, and no themes

- There is one look, in a light and a dark form. Each client follows the
  light or dark setting of the device it runs on.
- A person cannot choose a theme.

## The order of the work

1. **The high level:** the feel, the glass, and the colours. This is
   done; the candidates were on
   [the direction board](examples/direction-board.html).
2. **The design language:** colour, type, shape, spacing and motion,
   written as [tokens](tokens.md). A first set exists.
3. **Example components:** a few components that show the language in
   use. See [components](components.md).
4. **Low-fidelity mockups** of each client. They show layout and content,
   not polish, so that an agent can combine them with the design language.
   A first set exists, as proposals. See [mockups](mockups/README.md).

## Map of the documents

| Document | Covers | Status |
|---|---|---|
| [identity.md](identity.md) | The name, the feel, and what makes it recognisable | Started |
| [glass.md](glass.md) | The frosted glass material and where it is used | Started |
| [colour.md](colour.md) | The colours, in light and dark | Started |
| [typography.md](typography.md) | The typeface and the type scale | Started |
| [shape-and-spacing.md](shape-and-spacing.md) | Corners, density, spacing and icons | Started |
| [motion.md](motion.md) | How things move, and sound | Started |
| [assistant-visuals.md](assistant-visuals.md) | How an assistant appears and reacts to speech | Started |
| [tokens.md](tokens.md) | The full set of tokens | A first set |
| [components.md](components.md) | The shared components and how they behave | Started |
| [mockups/](mockups/README.md) | The low-fidelity mockups of each client | A first set, as proposals |
| [examples/](examples/) | Pages to open in a browser: the [direction board](examples/direction-board.html), the [typeface board](examples/typeface-board.html) and the [example components](examples/components.html), with the tokens as CSS | |

Planned, each made when work on it starts:

| Document | Covers |
|---|---|
| One file per client | How the look applies to the desktop, phone, tablet, admin panel and voice page, once its mockup is agreed |

## Open questions

Each subject's questions are in its own document. The questions below are
about the clients, whose documents are not started yet.

- What does a tablet in a room show when nobody is using it: the
  character, a clock, running timers, or nothing?
- Does the admin panel use glass as much as the other clients, or is it
  plainer because it holds dense tables and logs?
- Should a screen that an assistant composed look different from a
  built-in screen, so that a person can tell?
- Which client's mockup is worked out in detail first, and which screens
  of it matter most?
- Which devices are the references for the mockups: which phone, which
  tablet, which monitor size?
- Are settings screens generated from each feature's description, so
  that one definition serves the phone app, the desktop client and the
  admin panel? A2UI makes this possible, but one solution may not suit
  every device. This is decided once there are visual designs of the app
  and the admin panel.

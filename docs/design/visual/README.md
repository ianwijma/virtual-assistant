# Visual design

How the system looks and feels. The vision and principles are in
[the overarching design](../README.md).

Status: not started. This folder holds what is decided about the visual
design so far. The design itself is still to be made, and it affects every
screen, so it is worked on early.

## Decided

- **One look everywhere.** The experience is the same across the desktop
  client, the phone and tablet app, the admin panel and the voice page.
- **Recognisable as ours.** The design is distinctive, so that anyone can
  tell it is this product.
- **One set of design tokens** is the single source: colour, type, spacing,
  motion and assistant visuals. The theme for each platform is generated
  from it (Slint, SwiftUI, Jetpack Compose and CSS).
- **Described screens follow it too.** [A2UI](../technical/a2ui.md)
  catalog components use the same tokens.
- **Assistants have a visual.** Each assistant is a character with its own
  look. See [assistants](../technical/voice/assistants.md).
- **The product name** is chosen together with this work. "Virtual
  Assistant" is a working title.

## Planned documents

Each of these becomes its own file in this folder when work on it starts:

| Document | Covers |
|---|---|
| `identity.md` | The name, the feel, and what makes it recognisable |
| `tokens.md` | Colour, type, spacing and motion |
| `components.md` | The shared components and how they behave |
| `assistant-visuals.md` | How an assistant appears and reacts to speech |
| One file per client | How the look applies to the desktop, phone, admin panel and voice page |

## A fresh start

The identity starts fresh. Nothing visual is reused from the earlier voice
assistant: not its characters, not its colours, not its surfaces.

## Our own look, everywhere

Every client has our own look. No client imitates the look of the desktop
or the phone it runs on, and there is no theme that does. This replaces
the desktop brief's request to mimic the host desktop by default.

## Light and dark, and no themes

- There is one look, in a light and a dark form. Each client follows the
  light or dark setting of the device it runs on.
- A person cannot choose a theme.

## Open questions

- Are settings screens generated from each feature's description, so
  that one definition serves the phone app, the desktop client and the
  admin panel? A2UI makes this possible, but one solution may not suit
  every device. This is decided once there are visual designs of the app
  and the admin panel.
- Three or four words for how it should feel, and products whose look you
  admire.

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

## What exists to draw on

The earlier voice assistant has a look that can be reused or replaced:

- a "quiet instrument" idea: warm, near-black surfaces;
- a colour language where amber is the assistant and mint is the person;
- 19 animated characters driven by the audio.

See [the reference](../../reference/existing-voice-assistant.md).

## Open questions

- Three or four words for how it should feel, and products whose look you
  admire.
- Does our own identity replace "mimic the host desktop" as the default
  look? The desktop brief asked for mimicry by default; the later decision
  for one recognisable look points the other way. If so, mimicry could
  remain as an optional theme.
- Do the existing characters and the amber and mint colour language carry
  over, or does the identity start fresh?
- Can a person choose a different theme, and how far may it differ?
- Light and dark: both, and which is the default?

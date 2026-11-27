# Visual design

How the system looks and feels. The vision and principles are in
[the overarching design](../README.md).

Status: started. The direction is set and the high-level choices are open.
No colour, typeface or component is chosen yet.

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

1. **The high level:** the feel, the glass, and the colours. This is the
   current step. The owner chooses from
   [the direction board](examples/direction-board.html).
2. **The design language:** colour, type, shape, spacing and motion,
   written as tokens.
3. **Example components:** a few components that show the language in use.
4. **Low-fidelity mockups** of each client. They show layout and content,
   not polish, so that an agent can combine them with the design language.

## Map of the documents

| Document | Covers | Status |
|---|---|---|
| [identity.md](identity.md) | The name, the feel, and what makes it recognisable | Questions only |
| [glass.md](glass.md) | The frosted glass material and where it is used | Direction set |
| [colour.md](colour.md) | The colours, in light and dark | Candidates to choose from |
| [examples/](examples/direction-board.html) | Pages to open in a browser that show the candidates | First board |

Planned, each made when work on it starts:

| Document | Covers |
|---|---|
| `typography.md` | The typefaces and the type scale |
| `shape-and-spacing.md` | Corners, borders, depth, spacing and icons |
| `motion.md` | How things move, and sound |
| `tokens.md` | The full set of tokens and how each platform's theme is generated |
| `components.md` | The shared components and how they behave |
| `assistant-visuals.md` | How an assistant appears and reacts to speech |
| One file per client | How the look applies to the desktop, phone, tablet, admin panel and voice page |
| `mockups/` | The low-fidelity mockups of each client |

## Open questions

Questions about the feel, the glass and the colours are in
[identity](identity.md), [glass](glass.md) and [colour](colour.md). The
questions below belong to documents that are not started yet.

Typography:

- Is one typeface shipped with every client, so that text looks the same
  everywhere? The other choice is each platform's own font, which is
  lighter but looks different per device. Apple's San Francisco cannot be
  used outside Apple's devices.
- Which character should the typeface have: neutral (such as Inter or
  Geist), geometric and friendly (such as Manrope or Figtree), or rounded
  (such as Nunito)? Every candidate must have a licence that allows sold
  hardware.
- Do headings get their own typeface, or is one family used for
  everything?
- Which languages and scripts must the typeface cover later?
- Does text follow the text size set on the device?

Shape, spacing and icons:

- How round are corners: slightly (about 8 to 12), clearly (about 16 to
  24), or pill-shaped controls as in Apple's design? The direction board
  shows the three.
- Is there one density, or a compact one for the desktop and the admin
  panel and a roomy one for touch and for the tablet across a room?
- Are icons outlined or filled, and is an open icon set used (such as
  Lucide, Phosphor or Tabler) or do we draw our own? Apple's symbols
  cannot be used.
- Is there an illustration style, for empty screens and first-run setup?

Motion and sound:

- How much does the interface move: fluid and springy as in Apple's
  design, or quick and plain? The desktop must appear within 100 ms, so
  does the launcher appear with no animation at all?
- Are sounds part of the identity, such as a tone when an assistant
  starts listening or a timer ends?
- Does the phone use vibration as part of the feel?

Assistant visuals:

- What is a character: an abstract shape such as an orb or a wave, a
  simple face, or a full illustrated figure? The
  [reply tags](../technical/voice/reply-tags.md) include a wink, an eye
  roll, a nod and a shake of the head, which need eyes and a head.
- How do two assistants differ: by colour only, by shape, or as fully
  different characters?
- How does a person give their own assistant a look: by choosing from a
  set, by adjusting parts such as colour and eyes, or by supplying an
  image?
- How playful is the default household assistant: cute, friendly, or
  calm and abstract?
- Which states must a character show? The proposal is idle, listening,
  thinking, speaking, muted, waiting for the server, and voice not
  recognised.
- How large is the character on each screen: the whole screen on the
  tablet, a small part of the launcher on the desktop?

The clients:

- What does a tablet in a room show when nobody is using it: the
  character, a clock, running timers, or nothing?
- Does the admin panel use glass as much as the other clients, or is it
  plainer because it holds dense tables and logs?
- Should a screen that an assistant composed look different from a
  built-in screen, so that a person can tell?
- Which client is drawn first as a mockup, and which screens of it matter
  most?
- Which devices are the references for the mockups: which phone, which
  tablet, which monitor size?
- Are settings screens generated from each feature's description, so
  that one definition serves the phone app, the desktop client and the
  admin panel? A2UI makes this possible, but one solution may not suit
  every device. This is decided once there are visual designs of the app
  and the admin panel.

To research:

- How each character is animated so that it runs in Slint, Jetpack
  Compose, SwiftUI and a browser from one source.

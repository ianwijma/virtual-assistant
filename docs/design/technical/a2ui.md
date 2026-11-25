# A2UI

How screens are described and sent to devices. Part of
[the technical design](README.md).

Status: draft.

## What it is for

A2UI (<https://a2ui.org/>) lets an agent, or our own code, describe a
screen that a device then draws with its native components. It is a core
part of the system, for two purposes:

- **Building screens quickly.** New screens and features do not each need
  hand-written UI on every platform.
- **Screens made by AI.** An assistant can create a screen on the fly,
  such as a view that answers a request.

Not everything is a described screen. The cheapest way that does the job
is used.

## Screens and voice

A2UI is part of the assistant on every device that has a screen.

| Device | How an answer is given |
|---|---|
| Has a screen | A described screen, with speech as well if voice is on |
| No screen, voice on | Spoken |

Every described screen therefore carries a spoken form of its content, so
the same answer works on both kinds of device.

A device with no screen and no voice cannot be interacted with, so an
assistant never answers on one.

The server knows what each device can do from its recorded
[capabilities](server/protocol.md), including whether it can draw A2UI.
These are given to the AI model with a request, so the model answers in a
form the device can present.

## Three tiers

| Tier | What is sent | Example |
|---|---|---|
| 1. Command | A plain protocol message; the device uses its own native screen | "Play this URL" opens the native video player |
| 2. Catalog component | The name of a component built natively once per platform | A timer card, a list, a media player |
| 3. Generated surface | A screen an agent composes from catalog components | A one-off view that answers a request |

- A common screen, such as a video player, is a command or a catalog
  component, so that its description is not sent every time.
- A generated surface is kept by the server as a template. Next time only
  the new data is sent.
- We add our own catalog on top of A2UI's basic one. The catalog belongs
  to the system, not to [modules](modules/README.md).
- Catalog components use the [design tokens](../visual/README.md), so a
  generated screen matches the rest.

## Renderers

| Platform | Renderer |
|---|---|
| Android | The official Jetpack Compose renderer |
| iOS | The official SwiftUI renderer |
| Desktop | A Rust renderer for Slint, which we expect to write or contribute to |

The Rust renderer is the likely first library we contribute to or create.
It is kept separate from the application so that others can use it.

## Requirements from the desktop brief

- Screens we define ourselves must still meet the desktop's speed and
  scale targets, including lists of hundreds of thousands of items.
- A generated screen may take longer to arrive, but must draw smoothly
  once it does.
- Actions inside a described screen must work with the keyboard shortcut
  system.

## Verified and assumed

Verified on 25 November 2026:

- A2UI's basic catalog includes `Video` and `AudioPlayer`.
- Official SwiftUI and Compose renderers exist.

Assumed, needing a build to confirm:

- Surface templates can be kept and reused with new data.

## Who words the spoken form

It depends on the content:

- **A fixed sentence comes from the system feature,** with no AI model
  involved, such as "Ian, you have a notification". The audio of a
  sentence that does not change can be kept and reused. See
  [text to speech](voice/text-to-speech.md).
- **The AI model words it** when the content is raw data that has to be
  turned into a sentence, when it needs the assistant's character, such
  as a joke, or when a conversation may follow.

## Hand-built and described screens

- **The core of a client is hand-built:** whatever must be instant and
  must work without the server. That is the launcher, the clipboard, the
  notification centre, window control and sign-in.
- **Feature screens are described with A2UI:** lists, timers, settings
  pages and the like, and everything an assistant shows. A new feature
  then needs no new release of each client.
- A generated screen lives in the conversation it was made in. Saving one
  for reuse is not in the first release.

## Open questions

- What a generated surface may do when its content came from an untrusted
  source, such as an email.
- Whether any Rust implementation of A2UI exists, and whether the A2UI
  project would accept or list one.
- Whether A2UI suits screens our own code defines locally, and what it
  costs in latency.
- How each AI provider produces A2UI, including through a command-line
  tool.
- The contents of our catalog.

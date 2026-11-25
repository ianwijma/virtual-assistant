# Assistants

The assistant as a character. Part of [the voice design](README.md).

Status: draft.

## Design

An assistant is an entity on the server, and it is the same on every
device. A household can have several, each a distinct character.

| Part | What it holds |
|---|---|
| Identity | Name, wake word, voice, visual and personality |
| Brain | The [AI provider](../server/ai-providers.md) that answers |
| Abilities | The [modules](../modules/README.md) it has. A module is a set of tools, and the same module can be given to several assistants |
| Scope | The whole household, or one person |

- An assistant always acts with the permissions of the person it is
  talking to. See [summoning](summoning.md).
- An unrecognised voice gets guest abilities only.
- On a device with a screen, an assistant can answer with a screen. On a
  device without one, it answers by voice. See [A2UI](../a2ui.md).
- The visual side of an assistant belongs to
  [the visual design](../../visual/README.md).

## What is taken from the earlier voice assistant

The character idea is kept: an assistant with a personality, a voice and a
look. Its rules for when an assistant answers are not kept. They are
designed fresh in [summoning](summoning.md).

## Open questions

- Does a wake word belong to an assistant everywhere, or can a device
  choose which assistants it listens for?
- Is there always a household assistant, and can each person also have
  personal ones?
- Does a personal assistant follow its person to a household device once
  their voice is recognised?
- Does each person have a private memory with an assistant?
- Can an assistant act on a device other than the one spoken to, such as
  "show it on my desktop" or "send this to my partner's phone"? Must the
  other person accept?

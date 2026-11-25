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

- **Assistants are assigned to devices:** to chosen devices, or to all of
  them. A device answers only for the assistants assigned to it.
- **People can create their own assistants,** and configure them as they
  like.
- **An assistant can act on another device,** such as "show it on my
  desktop" or "send this to my partner's phone". The other person does not
  have to accept for now; that can be added later.
- An assistant always acts with the permissions of the person it is
  talking to. See [summoning](summoning.md).
- An unrecognised voice gets guest abilities only. What those are is
  configurable. See
  [identity and sharing](../server/identity-and-sharing.md).
- An assistant acting for a person can read what others have shared with
  that person.
- On a device with a screen, an assistant can answer with a screen. On a
  device without one, it answers by voice. See [A2UI](../a2ui.md).
- The visual side of an assistant belongs to
  [the visual design](../../visual/README.md).

## What is taken from the earlier voice assistant

The character idea is kept: an assistant with a personality, a voice and a
look. Its rules for when an assistant answers are not kept. They are
designed fresh in [summoning](summoning.md).

## Open questions

- Is there always a household assistant?
- Does each person have a private memory with an assistant?
- Who may assign an assistant to a device: can a person put their own
  assistant on a household device, or only an admin?
- Which devices an assistant may act on: only the speaker's own, or any
  device in the household?

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

- **There is a default household assistant.** First-run setup creates
  it. It is used by everyone and on every device, personal devices
  included, until someone customises it or makes their own. It is a
  starting point, with a set of modules already switched on.
- **Assistants are assigned to devices:** to chosen devices, or to all of
  them. A device answers only for the assistants assigned to it.
- **Only an admin assigns an assistant to a household device.** A person
  puts their own assistant on their own devices.
- **An assistant does not follow its person.** A personal assistant is on
  a household device only if it is assigned there. Nobody is tracked
  through the home.
- **People can create their own assistants,** and configure them as they
  like.
- **An assistant can act on another device,** such as "show it on my
  desktop" or "send this to my partner's phone". It may act on the
  speaker's own devices, on household devices and on other people's
  devices. The other person does not have to accept for now; that can be
  added later.
- **A conversation is remembered for a short time only.** A person can
  carry on a conversation for a little while. After a short pause, of a
  minute or a few, the assistant starts fresh. There is no memory across
  conversations for now. This is kept simple on purpose and will be
  reworked, so it must stay easy to change.
- **Remembering on request is a tool, not conversation memory.** "Remember
  this for me" would be handled by a lists module, which keeps lists and
  notes a person asks for.
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

- The default assistant: can it be removed, and does it start with every
  module switched on or only a few?
- How long a pause ends a conversation.

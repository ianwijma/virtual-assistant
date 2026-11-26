# Reply tags

The metadata an AI model can put inside its reply, next to the words to be
spoken. Part of [the voice design](README.md).

Status: draft.

## Design

- **A reply is words plus tags.** Besides the text to speak, the model can
  place tags anywhere in its reply: between sentences, or at the end.
- **A tag tells the system to do something,** not to say something.
  Examples:
  - an expression or a movement of the assistant's character, such as
    rolling its eyes, or laughing after a joke;
  - "keep listening", when the model expects the person to answer.
- **The model is told which tags exist,** so it can use them.
- **Tags are never spoken and never shown.** They are removed before the
  text goes to [text to speech](text-to-speech.md), and from an answer
  that is shown as text.
- **Character tags depend on the device.** Whether a device shows the
  assistant's character is one of its
  [capabilities](../server/protocol.md). When it does not, as on a
  voice-only device or in a plain chat, the model is not told about the
  character tags. If it sends one anyway, the tag is removed.
- **A tag takes effect where it stands.** An expression placed in the
  middle of a reply happens when the speech reaches that point, so the
  character's movement lines up with what it says.

## Follow-up without the wake word

A person can answer without the wake word only when the reply carried the
"keep listening" tag. The device then stays awake and listens for the
answer for a few seconds. Anyone may give that answer, not only the
person who started. It is handled with the permissions of the person who
started the conversation, whoever gives it. This is the explicit follow-up state of
[summoning](summoning.md): it is entered for a stated reason and has a
visible end.

## Settings

The timings and thresholds of this part are settings of an assistant,
with defaults. See [assistants](assistants.md).

## After a spoken notification

When a household device speaks a notification, it listens for a moment
for a follow-up about it, without the wake word, in the same way as after
a "keep listening" tag.

## Open questions

- The list of tags, and how they are written in a reply.
- How a tag is lined up with the moment in the speech where it stands.
  This is research still to do.

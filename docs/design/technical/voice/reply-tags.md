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
started the conversation, whoever gives it. This is the explicit
follow-up state of [summoning](summoning.md): it is entered for a stated reason and has a
visible end.

## Settings

The timings and thresholds of this part are settings of an assistant,
with defaults. See [assistants](assistants.md).

## After a spoken notification

When a household device speaks a notification, it listens for a moment
for a follow-up about it, without the wake word, in the same way as after
a "keep listening" tag.

## How tags are written, and the first list

A tag is written in double square brackets, such as `[[laugh]]`. A tag
with a value has a colon, such as `[[pause:500]]`. This form does not occur
in normal speech and is easy to cut out of text that is still arriving.

| Tag | What it does | Offered when |
|---|---|---|
| `[[listen]]` | Keep listening for an answer | Always |
| `[[end]]` | End the conversation and stop listening, such as after the person says goodbye. The next request starts fresh | Always |
| `[[pause:ms]]` | A silence of that length | The device speaks |
| `[[smile]]`, `[[laugh]]`, `[[think]]`, `[[surprised]]`, `[[sad]]`, `[[wink]]`, `[[eye-roll]]`, `[[nod]]`, `[[shake]]` | An expression of the character | The device shows a character |

- A tag the system does not know is removed and logged.
- The list of expressions is settled together with the visual design of
  the characters.
- **Timing:** speech is produced clause by clause. A tag takes effect
  when the clause after it starts to play on the device.

## Open questions

- How a tag is lined up with the moment in the speech where it stands.
  This is research still to do.

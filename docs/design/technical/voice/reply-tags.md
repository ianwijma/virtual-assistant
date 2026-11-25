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
- **Tags are never spoken.** They are removed before the text goes to
  [text to speech](text-to-speech.md).
- **A tag takes effect where it stands.** An expression placed in the
  middle of a reply happens when the speech reaches that point, so the
  character's movement lines up with what it says.

## Follow-up without the wake word

A person can answer without the wake word only when the reply carried the
"keep listening" tag. The device then stays awake and listens for the
answer. This is the explicit follow-up state of
[summoning](summoning.md): it is entered for a stated reason and has a
visible end.

## Open questions

- The list of tags, and how they are written in a reply.
- How a tag is lined up with the moment in the speech where it stands.
  This is research still to do.
- How long a device keeps listening after a "keep listening" tag, and
  whether only the same person's voice may answer.
- Whether tags are also used on a device that only shows text.

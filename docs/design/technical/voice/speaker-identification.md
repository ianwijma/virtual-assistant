# Speaker identification

Working out who is speaking on a household device. Part of
[the voice design](README.md).

Status: draft. Nothing like this exists in the earlier voice assistant.

## Design

- It is the second step of [summoning](summoning.md): after the wake word,
  the utterance is compared with enrolled voices.
- The result decides whose permissions the assistant uses.
- An unknown or uncertain voice is treated as unrecognised. There is no
  "probably this person" level. If recognition is not good enough, it is
  improved; it is kept as a part that can be replaced.
- Once a household device recognises a person, it can give them their own
  information when they ask. It does this only for a request made with the
  wake word, and never unprompted.
- A person's presence is known only at that moment. Nobody is tracked
  through the home.
- **It is a convenience, not security.** A voice can be recorded and
  replayed. It chooses whose calendar to read, but it is never the only
  check on a sensitive action. See
  [identity and sharing](../server/identity-and-sharing.md).
- It is not needed on a personal device, where the owner is known.

The expected technology is voice embeddings with sherpa-onnx, matched
against voices enrolled per person.

## Verified and assumed

Assumed, needing a build to confirm:

- Accuracy in a real home, with several people, background noise and
  children's voices.

## Open questions

- The level of certainty at which a voice counts as recognised.
- How a person enrols their voice, and on which device.
- Where voice data is stored, and how it is removed.

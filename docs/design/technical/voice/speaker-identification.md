# Speaker identification

Working out who is speaking on a household device. Part of
[the voice design](README.md).

Status: draft. Nothing like this exists in the earlier voice assistant.

## Design

- It is the second step of [summoning](summoning.md): after the wake word,
  the utterance is compared with enrolled voices.
- The result decides whose permissions the assistant uses.
- **A person enrols by recording the wake words** of the assistants they
  use. See [wake word](wake-word.md). They can do it on any of their
  devices that has a microphone: the phone app, the desktop client or a
  voice page.
- **Voice data stays on the server.** The recordings and the voiceprint
  made from them are kept there and never leave it. A person can delete
  their own at any time, and they are then no longer recognised.
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

## Settings

The timings and thresholds of this part are settings of an assistant,
with defaults. See [assistants](assistants.md).

## Open questions

None at the moment.

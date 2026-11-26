# Text to speech

Speaking an assistant's answer. Part of [the voice design](README.md).

Status: draft. The starting point is taken from the earlier voice
assistant, where this part works. It is to be confirmed in Rust.

## Design

- Providers are modular and configurable: local voices and cloud ones
  behind one interface, chosen in settings.
- A local voice must be enough for the system to work.
- The first cloud providers are ElevenLabs and Cartesia.
- Each [assistant](assistants.md) has its own voice.
- English first, built so that other languages can be added.
- **Speech is produced on the server only, for now.** Devices play the
  audio the server sends. Producing it on capable devices can be added
  later, and the design must not rule that out.
- **Fixed sentences are kept.** When a system feature speaks a sentence
  whose text does not change, the audio can be made once and reused.
- An answer is always speakable. A device without a screen gets the answer
  by voice. See [A2UI](../a2ui.md).

## Starting point from the earlier voice assistant

**One interface for every provider.** A provider takes a stream of
clauses and returns a stream of audio, each piece marked with the clause
it belongs to.

**Speaking early.** The answer is cut into clauses while the AI model is
still writing, and each clause is sent to the voice at once. Speech starts
before the answer is complete.

**Interruption.** When the person talks over the assistant, speech stops.
The conversation history keeps only the clauses the person actually heard.

**Providers.**

| Provider | Kind | Notes |
|---|---|---|
| Piper, through sherpa-onnx | Local | Many voices, with differing licences |
| Kokoro, through sherpa-onnx | Local | Apache-2.0 |
| Cartesia | Cloud | Optional |
| ElevenLabs | Cloud | Optional |

**Sharing.** Assistants with the same voice share one voice engine.

## Verified and assumed

Verified in the earlier project's code:

- The interface, speaking by clause, and keeping only heard clauses.

Known licence traps, from the earlier project's own notes, which say they
have had no legal review:

- Its default English Piper voice is for non-commercial use only, and so
  is at least one other.
- Several Piper voices are free for commercial use.
- The pronunciation data used by local voices is GPLv3, which fits this
  project but must ship with its sources.

Assumed, needing a build to confirm:

- Local voices are fast enough on a low-power ARM box.

## Open questions

- Which local voices are offered, given quality and licence.

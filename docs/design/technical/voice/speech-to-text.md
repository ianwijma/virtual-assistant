# Speech to text

Turning what a person says into words. Part of
[the voice design](README.md).

Status: draft. The starting point is taken from the earlier voice
assistant, where this part works. It is to be confirmed in Rust.

## Design

- Providers are modular and configurable: local models and cloud ones
  behind one interface, chosen in settings.
- A local model must be enough for the system to work.
- The first cloud provider is Deepgram.
- English first, built so that other languages can be added.
- **It runs on the server only, for now.** Devices send audio to the
  server. Running it on capable devices can be added later, and the design
  must not rule that out.
- Speech to text is not used to detect the wake word. See
  [wake-word.md](wake-word.md).

## Starting point from the earlier voice assistant

**One interface for every provider.** A provider takes a stream of audio
and returns a stream of events:

| Event | Meaning |
|---|---|
| Speech started | The person began to talk |
| Interim | The words so far, which may still change |
| Early end of turn | A short silence: the person has probably finished |
| Turn resumed | The person kept talking after all |
| End of turn | The person has finished |

**Answering early.** At the early end of turn (about 250 ms of silence)
the assistant starts preparing an answer. Only tools that read, and change
nothing, may run at that point. At the real end of turn (about 600 ms) the
prepared answer is used if the words are unchanged, and thrown away if the
person kept talking. In the earlier project's offline benchmark this cut
the time from end of turn to first sound from about 510 ms to about
310 ms.

**Providers.**

| Provider | Kind | Notes |
|---|---|---|
| sherpa-onnx | Local | Runs several models. It has a Rust interface and runs on Android and iOS |
| Deepgram | Cloud | Optional |

**Local models used there.**

| Model | Licence | Notes |
|---|---|---|
| Parakeet-TDT 0.6B v2 | CC-BY-4.0, needs attribution | The default |
| Whisper turbo | MIT | |
| Zipformer | Apache-2.0 | |
| Nemotron | NVIDIA's open model licence | Not checked; its archive carries no licence file |

Silero (MIT) detects when someone is speaking.

**Sharing.** Assistants with the same hearing settings share one
recogniser, so several assistants do not multiply the cost.

## Verified and assumed

Verified in the earlier project's code:

- The interface, the events and the answering-early behaviour.

From its documents only:

- The timings and the benchmark numbers. They were measured with recorded
  audio and a simulated AI model, never with a real microphone.
- Word error rates of 13% to 34% on phone-like audio.

Assumed, needing a build to confirm:

- The same models run fast enough through sherpa-onnx's Rust interface on
  a low-power ARM box.

## Settings

The timings and thresholds of this part are settings of an assistant,
with defaults. See [assistants](assistants.md).

## Open questions

- Which local model is the default, given accuracy, speed on low-power
  hardware and licence.

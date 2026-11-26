# Voice

The overview of everything spoken: assistants, how they are summoned, and
the speech technology underneath. Part of
[the technical design](../README.md).

Status: draft.

## How a spoken request flows

1. A device hears the **wake word**.
2. The server **identifies the speaker**.
3. The server resolves **permissions**: the assistant acts as that person.
4. **Speech to text** turns the request into words.
5. The assistant's **AI provider** answers and may use module tools.
6. **Text to speech** speaks the answer in the assistant's voice, and a
   screen may be shown.

Steps 1 to 3 are [summoning](summoning.md).

## Documents

| Document | Covers |
|---|---|
| [assistants.md](assistants.md) | The assistant as a character: identity, brain, abilities, scope |
| [summoning.md](summoning.md) | The process that decides whether, for whom and where an assistant answers |
| [wake-word.md](wake-word.md) | Detecting the wake word |
| [speaker-identification.md](speaker-identification.md) | Working out who is speaking |
| [speech-to-text.md](speech-to-text.md) | Turning speech into words |
| [text-to-speech.md](text-to-speech.md) | Speaking an answer |
| [reply-tags.md](reply-tags.md) | Metadata in a reply: character expressions, and staying awake for an answer |

## Rules for voice

- **Providers are modular and configurable.** Each speech job (wake word,
  speech to text, text to speech) has local models and cloud ones behind
  one interface, chosen in settings.
- **Local must be enough.** The system works fully with on-box models.
- **English first,** built so that other languages can be added.
- **Voice devices** are the voice page, tablets in kiosk mode, the phone
  app and the desktop client. See [clients](../clients/README.md).
- **Licences matter.** Every model and voice must allow use in hardware
  that is sold. See
  [licensing and hardware](../licensing-and-hardware.md).
- **A screen is optional.** A device with a screen can also show the
  answer. A device without one gets it by voice. See [A2UI](../a2ui.md).

## Starting point from the earlier voice assistant

Summoning is designed fresh, but the speech pipeline of the earlier
project works and is the starting point here. The detail is in
[speech-to-text.md](speech-to-text.md) and
[text-to-speech.md](text-to-speech.md).

- **Local speech stack:** sherpa-onnx, for speech to text and for local
  voices. It has a Rust interface and runs on Android and iOS.
- **Audio format:** 16 kHz, one channel, 16-bit, in 20 ms frames, sent as
  binary messages on the device's connection.
- **Narrow, streaming interfaces:** each provider takes a stream and
  returns a stream, and stops at once when interrupted.
- **Answering early:** the assistant starts preparing an answer at the
  first short silence, and discards it if the person keeps talking.
- **Speaking early:** the answer is spoken clause by clause while it is
  still being written.
- **Interruption:** talking over the assistant stops it, and the history
  keeps only what was heard.
- **A trace of every turn:** timing marks from the end of speech to the
  first sound, so that latency claims rest on numbers.

Not taken over:

- **Echo handling.** The earlier project compares the words it hears with
  the words it just spoke, and a reply that contains the wake word can
  stop itself. Its voice boxes have no echo cancellation.
- **Wake by transcription.** See [wake-word.md](wake-word.md).

## Verified and assumed

- The earlier project's pipeline was never run with a real microphone,
  speaker or small computer. Its numbers come from recorded audio.

## Speed targets

These are targets to tune against, not gates.

| From the end of the person's speech to the first sound of the answer | Target |
|---|---|
| With cloud speech and a cloud model | 1.5 seconds |
| With local speech and a local model on low-power hardware | 3 seconds |

## Open questions

- Echo: how a device avoids hearing its own answer.
- Whether audio shares the device's connection or has its own.

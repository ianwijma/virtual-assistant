# Wake word

Detecting the word that summons an assistant. Part of
[the voice design](README.md).

Status: draft. The detector is not chosen.

## Design

- **The wake words belong to the assistant.** Each assistant has a list
  of them, such as "Hey Jeff", and the list comes with the assistant to
  every device. The household chooses the words.
- **The list can hold other spellings of the same word,** for when an
  accent makes the usual one fail.
- **People can record themselves saying the wake words.** The recordings
  are used to recognise who is speaking. See
  [speaker identification](speaker-identification.md).
- **A device can override it.** A device can use a different wake word for
  an assistant. This is expected to be rare, so the setting sits in an
  advanced section.
- **Listening for a wake word is a setting of the device.** It is switched
  on for a device, and that device then listens for the wake words of the
  [assistants](assistants.md) assigned to it.
- A device with its own settings screen, such as the desktop client, sets
  this itself. A device without one, such as a tablet in kiosk mode, is set
  in the [admin panel](../clients/web-admin.md).
- Detection is the first step of [summoning](summoning.md).
- Where detection runs depends on the device:

| Device | Where the wake word is detected |
|---|---|
| Voice page in a browser | On the server. The page streams audio, so it stays small and works on old tablets. This costs server processing per device |
| Android tablet or phone | On the device. The app can keep listening with the screen off |
| iPad or iPhone | On the device, while the app is open in the foreground |
| Desktop client | Not decided |

## Verified and assumed

From the earlier voice assistant:

- It has no wake-word detector. It transcribes all audio and matches the
  text, which misses and misfires when a word is misheard.
- A trial of a small sherpa-onnx detector missed 21% of wakes, with
  synthetic voices on a desktop processor. It was never tried on small
  hardware.

Assumed, needing a build to confirm:

- Detection on the server scales to several devices on a low-power ARM
  box.

## Open questions

- Is a device's wake word override set per assistant on that device? It
  is written so for now.
- Which detector to use, and whether a detection is confirmed by
  transcribing the same audio.
- Where the desktop client detects the wake word.
- How false wakes and missed wakes are measured.

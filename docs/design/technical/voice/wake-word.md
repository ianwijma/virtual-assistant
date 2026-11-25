# Wake word

Detecting the word that summons an assistant. Part of
[the voice design](README.md).

Status: draft. The detector is not chosen.

## Design

- Each assistant has a wake word, such as "Hey Jeff".
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

- Which detector to use, and whether a detection is confirmed by
  transcribing the same audio.
- Whether custom wake words can be created by the household, and how.
- Where the desktop client detects the wake word.
- How false wakes and missed wakes are measured.

# Voice page

The light web page for talking to an assistant from any browser. Part of
[the clients design](README.md).

Status: draft.

## What it is

A small web page, served by the server, that relays voice. It lets any
device with a browser act as a voice device, including a tablet too old
for the app. It is one of the first ways to interact with the server.

## Design

- The page streams audio to the server, and the server detects the wake
  word. The page stays small. See [wake word](../voice/wake-word.md).
- It shows the assistant's visual and any screen the assistant presents.
- It works only while the page is visible.
- Browsers require HTTPS for the microphone. See
  [networking](../server/networking.md).

## Verified and assumed

Assumed, needing a build to confirm:

- Detecting the wake word on the server scales to several pages on a
  low-power box.

## Open questions

- Is a voice page a household device, a personal one, or either,
  depending on how it was opened?
- Does it need a sign-in or pairing? In the earlier voice assistant the
  voice page had no login at all.
- Can it be typed to as well as spoken to?

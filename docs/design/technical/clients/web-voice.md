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

## Personal or household

When the page is opened, the person chooses to use it as a personal
device or as a household device, as in the
[phone app](mobile.md). Each choice follows the same flow as there: a
personal page is signed in with an email address and a code, and a
household page is added with an admin's invite and then approved.

Before that, the page is not useless: it can already talk to guest
assistants, at guest level. See
[identity and sharing](../server/identity-and-sharing.md).

## Voice and chat

- By default the page is spoken to.
- **A button opens the conversation as text.** It shows what has been said
  so far and updates live while the person talks.
- **A person can also chat by typing,** to keep things quiet. The
  assistant then answers in text and does not speak.

## Open questions


# Phone app

How the look applies to the phone app in personal use. Part of
[the visual design](README.md). What the app does is in
[the technical design](../technical/clients/mobile.md).

Status: started. The screens, how they are joined and the call are set.

## Design

- **The app has several main screens, and no fixed first one:**

| Screen | What it is |
|---|---|
| Overview | A feed of what is running and what just arrived, with the assistant in a card |
| Assistant | The character has the screen, ready to be talked to |
| Timeline | Everything of today in one stream, newest first |
| Chat | The conversation with an assistant as text |

- **A floating glass tab bar joins them,** with one tab for each. The
  other areas, such as the clipboard, lists and settings, are reached
  from the avatar. This is "Tab bar" on
  [the phone screens board](examples/phone-screens-board.html).
- **A person chooses which screen the app opens on.**
- **Talking to an assistant shows the whole figure by default.** The
  character stands on the screen, as on the tablet. See
  [assistant visuals](assistant-visuals.md).
- **What the assistant shows pops up as a sheet** over the lower part of
  the screen, such as a list, and the figure stays visible above it.
- **Talking is like a call,** as in the ChatGPT app. The figure has the
  whole screen, and there are two round buttons at the bottom: Chat and
  End.
- **The call folds into the chat.** Switching to the chat does not leave
  the call. The figure shrinks into a glass header at the top, with its
  name, a sign of the sound level, and small buttons to mute and to end.
  The rest of the screen is the conversation as text, live, with a field
  to type in. A touch on the header returns to the full figure. This is
  "The call folds into the chat" on
  [the third phone conversation board](examples/phone-talk-board-3.html).
- The designs these came from are on
  [the phone home board](examples/phone-home-board.html) and
  [the phone conversation board](examples/phone-talk-board.html).
- It uses the roomy density. See
  [shape and spacing](shape-and-spacing.md).

## Open questions

- How is the microphone muted on the full call screen, which has only
  Chat and End?
- Is what is said also shown as a line of text on the full call screen?
- Where is the first screen chosen: in the app's own settings, or in the
  admin panel with a person's other settings?
- What does a touch on a clipboard item do: copy it to this phone, or
  open it?

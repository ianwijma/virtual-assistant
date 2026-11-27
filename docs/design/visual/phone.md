# Phone app

How the look applies to the phone app in personal use. Part of
[the visual design](README.md). What the app does is in
[the technical design](../technical/clients/mobile.md).

Status: started. Which screens exist is set. How they are joined is open.

## Design

- **The app has several main screens, and no fixed first one:**

| Screen | What it is |
|---|---|
| Overview | A feed of what is running and what just arrived, with the assistant in a card |
| Assistant | The character has the screen, ready to be talked to |
| Timeline | Everything of today in one stream, newest first |
| Chat | The conversation with an assistant as text |

- **A person chooses which screen the app opens on.**
- **Talking to an assistant shows the whole figure by default.** The
  character stands on the screen, as on the tablet. See
  [assistant visuals](assistant-visuals.md).
- **What the assistant shows pops up as a sheet** over the lower part of
  the screen, such as a list, and the figure stays visible above it.
- **A person can switch to the chat** and back. The chat shows the same
  conversation as text, live, while it is spoken.
- The designs these came from are on
  [the phone home board](examples/phone-home-board.html) and
  [the phone conversation board](examples/phone-talk-board.html).
- It uses the roomy density. See
  [shape and spacing](shape-and-spacing.md).

## Open questions

- How are the main screens joined: a tab bar, pages to swipe between, or
  something else? Several designs are on
  [the phone screens board](examples/phone-screens-board.html).
- How does a person switch between the figure and the chat? Several
  designs are on
  [the second phone conversation board](examples/phone-talk-board-2.html).
- Where is the first screen chosen: in the app's own settings, or in the
  admin panel with a person's other settings?
- What does a touch on a clipboard item do: copy it to this phone, or
  open it?

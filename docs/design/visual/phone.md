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

- **A floating glass tab bar joins them.** This is "Tab bar" on
  [the phone screens board](examples/phone-screens-board.html).
- **A person chooses what is on the bar.** It has four buttons that the
  person sets, and one fixed button at its end. The fixed button opens an
  overview of every area: the lists, the clipboard, the settings and any
  module added later. It is at the end in the direction of reading, so it
  is on the other side in a language read from right to left. The designs
  this came from are on
  [the phone areas board](examples/phone-areas-board.html).
- **The overview of all areas is a sheet that grows from that button.**
  It is a thick glass sheet over the lower part of the current screen,
  with the areas as a grid of icons, and the screen stays visible above
  it.
- **The bar is changed in that sheet.** An Edit button turns the four
  buttons of the bar into numbered slots. A touch on a slot selects it,
  and a touch on an area puts it there. This is "A sheet that grows from
  the button" on
  [the second phone bar board](examples/phone-bar-board-2.html).
- **A notification enters the top of the Overview's list.** See
  [the visual design](README.md).
- **A touch on a clipboard item copies it to the phone.** Holding it
  opens the item, with what else is known about it.
- **A new person's four are Overview, the assistant, Timeline and
  Chat.**
- **Anything can be one of the four:** an area, a single list such as
  Shopping, and later a screen of a module.
- **A person chooses which screen the app opens on,** in the settings of
  the app on that device.
- **Talking to an assistant shows the whole figure by default.** The
  character stands on the screen, as on the tablet. See
  [assistant visuals](assistant-visuals.md).
- **What the assistant shows pops up as a sheet** over the lower part of
  the screen, such as a list, and the figure stays visible above it.
- **Talking is like a call,** as in the ChatGPT app. The figure has the
  whole screen, and there are three round buttons at the bottom: Mute,
  Chat and End. This is "Three buttons" on
  [the call controls board](examples/call-controls-board.html).
- **What is said can also be shown as text.** A person can switch on a
  line of text under the figure, with the words of the moment in full
  strength. It shows what the assistant says, not what the person says. It is off unless switched on. This is the line of "Three
  buttons and a line of text" on the same board.
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
- **The sheet of all areas scrolls** when there are more than fit.
- **The fixed button shows a grid icon with the word "All".**
- **The line of text is switched on with a button on the call screen,**
  and the app remembers it.

## Open questions


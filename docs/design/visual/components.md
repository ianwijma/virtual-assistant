# Components

The shared components and how they behave. Part of
[the visual design](README.md).

Status: started. A few example components exist. The full set follows the
mockups.

## Design

- **Every component is built from the [tokens](tokens.md) only.**
- **A component looks and behaves the same in every client.** Each client
  builds it in its own toolkit. The
  [A2UI catalog](../technical/a2ui.md) components are built from the same
  parts.
- **Glass is for components that float:** cards over a backdrop, bars,
  sheets and menus. Lists and other content are plain. See
  [glass](glass.md).
- **A card is a row by default.** A card is what an assistant or the
  system shows for one thing: a timer, a notification, a list, a question
  to approve. It is a compact row with an icon or the character, two
  lines of text and one or two small buttons, and several are shown as a
  list, one under another. This is "Row cards" on
  [the card board](examples/card-board.html).
- **A touch on a card lifts it into a sheet.** The card rises out of its
  place into a larger glass card over the rest of the screen, which is
  dimmed, like a modal. The sheet floats over the middle of the list and has a
  button to close it. It has room for the whole content, such as every
  item of a list, and for larger buttons. The row it came from leaves a
  faint outline, so that it is clear where the sheet came from. This is
  "List of rows, sheet in the middle" on
  [the third card board](examples/card-board-3.html).
- **A screen has one primary action,** in the accent. Other actions are
  quiet.
- **Focus is always visible,** as a ring in the accent, since the desktop
  is used with the keyboard.
- **Waiting, empty and out of reach are shown as quietly as possible,**
  the same way in every client:

| State | What is shown |
|---|---|
| Waiting for the server | A thin line in the accent under the top bar. What was last known stays on screen |
| Nothing in it | One sentence in secondary text where the content would be |
| Home cannot be reached | A slim plain bar under the top bar that says so, with the time of the saved copy and a button to try again |

- **The app stays usable while home cannot be reached.** It works from
  its saved copy. What needs the server does not work, and the rest does.
  This is "As quiet as possible" on
  [the states board](examples/states-board.html). See
  [clients](../technical/clients/README.md).

## The examples

They are on [the example components page](examples/components.html), in
light and dark, built from [components.css](examples/components.css).

| Example | Shows |
|---|---|
| Timer card | A glass card with a character, a large number and two actions |
| Buttons | Primary, default, quiet, danger, disabled and focused |
| Settings fields | A text field, toggles and a segmented control |
| List | Plain rows with a selected row, shortcuts, status and a loader |
| Notification card | A glass card with a source, a text and actions |
| The accents | The five accents on the same card |
| Fallbacks | The same card as glass, without blur, and solid |
| Densities | The same list, roomy and compact |

## Open questions

- Agree to the example components as the base for the rest.
- While home cannot be reached, how does a thing that needs the server
  look: greyed out, hidden, or usable with the change sent later?
- Does the waiting line show at once, or only after a wait of about a
  second, so that a brief wait shows nothing?
- Does a changed setting apply at once, or after a Save button? The
  answer holds for the admin panel, the desktop settings and the app.
- Does a sheet also close by a touch on the dimmed area around it?
- On a tablet read from across a room, is a card shown open and large
  from the start?
- Which components come next? The proposal is the ones the mockups need:
  the launcher's search and results, a sheet, a menu, the tab bar and the
  side bar, a table for logs, the chat, and each card of the A2UI
  catalog.

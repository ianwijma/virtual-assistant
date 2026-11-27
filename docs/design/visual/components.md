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
  lines of text and one or two small buttons, so that several stack in a
  list. A touch on a card opens it to show more, such as the items of a
  list. This is "Row cards" on
  [the card board](examples/card-board.html).
- **A screen has one primary action,** in the accent. Other actions are
  quiet.
- **Focus is always visible,** as a ring in the accent, since the desktop
  is used with the keyboard.
- **A component that waits for the server shows a loader,** and the rest
  of the screen stays usable. See
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
- How does a row card open? Several designs are on
  [the second card board](examples/card-board-2.html).
- On a tablet read from across a room, is a card shown open and large
  from the start?
- Which components come next? The proposal is the ones the mockups need:
  the launcher's search and results, a sheet, a menu, the tab bar and the
  side bar, a table for logs, the chat, and each card of the A2UI
  catalog.

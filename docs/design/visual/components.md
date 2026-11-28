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
- **A card that was asked for shows large for a moment.** When a person
  asks for something, such as a timer, its card is shown larger for a
  short time and then returns to its small form. A card is small
  otherwise, on a tablet as well.
- **A touch on a card lifts it into a sheet.** The card rises out of its
  place into a larger glass card over the rest of the screen, which is
  dimmed, like a modal. The sheet floats over the middle of the list and has a
  button to close it. It has room for the whole content, such as every
  item of a list, and for larger buttons. The row it came from leaves a
  faint outline, so that it is clear where the sheet came from. This is
  "List of rows, sheet in the middle" on
  [the third card board](examples/card-board-3.html).
- **A sheet closes in several ways:** its close button, a touch on the
  dimmed area around it, Esc on a keyboard and a swipe down on a touch
  screen.
- **A screen that an assistant composed looks like any other.** It has
  no mark. That a screen was composed is shown in the chat's history
  and in the request timeline of the admin panel. See
  [described screens](../technical/a2ui.md).
- **A screen has one primary action,** in the accent. Other actions are
  quiet.
- **Focus is always visible,** as a ring in the accent, since the desktop
  is used with the keyboard.
- **Waiting, empty and out of reach are shown as quietly as possible,**
  the same way in every client:

| State | What is shown |
|---|---|
| Waiting for the server | A thin line in the accent under the top bar, shown only once the wait has lasted about half a second. What was last known stays on screen |
| Nothing in it | One sentence in secondary text where the content would be |
| Home cannot be reached | A slim plain bar under the top bar that says so, with the time of the saved copy and a button to try again |

- **A changed setting is saved with a Save button.** A changed field
  carries a small dot in the accent. A bar at the bottom of the page
  says how many changes are not saved, with Discard and Save. This holds
  in the admin panel, the desktop settings and the app. This is "A Save
  button" on [the saving board](examples/saving-board.html).
- **Leaving a page with unsaved changes asks first.** A small sheet
  offers Save, Discard and Stay.
- **The count of changes will open a list of them,** each with its value
  before and after. This comes after the first designs, possibly before
  the first release.
- **What needs home looks as usual while home cannot be reached.** A
  change is kept on the device and marked "Waiting to send", and the top
  bar counts the changes that wait. A timer runs on the device and is
  sent when home is back. An assistant that is opened says in one line
  that it cannot reach home. This is "Usable, sent later" on
  [the offline actions board](examples/offline-actions-board.html).
- **When two people changed the same thing, the first change stands.**
  The second person is told that someone else changed it, as an error.
- **The app stays usable while home cannot be reached.** It works from
  its saved copy. What needs the server does not work, and the rest does.
  This is "As quiet as possible" on
  [the states board](examples/states-board.html). See
  [clients](../technical/clients/README.md).
- **A dangerous action asks and then acts at once.** It does not go
  through the Save bar.
- **When changes that waited have been sent, their marks and the count go
  away.** Nothing else is said.
- **The chat's history shows that a screen was composed only in an
  advanced mode.**
- **A sheet with unsaved input asks before it closes by a touch outside
  it.**
- **A card that was asked for stays large for about five seconds.** Its
  large form is the sheet that a touch opens.
- **The next components are the ones the mockups need:** the launcher's
  search and results, a sheet, a menu, the tab bar and the side bar, a
  table for logs, the chat, and each card of the A2UI catalog.

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

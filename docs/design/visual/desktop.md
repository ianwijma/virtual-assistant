# Desktop client

How the look applies to the desktop client. Part of
[the visual design](README.md). What the client does is in
[the technical design](../technical/clients/desktop.md).

Status: started. The launcher's glass and shape and the place of the
settings are set.

## Design

- **The launcher is clear glass,** about half see-through, over whatever
  is on the desktop. See [glass](glass.md).
- **The launcher has more than one layout, and the content decides.**
  Where a preview helps, as in the clipboard, the window is wide with the
  list on the left and a preview of the selected row on the right. Where
  it does not, as in a plain search for actions, the window is a list
  only. These are "Wide with a preview" and "Classic window" on
  [the launcher layout board](examples/launcher-layout-board.html).
- **Under the search field is a row of chips:** the person's four areas
  and "All". A chip opens its area. Tab moves to the next chip and Shift
  with Tab to the one before, and the launcher can be opened straight
  into an area with a shortcut of that area.
- **A shortcut is always two or more keys together,** such as Ctrl,
  Shift and N. A single letter cannot be a shortcut, since it would be
  typed into the search field. See [the visual design](README.md).
- **Before anything is typed the launcher lists every action.** What is
  running now is on top, such as a timer. Under it are all the actions
  there are, ordered by how often they are used. Suggestions that follow
  what the person is doing may come later.
- **Talking to the assistant is an action like any other.** It is chosen
  from the list, and a person can give it a shortcut, as for any action. It has none at
  first.
  Tab is not its key, since Tab moves between the chips.
- **The launcher opens on the screen that holds the pointer.**
- **The launcher closes on a click elsewhere, in every view,** the
  settings included. With unsaved changes in the settings it asks first:
  Save, Discard or Stay.
- **The window grows smoothly.** It is narrow for a plain list and
  widens with a short animation for a view with a preview, and stays
  centred.
- **The launcher remembers where it was.** Opened again within about a
  minute, it shows the view and the state it was closed in, such as the
  settings page that was open. After that it opens in its neutral state.
- **For now only the clipboard has a preview.** The launcher keeps
  several kinds of view, so that a later feature can use the one that
  fits it.
- **A notification appears at the top right of the desktop,** outside
  the launcher, as a clear glass card. Several stack downward with the
  newest on top. This is "Top-right stack" on
  [the desktop notification board](examples/desktop-notification-board.html).
- **The settings of the device are a view of the launcher.** They are
  opened from the launcher, as in Raycast, and the launcher shows them in
  place of its list. They can also be opened from an icon in the system
  tray. There is no separate application for them.
- **The settings are laid out like the admin panel, in three columns:**
  a side bar of groups with a search field, a list of the chosen group's
  settings, and the chosen setting's page with its control and a
  sentence that explains it. The window is larger than the launcher's
  list. See [admin panel](admin-panel.md). This is "Three columns" on
  [the second desktop settings board](examples/desktop-settings-board-2.html),
  and the designs before it are on
  [the first](examples/desktop-settings-board.html).
- **It appears with a very short animation.** See [motion](motion.md).
- **It uses the compact density.** See
  [shape and spacing](shape-and-spacing.md).
- **The launcher returns to its neutral state after one minute.**
- **The tray icon's menu holds:** open the launcher, the settings, the
  state of the connection, and quit.
- **In the settings Esc first clears a search,** and then returns to the
  list.
- **A notification is answered in the launcher's notification centre,**
  not on the card. The card on the desktop does not take the keyboard.
  The centre is opened like any view, and its rows are used with the
  keyboard like any list.
- **A highlighted row has one main action, on Enter.** For a clipboard
  item that is copying it. For a notification it is opening it to read,
  and a person can set it to acknowledge the notification instead.
- **More actions open in a panel, with Ctrl and K,** as in Raycast. The
  arrow keys move through it, and Esc returns to the search field. For a
  notification the actions are such as reply, acknowledge, delete and
  snooze until a later time, such as tomorrow morning.
- **The notification centre has three sections:** what needs attention,
  which holds new ones and snoozed ones that are back; what is being
  worked on; and what is settled.
- **A question from an assistant stays on screen until it is answered or
  dismissed.**
- **The order of the actions follows this person's own use.**

## Open questions



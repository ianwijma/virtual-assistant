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
  and "All". See [the visual design](README.md).
- **Before anything is typed the launcher lists every action.** What is
  running now is on top, such as a timer. Under it are all the actions
  there are, ordered by how often they are used. Suggestions that follow
  what the person is doing may come later.
- **A notification appears at the top right of the desktop,** outside
  the launcher, as a clear glass card. Several stack downward with the
  newest on top. This is "Top-right stack" on
  [the desktop notification board](examples/desktop-notification-board.html).
- **The settings of the device are a view of the launcher.** They are
  opened from the launcher, as in Raycast, and the launcher shows them in
  place of its list. There is no separate application for them.
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

## Open questions

- Does the settings view stay open when the person clicks elsewhere,
  unlike the launcher's list?
- In the settings, does Esc first clear a search and only then return to
  the list?
- Can a notification on the desktop be answered from the keyboard?
- Does a question from an assistant stay on screen until it is answered?
- Which views of the launcher have a preview, and which are a list only?
- Is the order of the actions in the launcher taken from this person's
  own use, from the household's, or from both?
- Does the window change size when it goes from a list to a list with a
  preview, or is it always the wide size?

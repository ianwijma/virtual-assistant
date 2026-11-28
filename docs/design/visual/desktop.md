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
- **A notification appears at the top right of the desktop,** outside
  the launcher, as a clear glass card. Several stack downward with the
  newest on top. This is "Top-right stack" on
  [the desktop notification board](examples/desktop-notification-board.html).
- **The settings of the device are a view of the launcher.** They are
  opened from the launcher, as in Raycast, and the launcher shows them in
  place of its list. There is no separate application for them.
- **The settings are laid out like the admin panel:** a side bar of
  groups with a search field, and the chosen group's page. See
  [admin panel](admin-panel.md). The designs this came from are on
  [the desktop settings board](examples/desktop-settings-board.html).
- **It appears with a very short animation.** See [motion](motion.md).
- **It uses the compact density.** See
  [shape and spacing](shape-and-spacing.md).

## Open questions

- Does the launcher's window grow to hold the settings, and does it stay
  open when the person clicks elsewhere, unlike the launcher's list?
- Does a changed setting apply at once, or after a Save button?
- Can a notification on the desktop be answered from the keyboard?
- Does a question from an assistant stay on screen until it is answered?
- Which views of the launcher have a preview, and which are a list only?
- Does the launcher show suggestions before anything is typed? With a
  preview, the empty launcher can show what is running now.
- Does the window change size when it goes from a list to a list with a
  preview, or is it always the wide size?

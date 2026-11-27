# Desktop client

How the look applies to the desktop client. Part of
[the visual design](README.md). What the client does is in
[the technical design](../technical/clients/desktop.md).

Status: started. The launcher's glass and shape are set.

## Design

- **The launcher is clear glass,** about half see-through, over whatever
  is on the desktop. See [glass](glass.md).
- **The launcher has more than one layout, and the content decides.**
  Where a preview helps, as in the clipboard, the window is wide with the
  list on the left and a preview of the selected row on the right. Where
  it does not, as in a plain search for actions, the window is a list
  only. These are "Wide with a preview" and "Classic window" on
  [the launcher layout board](examples/launcher-layout-board.html).
- **It appears with a very short animation.** See [motion](motion.md).
- **It uses the compact density.** See
  [shape and spacing](shape-and-spacing.md).

## Open questions

- Which views of the launcher have a preview, and which are a list only?
- Does the launcher show suggestions before anything is typed? With a
  preview, the empty launcher can show what is running now.
- Does the window change size when it goes from a list to a list with a
  preview, or is it always the wide size?

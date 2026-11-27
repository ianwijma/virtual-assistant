# Household tablet

How the look applies to a tablet in a room, in kiosk mode. Part of
[the visual design](README.md). What it does is in
[the technical design](../technical/clients/mobile.md).

Status: started. The idle screen and the active screen are set in
outline.

## Design

- **While nobody uses it, the tablet shows the wallpaper,** such as a
  family photo, with three things on it: a large clock, a few small
  glance bars, and the assistant's figure.
- **A glance bar is a small, flat rectangle** with one fact: a running
  timer, the next reminder, the number of items on the shopping list.
- **The figure lives on the idle screen,** with a hint of how to call it,
  such as "Say Hey Juno".
- **When an assistant is active it stands on a stage.** See
  [assistant visuals](assistant-visuals.md).
- **In low-power mode the screen is black** with a dim clock and no
  glass. See [glass](glass.md).
- **Text is sized to be read from across a room.**
- The designs these came from are on
  [the tablet idle board](examples/tablet-idle-board.html) and
  [the tablet board](examples/tablet-board.html).

## Open questions

- How are the clock, the glance bars and the figure arranged on the idle
  screen? Several designs are on
  [the second tablet idle board](examples/tablet-idle-board-2.html).
- Does the clock move now and then, to protect the screen?
- Is the figure on the idle screen at night as well, or does the tablet
  then show only the clock?
- After how long without speech does the stage close and the idle screen
  return?

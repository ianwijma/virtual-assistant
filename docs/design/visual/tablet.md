# Household tablet

How the look applies to a tablet in a room, in kiosk mode. Part of
[the visual design](README.md). What it does is in
[the technical design](../technical/clients/mobile.md).

Status: started. The idle screen and the active screen are set.

## Design

- **While nobody uses it, the tablet shows the wallpaper,** such as a
  family photo, with three things on it: a large clock, a few small
  glance bars, and the assistant's figure.
- **A slim glass shelf runs along the bottom of the screen.** The glance
  bars sit in it and the figure stands on it. The bars are at
  the right of the shelf and the figure stands on its left end. The clock
  is large at the top left, on the photo. The rest of the photo stays
  clear. This is "Shelf with bars, clock above" on
  [the third tablet idle board](examples/tablet-idle-board-3.html).
- **A glance bar is a small, flat rectangle** with one fact: a running
  timer, the next reminder, the number of items on the shopping list. It
  is a [card](components.md) in its closed form.
- **A tablet with several assistants shows one figure at a time.** Small
  dots under it show that there are others, and the figure changes now
  and then. This is "One at a time" on
  [the idle figures board](examples/idle-figures-board.html).
- **The figure lives on the idle screen.** There is no written hint of
  how to call it, since a tablet can have several assistants, each with
  its own wake word.
- **When an assistant is active it stands on a stage.** See
  [assistant visuals](assistant-visuals.md).
- **In the dark the tablet follows the light in the room.** When the
  room is a little dark, or it is night, the photo is dimmed and the
  figure sleeps. When the room is fully dark, only a dim clock is shown.
  This can be set per tablet. These are the two night screens on
  [the idle figures board](examples/idle-figures-board.html).
- **In low-power mode the screen is black** with a dim clock and no
  glass. See [glass](glass.md).
- **Text is sized to be read from across a room.**
- The designs these came from are on
  [the tablet idle board](examples/tablet-idle-board.html) and
  [the tablet board](examples/tablet-board.html).

## Open questions

- How often does the figure on the idle screen change, and can a touch
  on the dots change it?
- Which assistant is shown first: the one used last, or a fixed order?
- Does the clock move now and then, to protect the screen?
- How does a tablet without a light sensor know the room is dark: by
  the time of day, by its camera, or does a person set the hours?
- What can be set for the dark on a tablet: only which of the two
  screens is used, or also the hours and how dim it is?
- After how long without speech does the stage close and the idle screen
  return?

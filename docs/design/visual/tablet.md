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
  dots under it show that there are others. This is "One at a time" on
  [the idle figures board](examples/idle-figures-board.html).
- **The figure lives on the idle screen.** There is no written hint of
  how to call it, since a tablet can have several assistants, each with
  its own wake word.
- **The conversation closes after 20 to 30 seconds without speech,** and
  the idle screen returns. The time is set for the whole server, and
  may also be set per device.
- **When an assistant is active it stands on a stage.** See
  [assistant visuals](assistant-visuals.md).
- **In the dark the tablet follows the light in the room, on one
  screen.** The darker the room, the darker the same idle screen
  becomes: the photo is dimmed and the figure sleeps, and when the room
  is fully dark everything is black except the clock. The clock is
  always shown. It is one screen whose parts change, so the change is
  smooth.
  This can be set per tablet. These are the two night screens on
  [the idle figures board](examples/idle-figures-board.html).
- **Low-power mode is that same screen at its darkest:** black, with a
  dim clock and no glass. See [glass](glass.md).
- **Text is sized to be read from across a room.**
- The designs these came from are on
  [the tablet idle board](examples/tablet-idle-board.html) and
  [the tablet board](examples/tablet-board.html).
- **The figure on the idle screen changes by a touch on the dots.** It
  does not change by itself unless that is switched on, for the
  household or for one device, and then it
  changes every 10 to 15 minutes. This leaves a character free to play
  an idle animation. The assistant that was used last is shown first.
- **The clock shifts a little now and then,** to protect the screen.
- **A tablet that cannot measure the light uses the time of day,** with
  hours that can be set.
- **For the dark, a tablet's settings hold which of the two screens is
  used and the hours.**
- **The time before a conversation closes is 30 seconds at first.**
- **The character shows that the conversation is about to close,** by
  winding down.

## Open questions

- Where does the bar for "home cannot be reached" go on a tablet, which
  has no top bar?
- On a household tablet, what marks the pinned areas as set by an admin:
  a small lock in place of the pencil?


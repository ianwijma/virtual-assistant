# Motion and sound

How things move, and what is heard and felt. Part of
[the visual design](README.md).

Status: started. The character of the motion is set. Sound is open.

## Design

- **Motion is fluid and springy,** following Apple's design. Things move
  as if they have weight: a sheet springs into place, a button gives
  under a press, a panel grows from the control that opened it.
- **What opens grows from what was touched.** A sheet, a pop-up or a new
  page grows out of the row, card or button that opened it, so that the
  action is seen to have a result. A card row swells into its sheet with
  a light overshoot. This is "Grows from the row" on
  [the motion board](examples/motion-board.html), and it is used
  wherever one thing opens another.
- **What is on both sides of a change stays on screen.** A part that is
  on the old and on the new screen, such as a title, is not removed and
  drawn again. It moves to its new place while the rest changes.
- **There are two modes: full motion and reduced motion.** Reduced motion
  switches the springs and movements off and keeps at most a short fade.
- **Reduced motion is used in three cases:** when the device's own
  setting asks for it, when a person switches it on for a device in our
  settings, and on a device that is too slow to move things smoothly.
  This keeps an old tablet fast.
- **Motion never makes a person wait.** An animation does not block
  input: a person can act while it runs.
- **The desktop launcher appears with a very short animation,** of about
  80 ms. It is drawn and takes typing at once; the animation does not
  delay it. See [desktop](../technical/clients/desktop.md).

## The timings

| Token | Value | Used for |
|---|---|---|
| Instant | 80 ms | The launcher appearing |
| Fast | 140 ms | A press, a hover, a small change of state |
| Base | 240 ms | A toggle, a card, a menu |
| Slow | 420 ms | A sheet, a change of screen, the backdrop changing accent |
| Spring | A light overshoot that settles | Things that appear or are pressed |

In reduced motion every timing is at most a 100 ms fade.

## Open questions

- Are sounds part of the identity, such as a tone when an assistant
  starts listening or a timer ends?
- Does the phone use vibration as part of the feel?
- Where a toolkit cannot grow a new page out of the thing that was
  touched, what is shown: the sheet rising from below, or a plain fade?
- Does everything that opens end with the light overshoot, or only
  sheets?
- How is a device found to be too slow for full motion: measured by the
  client, or switched by hand only?

To research:

- Whether Slint, Jetpack Compose, SwiftUI and CSS can each grow a sheet
  or a page out of one element and keep a shared element, such as a
  title, moving between two screens.

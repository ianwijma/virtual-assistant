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
- **Sounds and vibration are switched on per device.**
- **Where a toolkit cannot grow one thing out of another,** a sheet rises
  from below and a page fades in.
- **Only sheets and things that are pressed end with the light
  overshoot.** A page settles without it.
- **A client measures whether its device is too slow for full motion,**
  and a person can also switch reduced motion on by hand.

## Sound and vibration

- **Feedback is visual first.** What happens is shown on the screen, so
  that talking to an assistant feels like a conversation and not like
  operating a machine.
- **There is a small set of sounds of our own.**
- **The sounds of a conversation are off unless switched on,** such as
  the tone when an assistant starts to listen. The screen shows those.
- **Every other sound is on unless switched off,** such as a timer or an
  alarm that ends and a notification.
- **The phone can vibrate as part of the feel.** In a conversation this
  is off unless switched on.

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

- Which sounds are in the set, and who makes them?

To research:

- Whether Slint, Jetpack Compose, SwiftUI and CSS can each grow a sheet
  or a page out of one element and keep a shared element, such as a
  title, moving between two screens.

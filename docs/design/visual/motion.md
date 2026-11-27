# Motion and sound

How things move, and what is heard and felt. Part of
[the visual design](README.md).

Status: started.

## Design

- **The desktop launcher appears with no animation.** It must be on
  screen within 100 ms of its shortcut, and nothing may delay it. See
  [desktop](../technical/clients/desktop.md).
- **Motion never makes a person wait.** An animation does not block
  input: a person can act while it runs.
- **The device's setting for reduced motion is followed.** Movement is
  then replaced by a plain fade or by nothing.

## Open questions

- How much does the interface move where it is allowed to: fluid and
  springy as in Apple's design, or quick and plain?
- Are sounds part of the identity, such as a tone when an assistant
  starts listening or a timer ends?
- Does the phone use vibration as part of the feel?

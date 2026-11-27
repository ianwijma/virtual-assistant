# Colour

The colours of the system, in light and dark. Part of
[the visual design](README.md).

Status: candidates to choose from. No colour is chosen yet.

## Design

- **There is a light and a dark form,** and each client follows the
  setting of the device it runs on.
- **A person cannot choose a theme.**
- **The colours are tokens.** Every client and every
  [described screen](../technical/a2ui.md) takes them from the one set of
  design tokens.

## Proposal: the parts of the palette

Whatever the colours become, the palette has these parts:

| Part | Used for |
|---|---|
| Backdrop | What is behind the [glass](glass.md) |
| Glass | The tint and the edge of a glass surface |
| Text | Primary, secondary and disabled text, readable on glass |
| Accent | The one colour for the main action, for selection and for focus |
| Status | Success, warning and danger |
| Assistant colours | One per assistant, if assistants have a colour |

## Candidates

Five directions are shown on
[the direction board](examples/direction-board.html), each in light and
dark. The colours on the board are rough. They show a direction, not final
values.

| Direction | Accent | Neutrals | Feels |
|---|---|---|---|
| A. Tide | Blue to teal | Cool grey | Calm and clean. The closest to Apple's own look |
| B. Ember | Coral to amber | Warm grey | Warm and homely |
| C. Aurora | Violet to cyan | Cool, slightly violet | Lively. The look many AI products have |
| D. Moss | Sage green | Warm, natural grey | Quiet and natural |
| E. Clear | None of its own | Pure grey | The interface has no colour. All colour comes from the assistants |

## Open questions

- Which direction, A to E, or which mix of them? See the direction
  board.
- Agree to the parts of the palette in the proposal above.
- Is there one accent colour for everyone, or may a person choose their
  own accent? A theme cannot be chosen; is an accent a theme?
- Does each assistant have its own colour, and does the screen take that
  colour while the assistant is active?
- Does each person have a colour, to show whose account is active on a
  shared computer, or who added an item to a shared list?
- Is dark a true black, which saves power on a tablet with an OLED
  screen, or a dark grey with a slight tint?
- Is light a pure white, or a slightly tinted, softer white?
- Are the status colours the usual green, amber and red?
- How readable must text be: the common standard of a contrast of 4.5 to
  1 for normal text, or stricter?
- Are there colours to avoid, and is anyone in the household
  colour-blind?
- A tablet in a room has its light or dark setting fixed by whoever set
  it up. Should a household tablet go dark at night by itself?
- "Follows the device" means there is no switch for light and dark in
  our own settings. Is that right, or should a person be able to
  override it per device?

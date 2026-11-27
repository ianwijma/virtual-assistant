# Colour

The colours of the system, in light and dark. Part of
[the visual design](README.md).

Status: candidates to choose from. No colour is chosen yet.

## Design

- **There is a light and a dark form,** and each client follows the
  setting of the device it runs on.
- **A person cannot choose a theme.** There is no switch for light and
  dark in our own settings, and no accent colour to choose. There is one
  accent colour for everyone.
- **Dark is a dark grey with a slight tint, not black.** Glass needs
  something behind it, and on black it disappears. Only the low-power
  screen of a tablet is true black.
- **Status colours are the usual ones:** green for success, amber for a
  warning, red for danger. A status is never shown by colour alone; it
  also has an icon or a word.
- **Text is readable on every surface it is on,** glass included: a
  contrast of at least 4.5 to 1 for normal text and 3 to 1 for large
  text, measured against the least favourable backdrop.
- **The colours are tokens.** Every client and every
  [described screen](../technical/a2ui.md) takes them from the one set of
  design tokens.

## The parts of the palette

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
- Does each assistant have its own colour, and does the screen take that
  colour while the assistant is active?
- Does each person have a colour, to show whose account is active on a
  shared computer, or who added an item to a shared list?
- Is light a pure white, or a slightly tinted, softer white?
- Are there colours to avoid, and is anyone in the household
  colour-blind?
- A tablet in a room has its light or dark setting fixed by whoever set
  it up. Should a household tablet go dark at night by itself?

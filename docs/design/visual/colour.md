# Colour

The colours of the system, in light and dark. Part of
[the visual design](README.md).

Status: started. The structure is set. The exact values are made with the
design tokens.

## Design

- **There is a light and a dark form,** and each client follows the
  setting of the device it runs on. There is no switch for light and dark
  in our own settings.
- **A person cannot choose a theme.** The one thing that can be chosen is
  the accent.
- **The base is neutral.** Glass, text and plain surfaces are greys with
  no colour of their own. All colour comes from the accent, from the
  status colours and from the assistants.
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

## The accent

The accent is the one colour for the main action, for selection and for
focus. It also colours our own [backdrop](glass.md).

- **The accent is chosen from a fixed set.** Each accent in the set is
  checked for readable text in light and in dark.
- **It can be set in three places,** and the most specific one wins:

| Set on | Applies to | Wins over |
|---|---|---|
| The household | Every device, unless something more specific is set | Nothing |
| A device | That device | The household's |
| A person | Wherever that person is the one using the device | The device's and the household's |

- **On a personal device** the person's accent is shown, since the device
  is theirs.
- **On a household device** the accent changes to a person's own when an
  assistant recognises their voice, and returns to the device's or the
  household's when the conversation ends. An unrecognised voice changes
  nothing.

The first set, with working names. The values are made with the tokens.

| Accent | Colour |
|---|---|
| Tide | Blue to teal |
| Ember | Coral to amber |
| Aurora | Violet to cyan |
| Moss | Sage green |
| Graphite | Neutral: near black in light, near white in dark |

## The parts of the palette

| Part | Used for |
|---|---|
| Backdrop | What is behind the [glass](glass.md) |
| Glass | The tint and the edge of a glass surface |
| Text | Primary, secondary and disabled text, readable on glass |
| Accent | The colour for the main action, for selection and for focus |
| Status | Success, warning and danger |
| Assistant colours | One per assistant, if assistants have a colour |

## Open questions

- Which accent does a new household start with?
- Should the set have more accents, such as a pink or a red, and how
  many is enough?
- Does each assistant have its own colour? If so, which one shows while
  an assistant is active on a household device: the assistant's, or the
  accent of the person it recognised?
- Is a person's accent also the colour that marks them elsewhere, such as
  on the account switch of a shared computer, or beside an item they
  added to a shared list?
- Is light a pure white, or a slightly tinted, softer white?
- Are there colours to avoid, and is anyone in the household
  colour-blind?
- A tablet in a room has its light or dark setting fixed by whoever set
  it up. Should a household tablet go dark at night by itself?

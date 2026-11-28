# Colour

The colours of the system, in light and dark. Part of
[the visual design](README.md).

Status: started. The structure is set. The exact values are made with the
design tokens.

## Design

- **There is a light and a dark form,** and each client follows the
  setting of the device it runs on.
- **Every device has a setting for light and dark:** follow the device,
  always light, always dark, by the time of day, or by the light in the
  room. A phone and a desktop start on "follow the device".
- **A person cannot choose a theme.** The one thing that can be chosen is
  the accent.
- **Text and glass are neutral.** They are greys with no colour of their
  own.
- **Plain surfaces take a tint of the accent.** The base carries 3% of
  the accent's main colour. Each plain panel, such as a list or a page,
  has a soft run from 5% of the main colour at its top left to 5% of the
  second colour at its bottom right. This holds in light and in dark.
  This is "A soft run across each panel" on
  [the tint board](examples/tint-board.html); the whites it came from
  are on [the white board](examples/white-board.html).
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

- **An accent is two colours:** a main colour, and a second colour for
  the backdrop.
- **Four accents are built in:** Tide, Ember, Aurora and Moss. Each is
  checked for readable text in light and in dark. A new household starts
  with Tide. This is "Tide" on
  [the accent start board](examples/accent-start-board.html).
- **A person can also make their own accent.** Under the built-in
  accents is a grid of pairs of colours that go well together, with a
  button that brings a new set of pairs. A link leads to a free choice:
  one colour wheel with two handles, one for each colour. These are
  "Pairs that go together" and the wheel of "A two-handle colour wheel"
  on [the accent picker board](examples/accent-picker-board.html).
- **A colour that makes text hard to read gives a warning, and is
  allowed.** The person can keep it.
- **Choosing an accent shows a quick preview.** In the admin panel, the
  accent of the household is previewed on all four devices: the phone
  app, the tablet, the desktop and the admin panel. The accent of one
  device is previewed on that device only.
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
- **A recognised person is named in a chip.** While the conversation
  lasts, a small chip beside the assistant's name shows the person's
  name.
- **A person is marked by their accent and their photo.** A person can
  upload a photo of themselves. It is shown small and round with a ring
  in their accent, in the chip and wherever the person is marked, such
  as beside an item they added to a shared list. Their name or initial
  is always with it. A person without a photo shows their initial in
  the ring, on a soft fill of their accent.
- **An assistant has a colour of its own.** Its figure is drawn in that
  colour everywhere, whoever it talks to. The backdrop and the buttons
  around it follow the accent as above. This is "Figure in its own
  colour, screen in the person's" on
  [the assistant colour board](examples/assistant-colour-board.html),
  with the chip of the design beside it.

The built-in accents, with working names. The values are made with the
tokens.

| Accent | Colour |
|---|---|
| Tide | Blue to teal |
| Ember | Coral to amber |
| Aurora | Violet to cyan |
| Moss | Sage green |

Graphite, a neutral accent, is drawn and is left out for now.

## The parts of the palette

| Part | Used for |
|---|---|
| Backdrop | What is behind the [glass](glass.md) |
| Glass | The tint and the edge of a glass surface |
| Text | Primary, secondary and disabled text, readable on glass |
| Accent | The colour for the main action, for selection and for focus |
| Status | Success, warning and danger |
| Assistant colours | One per assistant, for its figure |

## Open questions

- Where does the warning about a colour that is hard to read appear:
  under the wheel, where "Checked: text stays readable" is on the board?
- Does the wheel set only the hue, or also how light and how strong a
  colour is?
- How is the wheel used with a keyboard, and can a value be typed?
- Where can an accent be chosen besides the admin panel: on the device
  itself, in its own settings?
- Is a character's colour picked with the same picker as the accent, and
  who may change it?
- What happens when an assistant's colour and the person's accent are
  the same, or clash?
- Should the set have more built-in accents, such as a pink or a red?
- Does Graphite return later as a built-in accent?
- Are there colours to avoid, and is anyone in the household
  colour-blind?
- Which setting for light and dark does a new household tablet start
  with?

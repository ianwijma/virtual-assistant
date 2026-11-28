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
- **No colour is avoided, and no check for colour-blindness is made.**
  The design relies on the rule that a status is never shown by colour
  alone.
- **The colours are tokens.** Every client and every
  [described screen](../technical/a2ui.md) takes them from the one set of
  design tokens.
- **The warning about a colour that is hard to read is under the picker,**
  in the place where it otherwise says that text stays readable.
- **The wheel works with a keyboard.** The arrow keys move the handle that
  has the focus. There is no field to type a value in.
- **An accent is chosen in the admin panel and on the device itself,** in
  its settings.
- **A character's colour is picked with the same picker as the accent,**
  by whoever may change the character.
- **A new household tablet follows the light in the room,** and the time
  of day where it cannot measure the light.

## The accent

The accent is the one colour for the main action, for selection and for
focus. It also colours our own [backdrop](glass.md).

- **An accent is two colours:** a main colour, and a second colour for
  the backdrop.
- **Seven accents are built in:** Tide, Ember, Aurora, Moss, a pink, a
  red and Graphite. Each is checked for readable text in light and in
  dark. A new household starts with Tide. This is "Tide" on
  [the accent start board](examples/accent-start-board.html).
- **A person can also make their own accent.** Under the built-in
  accents is a grid of pairs of colours that go well together, with a
  button that brings a new set of pairs. A link leads to a free choice:
  one colour wheel with two handles, one for each colour. The wheel sets
  the colour only; how light and how strong it is, is ours to set. These are
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
- **A character has two colours of its own,** like an accent. Its figure
  is drawn in them everywhere, whoever it talks to. Both can be set to
  the same colour, which gives a figure of one colour. Nothing is done
  when a character's colours and the person's accent are alike. The backdrop and the buttons
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
| A pink | To be made |
| A red | To be made |
| Graphite | Neutral: near black in light, near white in dark |

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

- Which pink and which red are built in, with which second colour, and
  what are they called?


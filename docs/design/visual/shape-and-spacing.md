# Shape and spacing

Corners, density, spacing and icons. Part of
[the visual design](README.md).

Status: started. The exact values are made with the design tokens.

## Design

- **Corners are clearly round.** A panel has a corner of about 16 to 24,
  and a control inside it a smaller one that follows the panel's curve.
  Controls are not pill-shaped. This is "Clearly round" on
  [the direction board](examples/direction-board.html).
- **There are two densities from one scale.** A compact one serves a
  mouse and a keyboard and long lists. A roomy one serves touch, and a
  screen that is read from across a room.
- **Each device has a default density, and it can be changed.** The
  desktop client and the admin panel start compact. The phone and the
  tablet start roomy.
- **There are no illustrations apart from the character.** Where a
  picture helps, such as on an empty screen or in the setup, the
  character appears in a fitting pose. Everything else uses an icon or
  a sentence.
- **The icons are Phosphor's,** an open set under the MIT licence, which
  allows sold hardware. Where the set lacks an icon, we draw our own in
  its style. Icons are always outlined; a chosen item is shown by the
  accent and the highlight behind it, not by a filled icon. Apple's symbols cannot be used. The sets it was chosen from
  are on [the icon board](examples/icon-board.html).
- **The density is changed on the device itself and in the admin panel.**
  It is one setting for the whole device, and a household tablet has it
  like any other device.

## Open questions


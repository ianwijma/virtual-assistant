# Typography

The typeface and the type scale. Part of [the visual design](README.md).

Status: started. The typeface is chosen and a first scale is set.

## Design

- **The typeface is Inter.** It is neutral and precise, and close to the
  typeface of Apple's own design. It is under the SIL Open Font License,
  which allows sold hardware. It covers Latin, Greek, Cyrillic and
  Vietnamese.
- **It is shipped with every client,** so that text looks the same on
  every device. No client uses the font of the platform it runs on.
- **Logs and timelines use JetBrains Mono,** shipped with every client.
  It is under the SIL Open Font License, which allows sold hardware.
- **One family is used for everything else.** Headings differ by size and
  weight, not by typeface.
- **Text follows the text size set on the device.** A person who has set
  larger text on their phone gets larger text in the app.
- **Numbers that change in place,** such as a running timer, have digits
  of equal width, so that they do not jump.
- The candidates that were compared are on
  [the typeface board](examples/typeface-board.html).

## The scale

Sizes are in the unit of the platform that scales with the text size
setting. The values are in [tokens](tokens.md).

| Style | Size / line | Weight | Used for |
|---|---|---|---|
| Display, extra large | 96 | 600 | A clock or a timer read from across a room |
| Display | 34 / 40 | 600 | The main number or greeting of a screen |
| Title | 22 / 28 | 600 | The title of a screen or a sheet |
| Heading | 17 / 22 | 600 | The heading of a group or a card |
| Body | 15 / 22 roomy, 13 / 18 compact | 400 | Text and list rows |
| Body, strong | As body | 600 | The name of a thing in a row or card |
| Label | 13 / 18 roomy, 12 / 16 compact | 500 | Buttons, secondary lines, field labels |
| Caption | 11 / 14 | 500 | Small capitals above a value, shortcuts, times |
| Mono | 12 / 18 | 400 | Logs and timelines |

## Open questions

- Which languages and scripts must be covered later, beyond what Inter
  covers?

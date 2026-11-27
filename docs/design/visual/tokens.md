# Tokens

The full set of design tokens. Part of [the visual design](README.md).

Status: a first set. The values are tried out in
[the example components](examples/components.html) and will be tuned.

## Design

- **The tokens are the single source** of every colour, size, shape and
  timing. Each platform's theme is generated from them: Slint, SwiftUI,
  Jetpack Compose and CSS.
- **A component uses tokens only.** It never holds a colour or a size of
  its own.
- **Every colour token has a light and a dark value.**
- **The web form exists already,** as
  [examples/tokens.css](examples/tokens.css). It is used by the example
  pages and the mockups. Until the tokens have their own source file in
  the repository, this document and that file are kept in step by hand.

## Neutral colours

| Token | Light | Dark | Used for |
|---|---|---|---|
| `bg` | `#F4F5F7` | `#101216` | Behind everything, under the backdrop |
| `surface` | `#FFFFFF` | `#17191E` | Plain content: lists, logs, text |
| `surface-2` | `#F4F5F7` | `#1E2127` | A plain area inside plain content |
| `text` | `#14161A` | `#F2F4F7` | Primary text |
| `text-2` | `text` at 64% | `text` at 66% | Secondary text |
| `text-3` | `text` at 42% | `text` at 40% | Disabled text and placeholders |
| `line` | Black at 10% | White at 10% | Dividers and borders |

## Glass

| Token | Light | Dark | Used for |
|---|---|---|---|
| `glass` | White at 58% | `#22252D` at 52% | Bars and cards |
| `glass-thick` | White at 74% | `#1E2128` at 72% | The launcher, sheets and menus; also glass without blur |
| `glass-solid` | `#FFFFFF` | `#23262E` | Glass with reduced transparency |
| `glass-edge` | White at 85% | White at 14% | The thin light edge |
| `glass-blur` | 24 | 24 | The blur of what is behind |
| `glass-saturate` | 170% | 170% | How much colour comes through |
| `control` | Black at 6% | White at 9% | A control resting on glass |
| `shadow-1`, `-2`, `-3` | Soft, dark blue-grey | Soft, black | A control, a card, a sheet |

## Accents

Each has a main colour, a second colour for the backdrop, and the colour
of text on it. The contrast of text on the main colour is at least 4.5 to
1 in both forms.

| Accent | Light | Dark | Second, light | Second, dark |
|---|---|---|---|---|
| Tide | `#0B74B8` | `#4DB4FF` | `#19B8B0` | `#27CFC3` |
| Ember | `#C2421D` | `#FF8A5C` | `#F5A13A` | `#FFB347` |
| Aurora | `#5B43E0` | `#A594FF` | `#22C1E6` | `#3FD0F2` |
| Moss | `#39733F` | `#86CF94` | `#A9C46C` | `#B9D67D` |
| Graphite | `#1B1D21` | `#F2F4F7` | `#8A9099` | `#6B717B` |

Text on an accent is white in light and `#0E1014` in dark.

## Status

| Token | Light | Dark |
|---|---|---|
| `success` | `#1B7F45` | `#4CD787` |
| `warning` | `#9A5B00` | `#FFB84D` |
| `danger` | `#C7352B` | `#FF6B5E` |

## Type

The typeface is Inter. The scale is in [typography](typography.md).

## Space

Spacing goes in steps of 4: 4, 8, 12, 16, 20, 24, 32, 40, 48 and 64.

## Shape

| Token | Roomy | Compact | Used for |
|---|---|---|---|
| `r-xs` | 6 | 6 | Tags and keys |
| `r-sm` | 10 | 8 | Controls |
| `r-md` | 14 | 10 | Large controls and fields |
| `r-lg` | 20 | 14 | Cards and panels |
| `r-xl` | 28 | 20 | The launcher, sheets and windows |
| `r-full` | Half the height | Half the height | Toggles and avatars |

A corner inside another follows its curve: the inner corner is the outer
one less the space between them.

## Density

| Token | Roomy | Compact |
|---|---|---|
| Height of a control | 44 | 32 |
| Height of a row | 52 | 36 |
| Padding | 16 | 12 |
| Icon | 22 | 16 |

Roomy is for touch and for the tablet. Compact is for the desktop client
and the admin panel.

## Motion

The timings are in [motion](motion.md).

## Verified and assumed

Verified on 28 November 2026, by calculation:

- Text on each accent, each accent as text on `bg`, each status colour on
  `bg` and `surface`, and `text-2` on `bg` all have a contrast of at
  least 4.5 to 1, in light and in dark.

Assumed, needing a check on real screens:

- Text on glass keeps that contrast over the strongest backdrop and over
  a photo wallpaper.

## Open questions

- In which format is the source of the tokens kept in the repository,
  and which tool generates the four themes from it? The Design Tokens
  format of the W3C community group is a candidate. This is research
  still to do.
- Agree to the first values, after seeing them in
  [the example components](examples/components.html) and the mockups.

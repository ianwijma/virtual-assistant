# Visual design

How the system looks and feels. The vision and principles are in
[the overarching design](../README.md).

Status: started. The design language has a first set of tokens, and the
main design of each client is chosen. The assistant's figure, the logo and
the remaining boards are next.

## What is being designed

One look for every screen the system has:

| Screen | Where it runs | What it must suit |
|---|---|---|
| [Desktop client](../technical/clients/desktop.md) | A launcher over the desktop, and a settings window | Speed, keyboard use, long lists |
| [Phone app](../technical/clients/mobile.md), personal | A person's phone | Touch, notifications, a quick talk to an assistant |
| [Phone app](../technical/clients/mobile.md), household | A tablet in a room, in kiosk mode | Reading from across a room, anyone using it, guests included |
| [Admin panel](../technical/clients/web-admin.md) | A browser | Many settings, logs and timelines |
| [Voice page](../technical/clients/web-voice.md) | A browser, often an old tablet | An assistant's character and a chat |
| [Described screens](../technical/a2ui.md) | Inside every client | Screens that an assistant composes |

## Decided

- **One look everywhere.** The experience is the same across the desktop
  client, the phone and tablet app, the admin panel and the voice page,
  and in any screen added later.
- **A design is reused across clients.** Where two clients do the same
  thing, they use the same design and the same controls. The voice page
  talks to an assistant the way the phone app does, and a card is the
  same card everywhere.
- **A design choice is made for every client at once.** A choice about
  how something looks, moves or behaves belongs to the design language,
  not to the client it was first drawn for. A client differs only where
  the choice cannot work on it, or where the device itself asks for
  something else. See [where clients differ](#where-clients-differ).
- **The layout follows the width of the screen, not the kind of client.**
  Every screen is responsive. A narrow screen shows one column at a
  time, a wider one two, and a wide one three. A browser window that is
  made narrow, or the phone app on a tablet, gets the layout of its
  width. This is "The layout follows the width" on
  [the width board](examples/width-board.html).
- **Recognisable as ours.** The design is distinctive, so that anyone can
  tell it is this product.
- **Frosted glass is the design language.** Apple's Liquid Glass is the
  main inspiration. See [glass](glass.md).
- **One set of design tokens** is the single source: colour, type, spacing,
  motion and assistant visuals. The theme for each platform is generated
  from it (Slint, SwiftUI, Jetpack Compose and CSS).
- **Described screens follow it too.** [A2UI](../technical/a2ui.md)
  catalog components use the same tokens.
- **Assistants have a visual.** Each assistant is a character with its own
  look. See [assistants](../technical/voice/assistants.md).
- **The product name** is chosen together with this work. "Virtual
  Assistant" is a working title.

## A fresh start

The identity starts fresh. Nothing visual is reused from the earlier voice
assistant: not its characters, not its colours, not its surfaces.

## Our own look, everywhere

Every client has our own look. No client imitates the look of the desktop
or the phone it runs on, and there is no theme that does. This replaces
the desktop brief's request to mimic the host desktop by default.

This holds on Apple's devices too. The look is inspired by Apple's, but it
is our own, and it is the same on Linux, Android and the web.

## Where clients differ

A difference between clients needs a reason that lies in the device. These
are the reasons that count:

| Reason | What may differ | Example |
|---|---|---|
| Room on the screen | Density, spacing, and how many columns are in view | The compact density on the desktop and in the admin panel, the roomy one on a phone |
| How it is operated | The size of what is touched, and what the keyboard does | Keyboard shortcuts on the desktop, larger targets for a finger |
| How far away it is read | The size of text | Text on a tablet is read from across a room |
| What the device cannot do | A simpler form of the same design | A flat tint where glass cannot be blurred |
| What only that device has | A part with no counterpart elsewhere | The launcher over other windows, the idle screen of a tablet that is always on |

Taste, habit and the order in which the clients were drawn are not
reasons. A choice that was made on one client holds on the others, in the
form that fits their screen.

The file of a client holds what is particular to it. A choice that holds
everywhere is written in the file of its subject, such as
[components](components.md) or [motion](motion.md).

## Light and dark, and no themes

- There is one look, in a light and a dark form. Each client follows the
  light or dark setting of the device it runs on.
- A person cannot choose a theme.

## The order of the work

1. **The high level:** the feel, the glass, and the colours. This is
   done; the candidates were on
   [the direction board](examples/direction-board.html).
2. **The design language:** colour, type, shape, spacing and motion,
   written as [tokens](tokens.md). A first set exists.
3. **Example components:** a few components that show the language in
   use. See [components](components.md).
4. **Low-fidelity mockups** of each client. They show layout and content,
   not polish, so that an agent can combine them with the design language.
   A first set exists, as proposals. See [mockups](mockups/README.md).

## How the work is done

- **Several designs of one thing come first.** Before many screens are
  drawn, one thing is drawn in several different ways, such as more
  glass, less glass and calmer, and the owner chooses. Only then are more
  screens drawn in the chosen way.
- **Every design question comes with an example** that shows what each
  answer would look like.
- **An example is shown one screen at a time,** so that nothing is cut
  off.
- The boards with these designs are in [examples/](examples/).

## Map of the documents

| Document | Covers | Status |
|---|---|---|
| [identity.md](identity.md) | The name, the feel, and what makes it recognisable | Started |
| [glass.md](glass.md) | The frosted glass material and where it is used | Started |
| [colour.md](colour.md) | The colours, in light and dark | Started |
| [typography.md](typography.md) | The typeface and the type scale | Started |
| [shape-and-spacing.md](shape-and-spacing.md) | Corners, density, spacing and icons | Started |
| [motion.md](motion.md) | How things move, and sound | Started |
| [assistant-visuals.md](assistant-visuals.md) | How an assistant appears and reacts to speech | Started |
| [tokens.md](tokens.md) | The full set of tokens | A first set |
| [components.md](components.md) | The shared components and how they behave | Started |
| [desktop.md](desktop.md) | The desktop client | Started |
| [phone.md](phone.md) | The phone app | Started |
| [tablet.md](tablet.md) | The household tablet | Started |
| [admin-panel.md](admin-panel.md) | The admin panel | Started |
| [voice-page.md](voice-page.md) | The voice page | Started |
| [mockups/](mockups/README.md) | The low-fidelity mockups of each client | Redrawn from the chosen designs, as proposals |
| [examples/](examples/) | The boards, to open in a browser. See the list below | |

The boards in `examples/`:

| Board | Shows | State |
|---|---|---|
| [direction-board.html](examples/direction-board.html) | Colour directions, glass strengths, backdrops and corners | Chosen from |
| [typeface-board.html](examples/typeface-board.html) | Four typefaces | Chosen from |
| [components.html](examples/components.html) | The example components, from [tokens.css](examples/tokens.css) and [components.css](examples/components.css) | To review |
| [material-board.html](examples/material-board.html) | Four designs of the material: as first drawn, more glass, calmer, closer to Apple | Chosen from |
| [launcher-board.html](examples/launcher-board.html) | The desktop launcher at four levels of see-through | Chosen from |
| [tablet-board.html](examples/tablet-board.html) | Five arrangements of the tablet around the character, and one without a figure | Chosen from |
| [name-and-logo-board.html](examples/name-and-logo-board.html) | Six name directions and six logo marks | "Hearth" chosen and later dropped; logo to a second round |
| [tablet-idle-board.html](examples/tablet-idle-board.html) | Five designs of the tablet while nobody is using it | Chosen from; a second round follows |
| [phone-home-board.html](examples/phone-home-board.html) | Five designs of the first screen of the phone app | Chosen from; a second round follows |
| [phone-talk-board.html](examples/phone-talk-board.html) | Five designs of the phone while talking to an assistant | Chosen from; a second round follows |
| [admin-layout-board.html](examples/admin-layout-board.html) | Five layouts of the admin panel, each on the Devices page | Chosen from; a second round follows |
| [admin-form-board.html](examples/admin-form-board.html) | Four designs of a settings page, each editing an assistant | Chosen from |
| [launcher-layout-board.html](examples/launcher-layout-board.html) | Five shapes of the desktop launcher | Chosen from |
| [card-board.html](examples/card-board.html) | Four designs of the card an assistant shows | Chosen from; a second round follows |
| [tablet-idle-board-2.html](examples/tablet-idle-board-2.html) | The idle tablet with glance bars and the figure, in several arrangements | Chosen from |
| [phone-screens-board.html](examples/phone-screens-board.html) | Several ways to join the main screens of the phone app | Chosen from |
| [phone-talk-board-2.html](examples/phone-talk-board-2.html) | The figure, the pop-up sheet and the switch to chat, in several designs | Chosen from |
| [admin-layout-board-2.html](examples/admin-layout-board-2.html) | Several forms of the Settings layout for the admin panel, with search | Chosen from |
| [card-board-2.html](examples/card-board-2.html) | Several ways for a row card to open | Chosen from |
| [tablet-idle-board-3.html](examples/tablet-idle-board-3.html) | The idle tablet with a bottom shelf, in several arrangements | Chosen from |
| [phone-talk-board-3.html](examples/phone-talk-board-3.html) | Talking to an assistant as a call, in several designs | Chosen from |
| [admin-layout-board-3.html](examples/admin-layout-board-3.html) | The admin panel between the Mac's Settings and three columns | Chosen from |
| [card-board-3.html](examples/card-board-3.html) | Closed cards as rows or pills, lifting into a sheet | Chosen from |
| [figure-style-board.html](examples/figure-style-board.html) | The assistant's figure in five drawing styles | Chosen from |
| [logo-board-2.html](examples/logo-board-2.html) | Four variants each of two logo marks, with the name Hearth and as app icons | Chosen from |
| [voice-page-board.html](examples/voice-page-board.html) | Four designs of the voice page for a guest | Chosen from |
| [desktop-notification-board.html](examples/desktop-notification-board.html) | Five ways a notification appears on the desktop | Chosen from |
| [admin-log-board.html](examples/admin-log-board.html) | Four designs of the request timeline in the admin panel | Chosen from |
| [setup-board.html](examples/setup-board.html) | Four designs of the first-run setup | Chosen from; a second round follows |
| [setup-board-2.html](examples/setup-board-2.html) | The first-run setup after Apple's, with the steps on top | Chosen from |
| [readability-board.html](examples/readability-board.html) | The measured contrast of text on glass, and four ways to mend it | Chosen from |
| [desktop-settings-board.html](examples/desktop-settings-board.html) | Four places for the settings of a device on the desktop | Chosen from; a second round follows |
| [desktop-settings-board-2.html](examples/desktop-settings-board-2.html) | Four ways the launcher becomes the settings view | Chosen from |
| [phone-areas-board.html](examples/phone-areas-board.html) | Four ways to reach the lists, the clipboard and the settings on the phone | Chosen from; a second round follows |
| [phone-bar-board-2.html](examples/phone-bar-board-2.html) | Four designs of the overview of all areas and of changing the bar | Chosen from |
| [states-board.html](examples/states-board.html) | Waiting, empty and out of reach, as four families | Chosen from |
| [motion-board.html](examples/motion-board.html) | Three ways a row lifts into a sheet, as stills and as a live loop | Chosen from |
| [dark-text-board.html](examples/dark-text-board.html) | Four ways to keep secondary text readable on dark glass | Chosen from |
| [icon-board.html](examples/icon-board.html) | Three open icon sets in four styles, in a tab bar, a side bar and a row | Chosen from |
| [name-board-2.html](examples/name-board-2.html) | Six names that mean home, most of them Dutch, with what a quick check found | Chosen from |
| [accent-start-board.html](examples/accent-start-board.html) | The phone's Overview in each of the five accents, light and dark | Chosen from |
| [width-board.html](examples/width-board.html) | The settings laid out by the width of the screen, or by the kind of client | Chosen from |
| [assistant-colour-board.html](examples/assistant-colour-board.html) | Whose colour a shared screen takes: the person's or the assistant's | Chosen from |
| [accent-picker-board.html](examples/accent-picker-board.html) | Three designs for choosing an accent, with the preview on four devices | Chosen from |
| [saving-board.html](examples/saving-board.html) | A changed setting applied at once, with a Save button, or both | Chosen from |
| [offline-actions-board.html](examples/offline-actions-board.html) | Four ways to show what needs the server while home cannot be reached | Chosen from |

No board is waiting to be made. New ones are added here as subjects come
up.

## Open questions

Each subject's questions are in its own document.

- Is a notification inside the phone and tablet app the same glass card
  as on the desktop, stacked in the same way? It was chosen on the
  desktop only.
- Is the overview of all areas the same on every client: the grid that
  the phone shows in a sheet, also on the tablet, the desktop and the
  web?
- Can a person set what is on the main bar on every client, as on the
  phone, or only where there is room for a few buttons?
- Is the tablet's stage the same design as the phone's call, at a larger
  size, or a design of its own?
- At which widths does the layout change? The board shows one column
  under 600, two from 600 to 1000 and three above.
- In two columns, do the destinations become a rail of icons, as on the
  board?
- Does the launcher of the desktop client, which has a fixed size, also
  follow this, or is it the one window that does not fold?
- Should a screen that an assistant composed look different from a
  built-in screen, so that a person can tell?
- Which devices are the references for the designs: which phone, which
  tablet, which monitor size?
- Are settings screens generated from each feature's description, so
  that one definition serves the phone app, the desktop client and the
  admin panel? A2UI makes this possible, but one solution may not suit
  every device. This is decided once there are visual designs of the app
  and the admin panel.

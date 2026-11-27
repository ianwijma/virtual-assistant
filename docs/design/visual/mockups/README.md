# Mockups

The low-fidelity mockups of each client. Part of
[the visual design](../README.md).

Status: a first rough set, as proposals. None is agreed yet. It was drawn
before the look of each part was chosen from several designs, so it shows
which screens exist and what is on them, not their final arrangement.

## What a mockup is

- **A mockup shows layout and content:** which regions a screen has, what
  is in them, and what matters most. It does not show polish.
- **The look comes from the design language.** Every mockup is drawn with
  the [tokens](../tokens.md) and the
  [example components](../components.md), so a change to a token changes
  every mockup.
- **Each screen has notes** under it that say what each region is and how
  it behaves. They are written for whoever builds the screen, person or
  agent.
- **A mockup is a proposal** until the owner agrees to it. What a mockup
  shows is not decided by being drawn.
- **A mockup is a web page.** Open it in a browser. It needs the internet
  once, to load the typeface.

## The mockups

| Mockup | Client | Screens |
|---|---|---|
| [desktop.html](desktop.html) | [Desktop client](../../technical/clients/desktop.md) | Launcher, results while typing, clipboard, notifications, the assistant in the launcher, the settings window, the account switch |
| [phone.html](phone.html) | [Phone app](../../technical/clients/mobile.md), personal | Set-up choice, sign-in, home, talking to an assistant, notifications, clipboard, settings, waiting for the server |
| [tablet.html](tablet.html) | [Phone app](../../technical/clients/mobile.md), household | Idle with a wallpaper, listening, an answer with a described screen, a recognised person, an approval prompt, an unrecognised voice, low power, set-up |
| [admin.html](admin.html) | [Admin panel](../../technical/clients/web-admin.md) | Devices, people, editing an assistant, appearance, the request timeline, the audit log, first-run setup, narrow width |
| [voice.html](voice.html) | [Voice page](../../technical/clients/web-voice.md) | Before sign-in, listening, a described screen, chat, without blur, microphone blocked |

The frames the screens are drawn in are in [mockup.css](mockup.css).

## Open questions

- Agree to each mockup, or say what to change in it. They were drawn
  before the designs of each client were chosen and are to be redrawn
  from the client documents.
- Desktop: how does a person go from searching to talking to the
  assistant: the Tab key, a prefix, or a shortcut of its own? The mockup
  shows Tab and a shortcut.
- Desktop: does the launcher open on the screen that holds the pointer,
  or on the main screen?
- Desktop: is the settings window opened from the launcher only, or also
  from an icon in the system tray?
- Admin panel: the request timeline shows the first words a person
  said. Who may see them?
- Admin panel: is "Undo" offered for every change in the audit log, or
  only for changes that can be reversed safely?
- Voice page: does the page remember on that browser that it was set up
  as a personal or a household device?

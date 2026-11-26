# Desktop client

The application on a person's computer. Part of
[the clients design](README.md).

Status: draft.

## What it is

One launcher application in the style of Raycast, opened by a global
hotkey, with views inside it. It is a personal device: it belongs to one
person and is an extension of the rest of the household's system.

## Accounts

A computer can hold more than one account. A person switches between them
with a short passcode. The accounts can belong to different people in the
household, or to one person on different servers, such as a home server
and a work server. See
[identity and sharing](../server/identity-and-sharing.md).

## Views and features

- **Launcher:** start applications and reach everything else.
- **Window control:** control the windows of other applications.
- **Clipboard:** history, search and sync. See
  [clipboard](../server/clipboard.md).
- **Notifications:** see and act on notifications. The desktop is the
  notification service of the machine: it shows local notifications at
  once and forwards them to the server. See
  [notifications and routing](../server/notifications-and-routing.md).
- **Assistant:** the desktop is a voice device by default. A person can
  summon an assistant by wake word, let it listen always, or type to it.
  Each person chooses. See [voice](../voice/README.md).
- **Settings:** the settings of this device, in a macOS-style window with
  groups on the left and the selected group on the right. A person's own
  settings open in the [admin panel](web-admin.md), through a link that
  is already signed in.

## Requirements

- **Speed is the key property.** It starts fast, and everything we control
  feels instant. Only AI, background work and outside services may take
  longer. "Snappy" is to be defined in numbers, with tests that stop the
  application getting slower.
- **Scale.** Lists of hundreds of thousands of items, with fast search.
- **Shortcuts.** Everything the launcher can do is a named command: open
  a view, start an application, a window action, talk to the assistant,
  paste a clipboard item. A person can bind any command to a global
  keyboard shortcut. A new feature adds commands, and they can be bound
  at once.
  Shortcuts are per device: they are set on that device and kept there,
  not on the server, so each computer has its own. A shortcut can start
  an action that needs the server. The action then talks to the server
  and shows a loader, or a similar sign that it is waiting.
- **Setup.** A light first-run setup that infers as much as possible from
  the machine.
- **Platforms.** Linux first, on most desktops, on both X11 and Wayland.
  The owner's machine runs Pop!_OS from before the COSMIC desktop. macOS
  and Windows come after the first release.

## Without the server

The launcher, window control, the local clipboard history and anything
already synced keep working. The assistant, voice and anything that
involves another device wait for the server, and show that they are
waiting.

## Where its data lives

| Data | Lives |
|---|---|
| Launcher index, keyboard shortcuts, window control | On the desktop |
| Clipboard | Captured locally, stored on the server, indexed locally |
| Notifications, settings | On the server, cached locally |

With the server down, it keeps working from its cache, read-only for
server data.

## Toolkit

Slint, under GPLv3. The first build task is a list of 100,000 items,
limited to two days, with a written pass or fail threshold. If it fails,
the fallback is iced, which lacks accessibility for now.

## Verified and assumed

Assumed, needing a build to confirm:

- Slint meets the speed target with 100,000 items.

## Speed targets

These are targets to tune against, measured with a simple benchmark. They
are not gates.

| Moment | Target |
|---|---|
| The launcher appears after its shortcut | 100 ms |
| Results update after a key press, over 100,000 items | 50 ms |
| Cold start of the client | 1 second |

## Open questions

- Where the wake word is detected on a desktop.
- How notifications, clipboard access, global hotkeys and window control
  work across Linux desktops on X11 and Wayland. This is research still to
  do, and the limits on Wayland are a known risk.

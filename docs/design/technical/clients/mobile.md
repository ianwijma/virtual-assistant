# Phone and tablet app

The app for phones and tablets, in personal use and as a household voice
device. Part of [the clients design](README.md).

Status: draft. Android is in the first release. iOS follows after it and
is planned for from the start.

## Two uses

| Use | Device | What it does |
|---|---|---|
| Personal | A person's phone | Their notifications, shared clipboard and assistants. It also receives household events, such as a broadcast, and can be targeted directly |
| Household | A tablet in a room, in kiosk mode | A voice device for everyone, with a screen |

A second-hand tablet is the intended household device: an iPad or an
Android tablet, set up once and left running.

## Household use

- **Android:** the app can keep listening for the wake word with the
  screen off.
- **iPad:** the app listens while it is open in the foreground, so it runs
  as a kiosk.
- **Low-power mode:** a black screen at minimum brightness, waking on
  voice or touch. A black screen alone saves power only on OLED screens.
- **A browser** is the fallback for a tablet too old for the app. See
  [voice page](web-voice.md).

## Personal use

- The phone cannot read the clipboard in the background. It uses a share
  action, a shortcut or a keyboard. See
  [clipboard](../server/clipboard.md).
- Remote access uses the installed Tailscale app first. See
  [networking](../server/networking.md).

## How it is built

Native shells (Jetpack Compose on Android, SwiftUI on iOS) over the shared
Rust core, joined by generated bindings (UniFFI). Official A2UI renderers
exist for both.

## Open questions

- One app with a household mode, or two apps: a household app and a
  personal app?
- Who may turn a device into a household device.
- How a person signs in on their phone. See
  [identity and sharing](../server/identity-and-sharing.md).
- How notifications reach a phone when the app is closed, without a cloud
  push service.
- Building and publishing for iOS needs a Mac and an Apple developer
  account, and the App Store has friction with the GPL.

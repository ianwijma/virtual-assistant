# Clients

The overview of the devices, apps and web pages that connect to the
server. Part of [the technical design](../README.md).

Status: draft.

## The clients

| Client | Document | Kind of device | First release |
|---|---|---|---|
| Desktop client | [desktop.md](desktop.md) | Personal | Linux; macOS and Windows after |
| Phone and tablet app | [mobile.md](mobile.md) | Personal, or household in kiosk mode | Android; iOS after, planned for |
| Admin panel | [web-admin.md](web-admin.md) | A web application | Yes |
| Voice page | [web-voice.md](web-voice.md) | A light web page | Yes |

## Rules for every client

- **It is a device of the server.** It holds one connection, sends events
  up and offers abilities down. See [protocol](../server/protocol.md).
- **It is never blocked by the server.** It writes locally first and syncs
  in the background. See [data and sync](../server/data-and-sync.md).
- **It shares one Rust core** with the other clients: protocol, sync,
  storage, module logic and voice.
- **The UI layer is chosen per platform,** for the best integration with
  that platform and for speed.
- **It has the same look** as the others. See
  [the visual design](../../visual/README.md).
- **It has "Report a bug" and "Suggest a feature".** See
  [feedback](../modules/feedback.md).
- **It can be a voice device.** See [voice](../voice/README.md).

## Toolkits

| Client | UI | Why |
|---|---|---|
| Desktop | Slint, in Rust | The most mature native Rust toolkit, with accessibility |
| Phone and tablet | Native shells (Jetpack Compose, SwiftUI) over the Rust core | Share actions, keyboards and notification extensions are normally written natively, and official A2UI renderers exist |
| Admin panel | Rust compiled to WebAssembly (Leptos) | Keeps the web in Rust |
| Voice page | A small web page | It only relays audio |

A wrong toolkit choice affects the UI layer only. The core and the
modules are untouched.

## Open questions

- Is the phone and tablet app one app with a household mode, or two apps?
- Which features of each client must work with no server at all.

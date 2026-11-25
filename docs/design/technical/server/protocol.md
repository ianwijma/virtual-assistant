# Protocol

How devices and the server talk. Part of [the server design](README.md).

Status: draft. The message set is not designed yet.

## Design

- Every device holds one WebSocket connection to the server.
- Message types live in the `protocol` crate, which every Rust binary
  imports. Swift and Kotlin shells get them through generated bindings.
- A device acts as a node of the server:
  - it **sends events up**, such as a copied item or a desktop
    notification;
  - it **offers abilities down**, such as showing a screen, controlling
    windows or playing media.
- A plain command is preferred over a described screen when the device has
  a native way to do the job. "Play this URL" is a command. See
  [A2UI](../a2ui.md).

## Device capabilities

The server keeps a record of what each device can do.

- A device states its capabilities when it is registered, and again
  whenever it is updated or they change.
- Examples: it has a screen, it can draw A2UI and which catalog it
  supports, it has a microphone, it has a speaker, it can play media, it
  can control windows.
- The capabilities of the device in use are sent to the AI model with a
  request, so the reply fits the device. For example, the model composes
  an [A2UI](../a2ui.md) screen only when the device can draw one, and
  otherwise answers in words to be spoken.
- The server uses the same record to decide what it may send to a device,
  such as a command or a notification with actions.
- A device needs a screen or voice to be used with an assistant. One with
  neither cannot be interacted with.

## Pairing

- A native app pins the server's key when it is paired.
- A device remembers the server's home-network address and its remote
  address, and tries the home network first. See
  [networking.md](networking.md).

The earlier voice assistant paired its voice boxes with a one-time code,
after which the server stored only a hash of the device's credential. That
flow is a candidate here.

## Open questions

- The full list of messages, and how the protocol is versioned.
- How audio travels: on the same connection or a separate one.
- The exact pairing steps for a personal device and for a household
  device. See [identity-and-sharing.md](identity-and-sharing.md).
- The full list of capabilities, and how a catalog version is expressed.

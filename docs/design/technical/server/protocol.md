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
  supports, it shows the assistant's character, it has a microphone, it has a
  speaker, it can play media, it
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

See [pairing](pairing.md).

## The messages

One WebSocket connection per device carries everything. Control
messages are JSON text, which is easy to read while the system is young.
Audio travels on the same connection as binary frames.

| Group | From device to server | From server to device |
|---|---|---|
| Session | Hello, with protocol version, device and capabilities | Welcome, or "update needed" |
| Sync | Events from the outbox; how far it has read | New events; confirmation of received events |
| Notifications | A local notification; an action on a notification | A notification to show or speak; a change of its state |
| Commands | The result of a command | A command to carry out, such as "play this" or "open this" |
| Voice | A wake word report with how well it was heard; audio; "stopped talking" | The device's new state; speech audio; tag events |
| Screens | What the person did on a described screen | A screen to show; new data for it |
| Sign-in | Email address, code, invite | Credential; "waiting for approval" |
| Health | Ping | Pong |

Every command carries a number, and its result carries the same number.

## Proposal: versions

- The hello message carries one protocol version number.
- Adding a message or a field does not change the number. Devices ignore
  what they do not know.
- A change that breaks older devices raises the number. The server speaks
  the current number and the one before it.
- A device that is too old is told to update, and shows that.

## Proposal: the list of capabilities

| Capability | Meaning |
|---|---|
| Screen | It can show things |
| A2UI | It can draw described screens, with the catalog version it knows |
| Character | It shows the assistant's character |
| Text input | It can be typed to |
| Microphone | It can hear |
| Speaker | It can speak and ring |
| Wake word on the device | It detects the wake word itself; otherwise it streams audio |
| Media | It can play audio and video |
| Notifications: source | It forwards notifications from local applications |
| Notifications: actions | It can carry out a reply or an "open" for its own notifications |
| Clipboard | It captures and restores clipboard items |
| Window control | It can control other applications' windows |
| Start applications | It can open an application or a link |
| Always on | It is expected to stay on, such as a tablet in kiosk mode |

The catalog version is one number. The server sends a device only
components that its version knows.

## Open questions

- Agree to the proposed versions and capabilities, or correct them.
- Whether audio on the same connection is fast enough, or needs its own.
  To be measured when the first voice device exists.
- Whether JSON is fast enough for sync of large histories, or a compact
  format is needed.

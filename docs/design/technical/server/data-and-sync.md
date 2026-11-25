# Data and sync

Where each kind of data lives and how it moves between the server and
devices. Part of [the server design](README.md).

Status: draft.

## Where data lives

The server is the default home for everything. Something lives on a device
only if it is tied to that machine or must respond within a frame.

| Data | Lives | Notes |
|---|---|---|
| People, roles, shares, routing, credentials, settings | Server | Devices keep a read-only copy |
| Notifications | Server | A desktop is a source and a display |
| Email | Server | Devices keep a cache for reading and search |
| Clipboard | Captured on the device, stored on the server | The device keeps a local index |
| Launcher index, hotkeys, window control | Desktop | Tied to the machine |

## Local first, then sync

Every action on a device follows the same path, so the server is never on
the fast path:

1. Write to the local store and update the screen at once.
2. Put the change in a local outbox.
3. Send the outbox to the server in the background.
4. If the server cannot be reached, the outbox waits and empties on
   reconnect.

## The sync model

- One append-only event log per person, with sequence numbers.
- Each device remembers how far it has read and catches up from there.
- Most data is only ever added (clipboard items, notifications, emails),
  so there are few conflicts.
- Settings use last-writer-wins.

## When the server is down

A device keeps working from its cache. Server data is read-only until the
connection returns.

## Open questions

- How the log handles household data that several people can see.
- How long history is kept, and how old events are trimmed.
- What happens to a person's data when they are removed.
- How search stays fast over years of history. This is research still to
  do.
- Whether there is any data to bring over from the earlier voice
  assistant.

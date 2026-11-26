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
| Clipboard | Captured on the device, stored on the server | The device keeps a local index |
| New email | Server | Kept for a week by default |
| Launcher index, keyboard shortcuts, window control | Desktop | Tied to the machine; shortcuts are per device |

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
- Most data is only ever added (clipboard items, notifications),
  so there are few conflicts.
- Settings use last-writer-wins.

## Removing data

Removing a person is a soft deletion. Their data is marked as removed and
is never erased. See [identity and sharing](identity-and-sharing.md).

## When the server is down

A device keeps working from its cache. Server data is read-only until the
connection returns.

## How long history is kept

History is kept forever by default: clipboard items, notifications and
other events. A person or an admin can set a limit per kind, such as 90
days for the clipboard.

## Nothing is migrated

The system starts empty. No data is brought over from the earlier voice
assistant.

## Proposal: data that several people can see

This section is proposed and waits for the owner's review.

- Besides one log per person, there is **one log for the household**.
- **Every event belongs to exactly one log:** its owner's, or the
  household's. A shopping list lives in the household log. A person's
  notification lives in theirs.
- **A share does not copy anything.** When a person shares an item with
  someone, the events stay in the owner's log, and a share record says
  who else may read them.
- **A device follows several logs,** each with its own position:

  | Device | Follows |
  |---|---|
  | A personal device | Its person's log, the household log, and what is shared with that person |
  | A household device | The household log only |

- **Ending a share** tells the other person's devices to drop what they
  held of it.
- A household device gets a person's own data only for the length of a
  request that person made with a recognised voice. It does not keep it.

## Open questions

- Agree to the proposal for data that several people can see, or correct
  it. Whether following several logs is simple enough is checked together
  with the choice of database.
- How search stays fast over years of history. This is research still to
  do.

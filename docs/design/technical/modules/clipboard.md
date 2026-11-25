# Clipboard module

Clipboard history on a device, and a clipboard shared between a person's
devices. Part of [the modules design](README.md).

Status: draft.

## Design

- **Capture and paste are local and instant.** Sync follows in the
  background.
- **Shared between a person's devices.** The newest item is pushed to
  their other devices. History and large items are fetched when needed.
- **History is stored on the server.** The device keeps a local index for
  search.
- **Password-manager copies are not synced** by default.
- **Phones** cannot read the clipboard in the background. They use a share
  action, a shortcut or a keyboard.

## Requirements from the desktop brief

- Each item has a rich representation of what was copied. Copied HTML is
  drawn, in a safe way.
- Hundreds of thousands of items, such as years of history, with search
  that stays fast.
- Restoring an item to the clipboard never blocks the application the
  person is in, and the person is told when it is done.

## Open questions

- Is clipboard sync on by default, and between which devices?
- How large items, such as images and files, are handled.
- How untrusted HTML is drawn safely.
- How search stays fast over years of history.
- How long history is kept.

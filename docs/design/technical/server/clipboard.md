# Clipboard

Clipboard history on a device, and a clipboard shared between a person's
devices. Part of [the server design](README.md).

Status: draft.

## Design

The clipboard is a feature of the system. A
[module](../modules/README.md) can give assistants tools to use it.

- **Capture and paste are local and instant.** Sync follows in the
  background.
- **Shared between a person's devices, and on by default.** The newest
  item is pushed to their other devices.
- **Clipboard content is sensitive, so it is encrypted** where it is
  stored and while it travels between devices.
- **History is kept forever by default.** A limit can be set. History and large items are fetched when needed.
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

- How far the encryption goes. If only the person's own devices can read
  their clipboard, the server cannot search it, an assistant cannot use
  it, and an admin cannot read it. Which of these is wanted?
- How large items, such as images and files, are handled.
- How untrusted HTML is drawn safely.
- How search stays fast over years of history.

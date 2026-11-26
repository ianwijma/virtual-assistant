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
- **Clipboard content is sealed.** It is encrypted on the person's
  devices, and only they can read it. The server stores it and passes it
  on. See [vault](vault.md).
- **An assistant can use it, after asking.** It asks whether it may
  search the clipboard and explains why. The person approves on one of
  their devices, which then supplies the content.
- **Search happens on the device,** in its local index, because the server
  cannot read the content.
- **Text syncs at once; a large item is fetched when needed.** An image
  or a file is sealed and uploaded in the background. Another device
  downloads it only when the person picks it. An item above a size limit,
  such as 50 MB, stays on the device it was copied on.
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

- How copied HTML is drawn with its formatting, safely, on each platform.
  A browser can isolate it in a sandboxed frame; what the Rust desktop
  client and the phone apps can use has to be found out. This is research
  still to do.
- How search stays fast over years of history.

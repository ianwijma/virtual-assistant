# Lists

Lists kept by the system, such as a shopping list, and things a person
asks an assistant to remember. Part of [the server design](README.md).

Status: draft. Only the outline is decided.

## Design

- Lists are a system feature in the first release. Their data lives on
  the server.
- **An entry is like a note in Google Keep.** It is either a list of
  items that can be ticked off, or plain text.
- Lists are shown and edited in every client, as a screen described with
  [A2UI](../a2ui.md).
- A lists [module](../modules/README.md) gives an assistant the tools to
  use them, such as adding an item or reading a list out.
- "Remember this for me" is handled here, and is saved as a plain text
  entry. It is how an assistant keeps
  something across conversations, because it has no memory of its own
  for now. See [assistants](../voice/assistants.md).
- A list is a household thing by default and is shared with everyone. A
  person can make one of their lists private. See
  [identity and sharing](identity-and-sharing.md).

## Open questions

None at the moment.

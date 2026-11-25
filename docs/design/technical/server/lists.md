# Lists

Lists kept by the system, such as a shopping list, and things a person
asks an assistant to remember. Part of [the server design](README.md).

Status: draft. Only the outline is decided.

## Design

- Lists are a system feature in the first release. Their data lives on
  the server.
- A lists [module](../modules/README.md) gives an assistant the tools to
  use them, such as adding an item or reading a list out.
- "Remember this for me" is handled here. It is how an assistant keeps
  something across conversations, because it has no memory of its own
  for now. See [assistants](../voice/assistants.md).
- A list is a household thing by default and is shared with everyone. See
  [identity and sharing](identity-and-sharing.md).

## Open questions

- What a list can hold: plain items, amounts, check marks, notes?
- Is "remember this" a list like any other, or a separate kind of note?
- Where lists are shown and edited in each client.

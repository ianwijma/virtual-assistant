# Modules

The overview of the module system, and the list of modules. Part of
[the technical design](../README.md).

Status: draft. The module system is not designed yet, and the list of
modules for the first release is not decided.

## What a module is

A module adds one feature to the system. It reaches across the parts: it
has a server part and optional parts on the clients, declared together.

A module can declare:

- events it produces and listens to;
- tools that [assistants](../voice/assistants.md) may use;
- settings, with a screen for each;
- screens in the clients, including its own page in the
  [admin panel](../clients/web-admin.md);
- [A2UI](../a2ui.md) catalog components;
- actions a person can bind to a keyboard shortcut.

## Rules

- **Adding a module must be easy.**
- **Modules are internal.** People extend the system by forking the
  repository and adding modules. There is no plugin system.
- **Each module has its own design document** in this folder. A module
  that needs several files gets its own folder.

## Modules

| Module | Document | State |
|---|---|---|
| Feedback | [feedback.md](feedback.md) | Among the first modules |
| Email | [email.md](email.md) | In scope |
| Clipboard | [clipboard.md](clipboard.md) | In scope |

Notifications and routing are part of the server core, not a module. See
[notifications and routing](../server/notifications-and-routing.md).

## What exists to draw on

The earlier voice assistant has about 21 modules and a full module
contract. Ideas worth keeping from it:

- one gateway that every tool call passes, which checks who is acting,
  whether the module is on, and the risk of the tool;
- settings screens generated from a description, where each page states
  where it belongs;
- typed services between modules, instead of modules calling each other;
- a spoken fallback for everything visual.

Its module host grew to 3,600 lines and its reviews did not converge, so
the contract here should start smaller. See
[the reference](../../../reference/existing-voice-assistant.md) for its
list of modules.

## Open questions

- Which modules are in the first release.
- The module contract: exactly what a module declares and how it is
  registered.
- Where a module's screens appear on each client.
- How a module stores data, and how that data is scoped to a person or
  the household.
- How modules hold accounts and sign-ins to outside services.
- Whether Home Assistant integration is in the first release.

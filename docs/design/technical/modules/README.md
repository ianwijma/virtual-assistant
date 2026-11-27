# Modules

What a module is, and the list of modules. Part of
[the technical design](../README.md).

Status: draft. The first modules are named; none is designed in detail
yet.

## What a module is

A module is a set of tools that an AI agent can call, grouped around one
subject. It is both the grouping and the place where those tools are
written.

- **A tool does one thing,** such as "send a test notification to this
  device" or "add a reminder".
- **A module covers a subject.** A kitchen module, for example, would
  manage the pantry ("five kilos of rice") and find recipes. It would have
  one tool that fetches what is in the pantry and one that finds recipes
  that can be made with it.
- **A core feature stays in the system.** Notifications are a core part of
  the server; a module only adds the tools through which an agent uses
  them.
- **The shared, complicated parts stay in the system:** storage, settings
  and their screens, sync, routing, permissions and sign-ins to outside
  services. A module uses these; it does not build its own.
- **A tool is written in one module** and belongs to that module only.
- **Modules belong to assistants, not to devices.** A device gets them
  through the assistants assigned to it.
- **A module is given whole.** An assistant has all of a module's tools or
  none of them, for now. Switching single tools off may come later.
- **The same module can be given to several assistants.** This is how
  assistants with different purposes are made, as in the earlier voice
  assistant. See [assistants](../voice/assistants.md).

```text
assistant  --has-->  modules  --contain-->  tools  --call-->  the system
"Jeff"               notifications          send a test       notification
                     reminders              notification      centre
```

## Rules

- **Adding a module must be easy.** It is a list of tools, each with a
  name, a description for the AI model, its inputs and the system call it
  makes.
- **A new feature is built into the system first, and its data lives on
  the server.** Timers, a shopping list or a pantry become part of the
  system, with their own screens, such as a bulk import of pantry items
  or an import from a supermarket's order email. A module then exposes
  that feature to an assistant as tools.
- **Switching a module off loses nothing.** The data stays in the system,
  and other modules keep working.
- **Modules are not keyboard shortcuts.** Shortcuts belong to a device.
  See [desktop](../clients/desktop.md).
- **Modules are internal.** People extend the system by forking the
  repository and adding modules. There is no plugin system.
- **A tool acts as the person the assistant is talking to.** It can do
  only what that person may do. See
  [identity and sharing](../server/identity-and-sharing.md).
- **A tool fits the device.** The agent knows the device's
  [capabilities](../server/protocol.md), so a tool's result can be shown
  or spoken.
- **Each module has its own document** in this folder once it is
  designed: its tools, and the part of the system each one uses.

## First release

The first release has a small set of base modules. More follow once the
overall system and these are in place.

| Module | Its tools |
|---|---|
| Feedback | Report a bug, suggest a feature |
| Notifications | Send a notification or an announcement to a person or a device |
| Timers and reminders | Set, list and cancel timers, alarms and reminders |
| Lists | Add to, read and change lists; remember something on request |
| Device control | Act on a device, such as showing something on its screen or opening an app |

There is no Home Assistant integration in the first release. It may be
reconsidered later. The preference is that, when smart-home control is
added, the system talks to those devices and services itself. Home
Assistant's code can serve as an example of how a given system is spoken
to.

The set may grow before the first release. Each of these needs its system
feature to exist first.

## What exists to draw on

The earlier voice assistant has about 21 modules. There a module carries
its own settings, storage, screens and scheduled work, and its module host
grew to 3,600 lines. Defining a module as tools only avoids that.

Ideas worth keeping from it:

- one gateway that every tool call passes, which checks who is acting,
  whether the assistant has the module, and the risk of the tool (read,
  change, message, money, security);
- a tool marked as read-only can run early, while the person may still be
  talking. See [speech to text](../voice/speech-to-text.md).

See [the reference](../../../reference/existing-voice-assistant.md) for
its list of modules.

## Open questions

None at the moment.

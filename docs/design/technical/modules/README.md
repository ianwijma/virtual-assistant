# Modules

What a module is, and the list of modules. Part of
[the technical design](../README.md).

Status: draft. The list of modules for the first release is not decided.

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
- **Modules are given to assistants.** Each
  [assistant](../voice/assistants.md) has the modules it may use, and the
  same module can be given to several assistants. This is how assistants
  with different purposes are made, as in the earlier voice assistant.

```text
assistant  --has-->  modules  --contain-->  tools  --call-->  the system
"Jeff"               notifications          send a test       notification
                     reminders              notification      centre
```

## Rules

- **Adding a module must be easy.** It is a list of tools, each with a
  name, a description for the AI model, its inputs and the system call it
  makes.
- **A new feature is built into the system first.** Timers or a shopping
  list become part of the system, and a module then adds the tools for
  them.
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

## Modules

None are designed yet. The system features that modules will expose first:

| System feature | Document | Example tools |
|---|---|---|
| Notifications | [notifications and routing](../server/notifications-and-routing.md) | Send a notification to a device; read out unread notifications |
| Feedback | [feedback](../server/feedback.md) | File a bug report; suggest a feature |
| Email | [email](../server/email.md) | Summarise new email; read an email |
| Clipboard | [clipboard](../server/clipboard.md) | Send this to my other device |

The example tools are illustrations, not decisions.

## First release

The first release has a small set of base modules. More follow once the
overall system and these are in place.

| Module | Its tools |
|---|---|
| Feedback | Report a bug, suggest a feature |
| Notifications | Send a notification or an announcement to a person or a device |
| Timers and reminders | Set, list and cancel timers, alarms and reminders |
| Device control | Act on a device, such as showing something on its screen or opening an app |

There is no Home Assistant integration. When smart-home control is
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

- Where does a module's own data live, such as a kitchen module's pantry:
  is the pantry a system feature that is built first, or data the module
  keeps through the system's storage?
- A lists module, for lists and things a person asks the assistant to
  remember: is it in the first release, and is a list private or shared
  with the household by default?
- Timers, alarms and reminders are a system feature with no design
  document yet. What do they cover, and where do they ring?
- Can an assistant be given a module with some of its tools switched off?

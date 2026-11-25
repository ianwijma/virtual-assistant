# Server

The overview of the server: what it is responsible for and which documents
describe each responsibility. Part of
[the technical design](../README.md).

Status: draft.

## What the server is

The server is the hub of the system and its core. It runs on a box in the
home, on the home network, and needs no internet. It is written fresh in
Rust as one self-contained binary that also runs on low-power ARM.

Every other part is a device of the server: the desktop client, the phone
and tablet app, the admin panel and the voice page.

## Responsibilities

| Responsibility | Document |
|---|---|
| The connection to every device and the messages on it | [protocol.md](protocol.md) |
| Storing data and syncing it to devices | [data-and-sync.md](data-and-sync.md) |
| People, devices, roles and sharing | [identity-and-sharing.md](identity-and-sharing.md) |
| The notification centre and its routing | [notifications-and-routing.md](notifications-and-routing.md) |
| The AI providers behind assistants | [ai-providers.md](ai-providers.md) |
| Home network, remote access and certificates | [networking.md](networking.md) |
| Assistants, summoning and speech | [../voice/README.md](../voice/README.md) |
| Feedback: bug reports and feature suggestions | [feedback.md](feedback.md) |
| Email | [email.md](email.md) |
| Clipboard history and sharing | [clipboard.md](clipboard.md) |
| Lists, and remembering on request | [lists.md](lists.md) |
| Timers, alarms and reminders | [timers.md](timers.md) |
| Credentials and other secrets | [vault.md](vault.md) |
| Modules: the sets of tools given to assistants | [../modules/README.md](../modules/README.md) |
| Screens sent to devices | [../a2ui.md](../a2ui.md) |

## One server per household

A household has one server. Another household, or a workplace, runs its
own separate server, and a person has an account on each. Linking servers
together is not needed for now.

## Rules for the server

- **It is the default home for data.** See
  [data-and-sync.md](data-and-sync.md).
- **Devices never wait for it.** A device works from its local copy and
  syncs in the background.
- **Features live here, not in modules.** Storage, settings, sync and
  sign-ins to outside services are part of the system. A module only adds
  tools an AI agent can call.
- **Every setting has a screen** in the
  [admin panel](../clients/web-admin.md). There are no configuration files
  for users.

## What it runs on

For the first release the server runs on Linux, on both ARM and x86
processors. That covers small boards such as a Raspberry Pi, and ordinary
home servers and mini PCs.

## Open questions

- How it is installed and updated: a single binary, a container image, a
  package?
- How backups are made and restored.
- Which database the server uses.

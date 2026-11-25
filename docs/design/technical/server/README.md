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
| The module system and each module | [../modules/README.md](../modules/README.md) |
| Screens sent to devices | [../a2ui.md](../a2ui.md) |

## Rules for the server

- **It is the default home for data.** See
  [data-and-sync.md](data-and-sync.md).
- **Devices never wait for it.** A device works from its local copy and
  syncs in the background.
- **Every setting has a screen** in the
  [admin panel](../clients/web-admin.md). There are no configuration files
  for users.

## Open questions

- What the server runs on for the first release: a home server, a
  Raspberry Pi, a container? Which processor types?
- How it is installed and updated: a single binary, a container image, a
  package?
- How backups are made and restored.
- Whether a household has exactly one server, and whether a person can
  belong to more than one household.
- Which database the server uses.

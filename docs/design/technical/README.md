# Technical design

The overview of how the system is built, and a map of the documents that
describe each part. The vision and principles are in
[the overarching design](../README.md).

Status: draft. Nothing here is built yet.

## The parts

```text
                 Household server (home network)
                 |                           |
        household devices             personal devices
        tablet in kiosk mode          desktop client
        voice page                    phone app
                                      admin panel
```

- The **server** is the hub. It holds people, devices, data, routing,
  assistants, AI and modules.
- Every **client** is a device of the server. It holds one connection,
  sends events up and offers abilities down.
- **Voice** runs through the server: summoning, speech and the assistants
  themselves.
- A **module** is a set of tools an AI agent can call. The features
  behind the tools are part of the system. Assistants are given modules.
- Everything is written in Rust in one repository, with native shells only
  where a platform needs them.

## Map of the documents

| Area | Start here | Documents |
|---|---|---|
| Server | [server/README.md](server/README.md) | [protocol](server/protocol.md), [pairing](server/pairing.md), [data and sync](server/data-and-sync.md), [identity and sharing](server/identity-and-sharing.md), [notifications and routing](server/notifications-and-routing.md), [AI providers](server/ai-providers.md), [networking](server/networking.md), [feedback](server/feedback.md), [email](server/email.md), [clipboard](server/clipboard.md), [lists](server/lists.md), [timers](server/timers.md), [vault](server/vault.md) |
| Voice | [voice/README.md](voice/README.md) | [assistants](voice/assistants.md), [summoning](voice/summoning.md), [wake word](voice/wake-word.md), [speaker identification](voice/speaker-identification.md), [speech to text](voice/speech-to-text.md), [text to speech](voice/text-to-speech.md), [reply tags](voice/reply-tags.md) |
| Modules | [modules/README.md](modules/README.md) | None yet; the first five are named there |
| Clients | [clients/README.md](clients/README.md) | [desktop](clients/desktop.md), [mobile](clients/mobile.md), [admin panel](clients/web-admin.md), [voice page](clients/web-voice.md) |
| Screens sent to devices | [a2ui.md](a2ui.md) | |
| Project | | [repository layout](repository.md), [licensing and hardware](licensing-and-hardware.md) |

How the system looks is in [the visual design](../visual/README.md).

## First release

| Piece | First release | After it |
|---|---|---|
| Server | Yes | |
| Admin panel | Yes | |
| Voice page | Yes | |
| Desktop client | Linux, on X11 and Wayland | macOS, then Windows |
| Phone and tablet app | Android | iOS, planned for from the start |
| System features | Notifications, feedback, lists, timers and reminders, clipboard, new-email notifications, device control | Smart-home control, sealed data and a password manager, a children's role |
| Speech | Local by default; Deepgram, ElevenLabs and Cartesia as cloud options; English | Other languages, speech on devices |

There is no roadmap yet. The technical details are made clear first, and
the build order is decided after that.

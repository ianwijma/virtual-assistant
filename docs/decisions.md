# Decisions

The log of what was decided, newest last. Every decision here is also
written into the design document it belongs to, which is named after it.
The design is what to read to learn how the system works; this log shows
what was decided and in what order.

"Thread" means
[the design conversation](sources/design-thread-2026-11-25.md). All dates
are 25 November 2026.

## From the thread

| # | Decision | Written into |
|---|---|---|
| 1 | One system, not two: the server is the hub and every client is a device | [design](design/README.md) |
| 2 | The server runs on the home network and needs no internet | [design](design/README.md), [server](design/technical/server/README.md) |
| 3 | The server is the default home for data; clients write locally first and are never blocked by it | [data and sync](design/technical/server/data-and-sync.md) |
| 4 | Notifications are server-first; the desktop is a source and a display | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 5 | Private by default; roles are admin, member and restricted; an admin can read all data for now, and that access is logged | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 6 | Home network only by default; remote access is opt-in through Tailscale | [networking](design/technical/server/networking.md) |
| 7 | One monorepo, Rust first; another language only for UI and platform glue | [design](design/README.md), [repository](design/technical/repository.md) |
| 8 | No open-ended prototyping; risky choices sit behind boundaries | [design](design/README.md) |
| 9 | The server is written fresh; the earlier voice assistant is a reference, and its summoning rules are not copied | [design](design/README.md), [summoning](design/technical/voice/summoning.md) |
| 10 | AI is part of the core; providers from day one are Claude Code, Codex, OpenRouter and Ollama | [AI providers](design/technical/server/ai-providers.md) |
| 11 | A2UI is core, in three tiers: commands, catalog components, generated surfaces | [A2UI](design/technical/a2ui.md) |
| 12 | Every app has built-in bug reports and feature suggestions, filed as GitHub issues through the server | [feedback](design/technical/server/feedback.md) |
| 13 | One visual identity across all apps, from one set of design tokens | [visual design](design/visual/README.md) |
| 14 | Two web clients: a full admin panel and a light voice page | [clients](design/technical/clients/README.md) |
| 15 | Summoning includes identifying the speaker, so permissions follow the person | [summoning](design/technical/voice/summoning.md) |
| 16 | Toolkits: Slint for the desktop, native shells on phones, Rust compiled to WebAssembly for the admin panel | [clients](design/technical/clients/README.md) |
| 17 | The project is open source and earns money by selling hardware later | [licensing and hardware](design/technical/licensing-and-hardware.md) |

## From planning

| # | Decision | Written into |
|---|---|---|
| 18 | The licence is GPLv3, not AGPLv3 | [licensing and hardware](design/technical/licensing-and-hardware.md) |
| 19 | A clean rewrite: nothing is ported from the earlier voice assistant | [design](design/README.md) |
| 20 | The repository holds documents only for now | [repository](design/technical/repository.md) |
| 21 | The plan lives in the repository as Markdown, not in GitHub issues | [repository](design/technical/repository.md) |
| 22 | "Virtual Assistant" is a working title, with `va-` as a neutral prefix | [repository](design/technical/repository.md), [visual design](design/visual/README.md) |
| 23 | Pull requests go into `develop`; `main` receives releases | [repository](design/technical/repository.md) |
| 24 | First release: server, admin panel, voice page, Linux desktop client and Android app; macOS, Windows and iOS follow | [technical design](design/technical/README.md) |
| 25 | The desktop client is one launcher in the style of Raycast, with views for applications, window control, clipboard and notifications | [desktop](design/technical/clients/desktop.md) |
| 26 | Voice providers are modular and configurable, local and cloud; English first | [voice](design/technical/voice/README.md) |
| 27 | Feedback is among the first features and has a screen in the admin panel | [feedback](design/technical/server/feedback.md) |
| 28 | No code is written until the functionality and the interactions are agreed | [repository](design/technical/repository.md) |
| 29 | Two kinds of device: household, used by everyone, and personal, for one person; a personal device still receives household events | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 30 | Each person configures their own notification routing, including by schedule; an admin can view and change it; the nearest device is not guessed | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 31 | The desktop client is a voice device by default: wake word, always listening, or typing | [desktop](design/technical/clients/desktop.md) |
| 32 | One AI configuration for the whole household, with any of the four providers; choosing a subscription by recognised voice can be added later | [AI providers](design/technical/server/ai-providers.md) |
| 33 | The design is split into many documents: technical and visual, one subject per file | [design](design/README.md) |
| 34 | Decisions are written into the design documents, and this log is kept as well | [design](design/README.md) |
| 35 | A2UI is part of the assistant on devices with a screen; a device without a screen gets the answer by voice, if voice is on | [A2UI](design/technical/a2ui.md) |
| 36 | There is no roadmap yet; the technical details are made clear first | [technical design](design/technical/README.md) |
| 37 | The speech design starts from the earlier voice assistant's working speech pipeline; summoning is still designed fresh | [voice](design/technical/voice/README.md) |
| 38 | A device with no screen and no voice cannot be interacted with, so an assistant never answers on one | [A2UI](design/technical/a2ui.md), [protocol](design/technical/server/protocol.md) |
| 39 | The server records each device's capabilities when it is registered or updated, and sends them to the AI model so the reply fits the device, such as whether A2UI can be used | [protocol](design/technical/server/protocol.md), [AI providers](design/technical/server/ai-providers.md) |
| 40 | A module is a set of tools an AI agent can call, and nothing more; the features, their settings and their storage are part of the system; modules are given to assistants, and one module can be given to several | [modules](design/technical/modules/README.md), [server](design/technical/server/README.md) |
| 41 | Keyboard shortcuts are per device, kept on that device, not server-wide | [desktop](design/technical/clients/desktop.md) |
| 42 | A new feature is built into the system first; a module then adds the tools for it | [modules](design/technical/modules/README.md) |
| 43 | An action that needs the server, including one started by a shortcut, talks to the server and shows a loader or a similar sign while it waits | [clients](design/technical/clients/README.md), [desktop](design/technical/clients/desktop.md) |
| 44 | Every person has an account on the server and signs in with an email address and a password | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 45 | Once a household device recognises a person's voice, it can give that person their own information | [identity and sharing](design/technical/server/identity-and-sharing.md), [speaker identification](design/technical/voice/speaker-identification.md) |
| 46 | Listening for a wake word is a setting of the device; a device without its own settings is set in the admin panel | [wake word](design/technical/voice/wake-word.md) |
| 47 | Assistants are assigned to chosen devices or to all devices, and people can create their own assistants | [assistants](design/technical/voice/assistants.md) |
| 48 | An assistant can act on or send to another device; the other person does not have to accept for now | [assistants](design/technical/voice/assistants.md) |
| 49 | The phone and tablet app is one app; at install it is set up as a personal device or as a household device, each with its own sign-in flow | [mobile](design/technical/clients/mobile.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 50 | A computer can hold several accounts, switched with a short passcode | [identity and sharing](design/technical/server/identity-and-sharing.md), [desktop](design/technical/clients/desktop.md) |
| 51 | What guests, children and unrecognised voices may do is configurable; the starting point is things that touch nobody's private data | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 52 | Household things, such as a shopping list, are shared across the household by default; a share can be to named people or to the household | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 53 | An assistant acting for a person can read what others have shared with that person | [identity and sharing](design/technical/server/identity-and-sharing.md), [assistants](design/technical/voice/assistants.md) |
| 54 | One server per household; another household or a workplace is a separate server, and a person has an account on each; linking servers is not needed for now | [server](design/technical/server/README.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 55 | Removing a person is a soft deletion | [data and sync](design/technical/server/data-and-sync.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 56 | `docs/open-questions.md` is the full list of open questions; a new question raised by an answer is added there, not asked in conversation | [design](design/README.md) |
| 57 | A household device speaks personal information only when its owner asks with the wake word and their voice is recognised; never unprompted | [identity and sharing](design/technical/server/identity-and-sharing.md), [notifications and routing](design/technical/server/notifications-and-routing.md), [speaker identification](design/technical/voice/speaker-identification.md) |
| 58 | The wake word belongs to the assistant; a device can override it, in an advanced setting | [wake word](design/technical/voice/wake-word.md) |
| 59 | A personal assistant is on a household device only if assigned there; nobody is tracked through the home, and presence is known only at a recognised wake word | [assistants](design/technical/voice/assistants.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 60 | A source connected through a person's own account is private to them; household things are shared by default | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 61 | Account switching on a computer covers different people in one household and one person's accounts on different servers | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 62 | For the first release the server runs on Linux, on ARM and x86 | [server](design/technical/server/README.md) |
| 63 | Without the server, local features and synced data keep working; the assistant, voice and anything involving another device wait and show it | [clients](design/technical/clients/README.md), [desktop](design/technical/clients/desktop.md) |
| 64 | Speech to text and text to speech run on the server only for now; on-device speech stays possible later | [speech to text](design/technical/voice/speech-to-text.md), [text to speech](design/technical/voice/text-to-speech.md) |
| 65 | The first release has base modules for feedback, notifications, timers and reminders, and device control; more follow | [modules](design/technical/modules/README.md) |
| 66 | No Home Assistant integration; smart-home systems are integrated directly later, with Home Assistant's code as an example | [modules](design/technical/modules/README.md) |
| 67 | Only an admin adds a household device: a shareable invite code or QR code registers the device, and an admin then approves it | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 68 | There are no passwords; a person signs in with their email address and a one-time code sent to it. This replaces the password in decision 44 | [identity and sharing](design/technical/server/identity-and-sharing.md), [mobile](design/technical/clients/mobile.md), [admin panel](design/technical/clients/web-admin.md) |
| 69 | Every member manages their own settings, in the phone app first, and also in the desktop client and the admin panel; an admin also manages the household and the server | [admin panel](design/technical/clients/web-admin.md), [mobile](design/technical/clients/mobile.md) |
| 70 | Sign-in codes are sent through a mail account the admin enters; a relay hosted by the project may come later | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 71 | Without internet, a new device is signed in with a code from an already signed-in device or one an admin issues; otherwise it is not possible | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 72 | First-run setup of a server is done in the admin panel | [admin panel](design/technical/clients/web-admin.md) |
| 73 | A voice page is set up as personal or household when opened, with the same flows as the phone app | [voice page](design/technical/clients/web-voice.md) |
| 74 | First-run setup creates a default household assistant, used by everyone on every device until customised | [assistants](design/technical/voice/assistants.md) |
| 75 | A conversation is remembered for a short time and then starts fresh; there is no memory across conversations for now, and remembering on request is a tool of a lists module | [assistants](design/technical/voice/assistants.md), [modules](design/technical/modules/README.md) |
| 76 | Only an admin assigns an assistant to a household device; a person puts their own assistant on their own devices | [assistants](design/technical/voice/assistants.md) |
| 77 | An assistant may act on the speaker's own devices, household devices and other people's devices | [assistants](design/technical/voice/assistants.md) |
| 78 | An assistant does not ask for confirmation before acting, for now; confirmation is added when a tool needs it | [AI providers](design/technical/server/ai-providers.md) |
| 79 | Unrecognised voices are served by guest assistants: assistants marked to answer anyone, with guest-level tools; there can be several | [identity and sharing](design/technical/server/identity-and-sharing.md), [assistants](design/technical/voice/assistants.md) |
| 80 | Several AI providers can be configured, and each assistant uses exactly one; nobody overrides it per person. This replaces the single household configuration | [AI providers](design/technical/server/ai-providers.md) |
| 81 | A subscription's command-line tool runs on the server | [AI providers](design/technical/server/ai-providers.md) |
| 82 | An assistant that is not a guest assistant gives an unrecognised voice a short refusal, for now | [summoning](design/technical/voice/summoning.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 83 | A guest assistant that recognises the speaker acts with that person's permissions | [identity and sharing](design/technical/server/identity-and-sharing.md), [assistants](design/technical/voice/assistants.md) |
| 84 | A module is both a grouping of tools around a subject and the place where those tools are written; core features and shared parts stay in the system | [modules](design/technical/modules/README.md) |
| 85 | When several devices hear the wake word, the one that heard it loudest and clearest answers; the choice is a replaceable step | [summoning](design/technical/voice/summoning.md) |
| 86 | A feature's data lives on the server as a system feature; a module exposes it as tools, and switching a module off loses nothing | [modules](design/technical/modules/README.md) |
| 87 | A reply can carry tags next to its words, for character expressions and for "keep listening"; tags are removed before speech | [reply tags](design/technical/voice/reply-tags.md) |
| 88 | A follow-up without the wake word is possible only when the reply carried the "keep listening" tag | [reply tags](design/technical/voice/reply-tags.md), [summoning](design/technical/voice/summoning.md) |
| 89 | A voice not matched with enough certainty counts as unrecognised; there is no in-between level and no PIN or phone fallback | [summoning](design/technical/voice/summoning.md), [speaker identification](design/technical/voice/speaker-identification.md) |
| 90 | A routing rule can send to the person's own devices, household devices and other people; household sources have rules too | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 91 | A routing rule has four parts: what, when, where and how it arrives; the first matching rule is used | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 92 | Every client has our own look; nothing mimics the host desktop, not even as a theme | [visual](design/visual/README.md) |
| 93 | A household device invite can be limited in number of devices and in time, per invite; both are unlimited by default | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 94 | The account passcode is asked for when switching account, when the client starts and when the computer is unlocked | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 95 | The first release has two roles, admin and member; a restricted role for children comes later | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 96 | A shared item appears among the receiver's own items, marked, and in a "shared with me" view | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 97 | Lists, timers and alarms, household devices and assistants, and announcements are household things by default | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 98 | A removed person's data is never erased and can always be restored | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 99 | After a "keep listening" tag, anyone may answer without the wake word, for a few seconds | [reply tags](design/technical/voice/reply-tags.md) |
| 100 | Tags are never shown or spoken; whether a device shows a character is a capability, and without it character tags are not offered to the model and are removed if returned | [reply tags](design/technical/voice/reply-tags.md), [protocol](design/technical/server/protocol.md) |
| 101 | "Stop" while something rings or while the assistant speaks, and "snooze" on an alarm, work without the wake word | [summoning](design/technical/voice/summoning.md) |
| 102 | An assistant has a list of wake words chosen by the household, with room for other spellings; people record the wake words, and the recordings are used to recognise them | [wake word](design/technical/voice/wake-word.md), [speaker identification](design/technical/voice/speaker-identification.md) |
| 103 | A person records the wake words on any of their devices with a microphone | [speaker identification](design/technical/voice/speaker-identification.md) |
| 104 | Voice recordings and voiceprints stay on the server, and a person can delete their own | [speaker identification](design/technical/voice/speaker-identification.md) |
| 105 | The first cloud speech providers are Deepgram for speech to text, and ElevenLabs and Cartesia for text to speech | [speech to text](design/technical/voice/speech-to-text.md), [text to speech](design/technical/voice/text-to-speech.md) |
| 106 | Lists are a system feature with a module in the first release | [lists](design/technical/server/lists.md), [modules](design/technical/modules/README.md) |
| 107 | The default assistant can be removed, provided other assistants cover what it did | [assistants](design/technical/voice/assistants.md) |
| 108 | A timer or alarm rings where it was set, and can be asked to ring elsewhere | [timers](design/technical/server/timers.md) |
| 109 | A notification that matches no rule falls back to its owner's phone; a household one goes to the admin's phone and the history | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 110 | Quiet hours exist per person and per device | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 111 | Every personal device shows the notification centre, with personal and household notifications, and a notification is controlled from anywhere | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| 112 | An assistant is given a module whole; single tools are not switched off, for now | [modules](design/technical/modules/README.md) |
| 113 | A feedback report arrives in the admin panel first; an admin is notified, reviews a preview of the GitHub issue and creates it under their own account with their own token | [feedback](design/technical/server/feedback.md) |
| 114 | Timers and alarms ring on a device; a reminder is a notification at a set time, routed like any other; alarms and reminders can repeat | [timers](design/technical/server/timers.md) |
| 115 | A timer or alarm whose device is off falls back like a notification: to the setter's phone, or to other household devices | [timers](design/technical/server/timers.md) |
| 116 | A list entry is like a Google Keep note: a list of items to tick off, or plain text | [lists](design/technical/server/lists.md) |
| 117 | Anyone may file feedback, including an unrecognised voice through a guest assistant | [feedback](design/technical/server/feedback.md) |
| 118 | Email accounts connect through any IMAP server, Google sign-in or Microsoft sign-in from the start | [email](design/technical/server/email.md) |
| 119 | Credentials and other secrets are kept encrypted on the server in one vault, a system feature | [vault](design/technical/server/vault.md), [email](design/technical/server/email.md) |
| 120 | Clipboard sync between a person's devices is on by default, and clipboard content is encrypted in storage and in transit | [clipboard](design/technical/server/clipboard.md) |
| 121 | History is kept forever by default, with a limit that can be set per kind | [data and sync](design/technical/server/data-and-sync.md), [clipboard](design/technical/server/clipboard.md) |
| 122 | The vault holds system secrets, which the server can use, and each person's encrypted data, which only that person's devices can read; the server, admins and assistants cannot | [vault](design/technical/server/vault.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 123 | Clipboard history is a person's encrypted data; an assistant cannot read it by default, and when allowed it is sent from a device that holds the key | [clipboard](design/technical/server/clipboard.md), [vault](design/technical/server/vault.md) |
| 124 | The vault is also a password manager, using the same personal keys | [vault](design/technical/server/vault.md) |
| 125 | A fixed spoken sentence comes from the system feature, with reusable audio; the AI model words anything that is raw data, needs character or may lead to conversation | [A2UI](design/technical/a2ui.md), [text to speech](design/technical/voice/text-to-speech.md) |
| 126 | The voice page is spoken to by default, can show the conversation as live text, and can be chatted with by typing, without spoken answers | [voice page](design/technical/clients/web-voice.md) |
| 127 | Only the clipboard and passwords are a person's sensitive data; anything an assistant must read by itself stays readable by the server | [vault](design/technical/server/vault.md) |
| 128 | The password manager is in the first release, and passwords can be shared with the household | [vault](design/technical/server/vault.md) |
| 129 | Each person gets a recovery sheet as a PDF, like 1Password's emergency kit, and an admin should be able to help recover a key | [vault](design/technical/server/vault.md) |
| 130 | Browsers do not get at a person's sensitive data in the first release | [vault](design/technical/server/vault.md) |
| 131 | Assistants should be able to use the clipboard and passwords. This reopens decisions 122 and 123: whether the server can read a person's sensitive data is an open question again | [vault](design/technical/server/vault.md), [clipboard](design/technical/server/clipboard.md) |
| 132 | An assistant asks before searching a person's clipboard; for passwords it asks twice, once to search and once before a password is decrypted | [vault](design/technical/server/vault.md), [clipboard](design/technical/server/clipboard.md), [AI providers](design/technical/server/ai-providers.md) |
| 133 | A person's clipboard history and passwords are sealed: only their devices hold the key, and the server, admins and assistants cannot read them. This settles the question reopened in 131 | [vault](design/technical/server/vault.md), [clipboard](design/technical/server/clipboard.md), [identity and sharing](design/technical/server/identity-and-sharing.md) |
| 134 | An approval for sealed data is given on a device of that person that holds the key; that device decrypts what was asked for | [vault](design/technical/server/vault.md) |
| 135 | Every request for sealed data explains why it is needed and what will be done with it | [vault](design/technical/server/vault.md) |
| 136 | A password can be shared with a limit on views and on time, as in 1Password | [vault](design/technical/server/vault.md) |
| 137 | Recovery is by the person's recovery sheet, or by a sealed recovery copy that an admin can release | [vault](design/technical/server/vault.md) |
| 138 | There are no groups of people and no shared vaults for now; a password is shared with named people or the household | [vault](design/technical/server/vault.md) |
| 139 | A password is never spoken and never shown on a household device | [vault](design/technical/server/vault.md) |
| 140 | The core of a client is hand-built; feature screens and everything an assistant shows are described with A2UI | [A2UI](design/technical/a2ui.md) |
| 141 | Saving a generated screen for reuse is not in the first release | [A2UI](design/technical/a2ui.md) |

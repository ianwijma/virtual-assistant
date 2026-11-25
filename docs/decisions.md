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

# Open questions

An index. Each design document ends with its own "Open questions"
section, and that is where a question lives. This page says which to
answer first and where the rest are. An answered question is removed from
its "Open questions" section and written into that document's design.

Planning order: first the technical details of the system and how its
parts interact, then modules. The roadmap comes after that.

## Answer these first

These five shape the most other answers.

| Question | Lives in |
|---|---|
| How does someone become "them" on a personal device, and who may make a device a household device? One app or two? | [identity and sharing](design/technical/server/identity-and-sharing.md), [mobile](design/technical/clients/mobile.md) |
| Once a household device recognises a voice, may it show or speak that person's own things? | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| Does a wake word belong to an assistant everywhere, and does every device listen for every assistant? | [assistants](design/technical/voice/assistants.md) |
| Can each person have their own assistant with its own memory, and does it follow them to household devices? | [assistants](design/technical/voice/assistants.md) |
| Can an assistant act on another device or for another person, and must that person accept? | [assistants](design/technical/voice/assistants.md) |

## Where the rest are

| Subject | Document |
|---|---|
| Hardware, installing, updating, backups, database | [server](design/technical/server/README.md) |
| Messages, pairing steps, audio transport | [protocol](design/technical/server/protocol.md) |
| History, removal of a person's data, search | [data and sync](design/technical/server/data-and-sync.md) |
| Sign-in, guests and children, how shares appear | [identity and sharing](design/technical/server/identity-and-sharing.md) |
| What a routing rule is, quiet hours, actions across devices | [notifications and routing](design/technical/server/notifications-and-routing.md) |
| Overrides, confirmation of actions, memory | [AI providers](design/technical/server/ai-providers.md) |
| Trusting the server's certificate, finding the server | [networking](design/technical/server/networking.md) |
| Echo, interruption, timing | [voice](design/technical/voice/README.md) |
| States, which device answers, follow-ups | [summoning](design/technical/voice/summoning.md) |
| Which detector, custom wake words | [wake word](design/technical/voice/wake-word.md) |
| Enrolment, certainty, voice data | [speaker identification](design/technical/voice/speaker-identification.md) |
| Models, providers, languages | [speech to text](design/technical/voice/speech-to-text.md), [text to speech](design/technical/voice/text-to-speech.md) |
| Which modules, the module contract | [modules](design/technical/modules/README.md) |
| GitHub sign-in, review before sending | [feedback](design/technical/modules/feedback.md) |
| Providers, credentials, safe HTML | [email](design/technical/modules/email.md) |
| Sync defaults, large items | [clipboard](design/technical/modules/clipboard.md) |
| Offline features, Linux desktop integration, "snappy" | [desktop](design/technical/clients/desktop.md) |
| One app or two, push without a cloud | [mobile](design/technical/clients/mobile.md) |
| Who uses it, first-run setup | [admin panel](design/technical/clients/web-admin.md) |
| Household or personal, sign-in | [voice page](design/technical/clients/web-voice.md) |
| Hand-built or described screens, untrusted content, a Rust library | [A2UI](design/technical/a2ui.md) |
| The feel, mimicry of the host desktop, existing characters | [visual design](design/visual/README.md) |
| Build order, review and testing, test machines | [repository](design/technical/repository.md) |
| Licences of models and voices | [licensing and hardware](design/technical/licensing-and-hardware.md) |

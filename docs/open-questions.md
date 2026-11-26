# Open questions

Every open question, in one list, sorted from what matters most now to
what can wait. This is the document the owner answers from. Each question
also sits at the end of the design document it belongs to, which is linked
after the question. A question that sits in two design documents is listed
once here.

## How the list is sorted

| Part | What is in it | Who moves it forward |
|---|---|---|
| [To confirm](#to-confirm) | Readings of earlier answers | The owner, only if a reading is wrong |
| [1. Now](#1-now) | Questions that shape the data, the protocol, who may do what, or what the first release contains. A late answer means rework | The owner |
| [2. Next](#2-next) | Questions that shape one part. Each is needed before that part is designed in detail | The owner |
| [3. Later](#3-later) | Details and numbers that can be settled while building | The owner |
| [4. To research or propose](#4-to-research-or-propose) | Questions that need investigation or a worked-out proposal, not an opinion | An agent proposes, the owner agrees |
| [5. Visual design](#5-visual-design) | Questions about the look and feel | The owner, in a separate thread |

A new question is placed in the part it fits, not at the end.

## The flow

This is how a question moves from open to decided.

1. **The owner answers** one or more questions from this list, by number,
   in any order and as loosely as they like.
2. **The answer is written into the design.** It goes into the design
   document the question belongs to, as part of the design itself.
3. **The question is removed** from this list and from the "Open
   questions" section of that design document.
4. **A line is added to [decisions.md](decisions.md),** naming the design
   document the decision is written into.
5. **Follow-ups are added here.** If the answer raises a new question, it
   is added to this list and to its design document. If the answer had to
   be interpreted, the reading goes under "To confirm".
6. **Nothing is asked in conversation.** The owner is not asked to clarify
   an answer. They find follow-ups in this list the next time they answer.
7. **The change is committed** as one change: the design, this list and
   the decisions log together.

Rules that go with the flow:

- A question is never decided by anyone but the owner.
- A reading under "To confirm" stands as written in the design until the
  owner corrects it. No reply means it is accepted.
- A question that needs investigation, not an opinion, stays in the list
  until the research is done and the owner has agreed to the outcome.
- Numbers are for answering by number. They change when the list changes,
  so answer against the current list.

Planning order: the technical details first, then modules. The roadmap
comes after that.

## To confirm

These are readings of earlier answers. Each stands as written in the design
unless corrected. They are lettered so that the numbers below stay for the
questions.

- **AP.** With sealing put off, an assistant still asks before it
  searches the clipboard, and the person can say yes by voice or on
  screen. An admin can read clipboard history like other data, and
  clipboard search can also run on the server. [clipboard]
- **AQ.** A reply made while the source device is off waits and is sent
  when that device is back; it is never dropped. [notifications]
- **AR.** A referral link is shown as one: the person can see that the
  project earns from it. [licensing]
- **AN.** The kept text of an email can be shown as plain text on the
  person's own devices, from its notification. [email]
- **AO.** Attachments are ignored entirely: not kept, not listed, not
  summarised. [email]

## 1. Now

Nothing is waiting here at the moment.

## 2. Next

Nothing is waiting here at the moment.

## 3. Later

1. The App Store's terms conflict with the GPL. How is the project's
   own iOS build published? To be worked out before iOS is built.
   [mobile]
2. What a restricted role for children may do, once it is added.
   [identity]
3. The build order of the parts. There is no roadmap yet; it is decided
    after the technical details are clear. [repository]

4. Sealed data and a password manager, after the first release: data
   only a person's own devices can read, with a recovery sheet and a
   recovery copy. The earlier answers on this are decisions 122 to 139.
   [vault]

5. How the research and write-up threads are run after the merge: one
   thread that starts several others by area, each raising a pull
   request? And are the design write-ups (protocol, pairing, summoning
   states) written before building starts, or by whoever builds each
   part? [repository]

## 4. To research or propose

These need investigation or a worked-out proposal. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

This work is done in separate threads, after the planning pull request is
merged. It is not started from the planning thread.

How the threads are run is not settled. The likely form: one thread
starts several others, by area. Each does its research or writes its
proposal, raises a pull request that updates the design, and puts
anything that needs the owner's answer into this list.

Research is kept as small as possible. It is done online, from
documentation and other projects. A small prototype is made only when a
question cannot be settled otherwise. The aim is a quick first working
product, not a complete study.

6. The summoning states and transitions themselves. [summoning]
7. Which database the server uses, and how search stays fast over years
   of history. The owner leans towards PostgreSQL, for being open source
   and for its extensions such as time series, unless there is a strong
   case for SQLite. [server], [data], [clipboard]
8. How the event log handles household data that several people can
    see. [data]
9. The full list of protocol messages, and how the protocol is
    versioned. [protocol]
10. The exact pairing steps for a personal device and for a household
    device. [protocol], [identity]
11. How audio travels: on the device's connection or a separate one.
    [protocol], [voice]
12. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
13. How notifications reach a phone when the app is closed. To compare:
   what works on Android without Google's push service, what iOS allows,
   and simply accepting Google's and Apple's push services with a small
   relay if one is needed. Include what happens when the connection is
   lost. [mobile]
14. Which wake word detector to use, and whether a detection is confirmed
   by transcribing the same audio. Wake words are typed in freely, so
   the detector must accept any word. Finding the wake word in the
   transcript is the fallback, though transcripts can get the word
   wrong. Also: whether training a device per person, from several
   places in the room, improves detection. [wake word]
15. Which small local speech-to-text model and small local voice are the
   defaults, which better ones are suggested in set-up, and which of
   them have licences that allow selling hardware. [speech to text],
   [text to speech], [licensing]
16. Which of the services the system suggests have a referral programme,
   and on what terms. [licensing]
17. Echo: how a device ignores its own voice while it speaks and still
   hears another voice, so that "stop" works. [voice]
18. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
19. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
20. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
21. How copied HTML is drawn with its formatting, safely, on each
   platform: a sandboxed frame in a browser, and whatever the Rust
   desktop client and the phone apps can use. [clipboard]
22. How the admin panel and the voice page get HTTPS that a browser
   trusts, for a non-technical person. To compare: certificates through
   Tailscale, a proxy domain per installation that the project provides,
   the person's own certificates, accepting the browser's warning at
   first, and any other way found. An AI assistant could also walk a
   person through the set-up. [networking]
23. How the server is found on the home network when a device is first
     paired. [networking]
24. How a reply tag is lined up with the moment in the speech where it
   stands. [reply tags]
25. Signing in with Google or Microsoft for email, after the first
   release: who registers the application with each company, and what
   Google's review of applications that read mail involves. [email]
26. Can the development virtual machine run an Android emulator with
   sound and virtual machines inside it? Both need virtualisation inside
   a virtual machine. The Rust toolchain is not installed on it yet
   either. [repository]
27. How a vendor's command-line tool is installed and signed in to from
   the admin panel, including inside a container. [ai providers]
28. The list of reply tags, and how they are written in a reply.
   [reply tags]
29. The contents of our A2UI catalog. [a2ui]
30. The full list of capabilities, and how a catalog version is
    expressed. [protocol]
31. Whether a notification can open the email in the person's own email
   application, on a phone and on a desktop. [email]
32. How the vault encrypts its secrets, so that control of the running
   server does not expose them, and where that key is kept. Kept small;
   if it slows the work, the first release relies on disk encryption.
   [vault]

## 5. Visual design

These are not asked in the technical planning thread. The owner works on
the look and feel in a separate thread.

33. Three or four words for how it should feel, and products whose look
   you admire. [visual]
34. Are settings screens generated from each feature's description, so
   that one definition serves the phone app, the desktop client and the
   admin panel? This is decided once there are visual designs of the app
   and the admin panel. [visual]

[identity]: design/technical/server/identity-and-sharing.md
[assistants]: design/technical/voice/assistants.md
[summoning]: design/technical/voice/summoning.md
[wake word]: design/technical/voice/wake-word.md
[speaker identification]: design/technical/voice/speaker-identification.md
[notifications]: design/technical/server/notifications-and-routing.md
[ai providers]: design/technical/server/ai-providers.md
[modules]: design/technical/modules/README.md
[clients]: design/technical/clients/README.md
[desktop]: design/technical/clients/desktop.md
[mobile]: design/technical/clients/mobile.md
[admin panel]: design/technical/clients/web-admin.md
[voice page]: design/technical/clients/web-voice.md
[feedback]: design/technical/server/feedback.md
[email]: design/technical/server/email.md
[clipboard]: design/technical/server/clipboard.md
[lists]: design/technical/server/lists.md
[vault]: design/technical/server/vault.md
[timers]: design/technical/server/timers.md
[data]: design/technical/server/data-and-sync.md
[a2ui]: design/technical/a2ui.md
[server]: design/technical/server/README.md
[networking]: design/technical/server/networking.md
[protocol]: design/technical/server/protocol.md
[voice]: design/technical/voice/README.md
[reply tags]: design/technical/voice/reply-tags.md
[speech to text]: design/technical/voice/speech-to-text.md
[text to speech]: design/technical/voice/text-to-speech.md
[licensing]: design/technical/licensing-and-hardware.md
[repository]: design/technical/repository.md
[visual]: design/visual/README.md

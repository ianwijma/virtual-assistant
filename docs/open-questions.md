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

- **X.** An admin without a GitHub token can still read reports in the
  admin panel, but cannot send them on. [feedback]

- **Y.** "Remember this for me" is saved as a plain text entry.
  [lists]

- **Z.** Email credentials are system secrets: the server must be able
  to use them to fetch mail while every device is off. [vault]
- **AA.** After a household device speaks a notification, it can listen
  for a follow-up about it without the wake word, in the same way as
  after a "keep listening" tag. [reply tags]
- **AB.** The voice page has two views: a voice view with the live text
  of the conversation, and a typed chat view that does not speak.
  [voice page]

- **AC.** Passwords follow the same rule as the clipboard: approval and
  decryption happen only on a device of that person that holds the key.
  [vault]
- **AD.** What an assistant may do with an unsealed password is whatever
  its request said and the person approved. There is no fixed list.
  [vault]
- **AE.** An admin releasing a recovery copy gives the key back to that
  person; it does not let the admin read their data. [vault]

- **AF.** The audit log covers every settings change, made from any
  client and by anyone, not only changes made in the admin panel. An
  admin can undo a single change from it. [server]
- **AG.** "At most two rounds" is the limit for a review. Your answer
  also mentioned five rounds; two is what is written. [repository]

- **AH.** Because mail is not stored, these are dropped for now: reading
  and searching mail in the desktop client, sharing single emails, and
  "copy the login code" from an email. An AI summary exists only as part
  of the new-mail notification. [email]
- **AI.** The person chooses the level of their new-mail notification,
  per account. The fuller levels are shown or spoken on their own
  devices; a household device keeps to "Ian, you have a new email".
  [email]

- **AJ.** The defaults in [assistants], and the speed targets in
  [desktop] and [voice], are my proposals. Each can be changed.
- **AK.** Lists are shown and edited in every client.
  [lists]

- **AL.** Guest use before sign-in applies to the voice page only. The
  phone app does nothing until it is signed in or approved. [voice page]
- **AM.** The quick link from an app into the admin panel works for
  members and admins alike, and shows each what they may manage.
  [admin panel]

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

## 4. To research or propose

These need investigation or a worked-out proposal. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

This work is done in separate threads, after the planning pull request is
merged. It is not started from the planning thread.

4. The summoning states and transitions themselves. [summoning]
5. Which database the server uses. [server]
6. How the event log handles household data that several people can
    see. [data]
7. The full list of protocol messages, and how the protocol is
    versioned. [protocol]
8. The exact pairing steps for a personal device and for a household
    device. [protocol], [identity]
9. How audio travels: on the device's connection or a separate one.
    [protocol], [voice]
10. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
11. How notifications reach a phone when the app is closed, without a
    cloud push service. [mobile]
12. Which wake word detector to use, and whether a detection is confirmed
    by transcribing the same audio. [wake word]
13. Where the desktop client detects the wake word. [wake word],
    [desktop]
14. Which local speech-to-text model is the default, given accuracy,
    speed on low-power hardware and licence. [speech to text]
15. Which local voices are offered, given quality and licence.
    [text to speech]
16. Which speech models and voices have licences that allow selling
    hardware. [licensing]
17. Echo: how a device avoids hearing its own answer. [voice]
18. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
19. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
20. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
21. What a generated surface may do when its content came from an
    untrusted source, such as an email. [a2ui]
22. How copied HTML is drawn safely. [clipboard]
23. How search stays fast over years of history. [data], [clipboard]
24. How a non-technical person gets a browser to trust the server's
     certificate authority. [networking]
25. How the server is found on the home network when a device is first
     paired. [networking]
26. How a reply tag is lined up with the moment in the speech where it
   stands. [reply tags]
27. How a person's key is made, how a new device of theirs gets it, and
   how the recovery copy is sealed so that releasing it takes an admin
   and cannot happen silently. [vault]
28. How system secrets are encrypted, and where that key is kept, so that
   a stolen disk or a copied backup gives nothing away. [vault]
29. Signing in with Google or Microsoft needs an application registered
   with each company, and Google reviews applications that read mail.
   Who registers them: the project, or each household's admin? [email]
30. Can the development virtual machine run an Android emulator with
   sound and virtual machines inside it? Both need virtualisation inside
   a virtual machine. The Rust toolchain is not installed on it yet
   either. [repository]
31. What happens to a reply or an "open" when the device the notification
   came from is off. [notifications]
32. How a vendor's command-line tool is installed and signed in to from
   the admin panel, including inside a container. [ai providers]
33. The list of reply tags, and how they are written in a reply.
   [reply tags]
34. The contents of our A2UI catalog. [a2ui]
35. The full list of capabilities, and how a catalog version is
    expressed. [protocol]

## 5. Visual design

These are not asked in the technical planning thread. The owner works on
the look and feel in a separate thread.

36. Three or four words for how it should feel, and products whose look
   you admire. [visual]
37. Are settings screens generated from each feature's description, so
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

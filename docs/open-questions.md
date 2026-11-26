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

- **A.** A device's wake word override is set per assistant on that
  device, in an advanced section. [wake word]
- **B.** An admin can connect a source, such as a shared mailbox, for the
  whole household, and it is then a household thing. A source a person
  connects themselves is private to them. [identity]
- **C.** The account passcode is four to six digits, and each account
  has its own. [identity]
- **D.** There is no Home Assistant integration in any release, not only
  the first. Smart-home systems are integrated directly. [modules]
- **E.** A person's own settings exist in three places: the phone app as
  the main one, the desktop client, and the admin panel. [admin panel],
  [mobile]
- **F.** Sign-in with an emailed code replaces passwords everywhere. The
  passcode for switching accounts on a computer stays. [identity]

- **G.** Both offline sign-in ways are built: a code from a device where
  the person is already signed in, and a code an admin issues. The first
  also works when there is internet, as a quick way to add a device.
  [identity]
- **H.** First-run setup covers: the first admin, the household's name,
  the mail account, the AI provider and speech. The first admin is created
  without an emailed code, because no mail account exists yet.
  [admin panel]
- **I.** A voice page does nothing until it is signed in as personal, or
  added and approved as household. It is not usable as a household device
  before that. [voice page]

- **J.** A guest assistant is an ordinary assistant with a "guest"
  setting, not a separate kind of thing. [assistants]
- **K.** The default household assistant is also a guest assistant at
  first: it answers anyone, at guest level when it does not recognise the
  voice. That is why it can only be removed when another assistant
  answers guests. [assistants]

- **L.** A tool is written in one module and belongs to that module
  only. [modules]

- **M.** Modules are switched on per assistant, not per device. A device
  gets them through the assistants assigned to it. [modules]
- **N.** A household source's routing rules are set by an admin.
  [notifications]

- **O.** An admin can withdraw a household device invite at any time.
  [identity]
- **P.** In routing rules, the order is set by the person, and the first
  matching rule is the only one used. [notifications]

- **Q.** "Never erased" also means an admin has no button to erase a
  removed person's data. [identity]
- **R.** A person can make one of their lists private; it is then not a
  household thing. [identity]

- **S.** An answer given by someone else during "keep listening" is
  handled with the permissions of the person who started the
  conversation. [reply tags]
- **T.** Wake words are typed in as text, and any word can be used. The
  recordings are per person and serve to recognise that person; they are
  not needed to make a wake word work. Whether a detector can do this is
  part of the detector research. [wake word]

- **U.** The last remaining assistant cannot be removed. [assistants]
- **V.** A personal notification whose owner has no phone falls back to
  the history only. With several admins, a household notification falls
  back to all of them. [notifications]

- **W.** "Controlled from anywhere" means, for the first release, seeing
  and dismissing. Replying to a notification or opening it on its source
  device is added later, per kind of notification. [notifications]
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
  and searching mail in the desktop client, an assistant summarising or
  reading out an email, sharing single emails, and "copy the login code"
  from an email. [email]

## 1. Now

Nothing is waiting here at the moment.

## 2. Next

### Voice

1. The list of reply tags, and how they are written in a reply.
   [reply tags]

### Screens


## 3. Later

2. Which notifications can be replied to or opened from another device,
   and what happens when the source device is off? [notifications]
3. How many voice recordings are needed, and whether a new wake word
   means recording again. [speaker identification]
4. Where lists are shown and edited in each client. [lists]
5. The number of seconds a device keeps listening after a "keep
   listening" tag. [reply tags]
6. What a restricted role for children may do, once it is added.
   [identity]
7. The level of certainty at which a voice counts as recognised.
   [speaker identification]
8. How long a pause ends a conversation. [assistants]
9. The build order of the parts. There is no roadmap yet; it is decided
    after the technical details are clear. [repository]
10. Whether to create the Cargo workspace and CI before planning is
    finished. For now the answer is no. [repository]
11. Building and publishing for iOS needs a Mac and an Apple developer
    account, and the App Store has friction with the GPL. How is that
    handled? [mobile]
12. Is preinstalling a vendor's AI command-line tool on hardware ever
    wanted? It would need that vendor's commercial terms. [licensing]
13. The silence timings, and whether a person can tune them.
    [speech to text]
14. The numbers that define "snappy" on the desktop, and the tests for
    them. [desktop]
15. The numbers for a fast voice turn, and how they are tested. [voice]
16. How false wakes and missed wakes are measured. [wake word]
17. Feedback: how duplicates are avoided. [feedback]
18. The contents of our A2UI catalog. [a2ui]
19. The full list of capabilities, and how a catalog version is
    expressed. [protocol]

## 4. To research or propose

These need investigation or a worked-out proposal. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

20. The summoning states and transitions themselves. [summoning]
21. Which database the server uses. [server]
22. How the event log handles household data that several people can
    see. [data]
23. The full list of protocol messages, and how the protocol is
    versioned. [protocol]
24. The exact pairing steps for a personal device and for a household
    device. [protocol], [identity]
25. How audio travels: on the device's connection or a separate one.
    [protocol], [voice]
26. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
27. How notifications reach a phone when the app is closed, without a
    cloud push service. [mobile]
28. Which wake word detector to use, and whether a detection is confirmed
    by transcribing the same audio. [wake word]
29. Where the desktop client detects the wake word. [wake word],
    [desktop]
30. Which local speech-to-text model is the default, given accuracy,
    speed on low-power hardware and licence. [speech to text]
31. Which local voices are offered, given quality and licence.
    [text to speech]
32. Which speech models and voices have licences that allow selling
    hardware. [licensing]
33. Echo: how a device avoids hearing its own answer. [voice]
34. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
35. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
36. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
37. What a generated surface may do when its content came from an
    untrusted source, such as an email. [a2ui]
38. How copied HTML is drawn safely. [clipboard]
39. How search stays fast over years of history. [data], [clipboard]
40. How a non-technical person gets a browser to trust the server's
     certificate authority. [networking]
41. How the server is found on the home network when a device is first
     paired. [networking]
42. How a reply tag is lined up with the moment in the speech where it
   stands. [reply tags]
43. How a person's key is made, how a new device of theirs gets it, and
   how the recovery copy is sealed so that releasing it takes an admin
   and cannot happen silently. [vault]
44. How system secrets are encrypted, and where that key is kept, so that
   a stolen disk or a copied backup gives nothing away. [vault]
45. Signing in with Google or Microsoft needs an application registered
   with each company, and Google reviews applications that read mail.
   Who registers them: the project, or each household's admin? [email]
46. Can the development virtual machine run an Android emulator with
   sound and virtual machines inside it? Both need virtualisation inside
   a virtual machine. The Rust toolchain is not installed on it yet
   either. [repository]

## 5. Visual design

These are not asked in the technical planning thread. The owner works on
the look and feel in a separate thread.

47. Three or four words for how it should feel, and products whose look
   you admire. [visual]
48. Are settings screens generated from each feature's description, so
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

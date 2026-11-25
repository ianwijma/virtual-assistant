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

## 1. Now

Nothing is waiting here at the moment.

## 2. Next

### Voice

1. The list of reply tags, and how they are written in a reply.
   [reply tags]

### Modules and timers

2. Timers, alarms and reminders: how do the three differ, and is a
   reminder a notification at a set time, routed like any other? Do they
   repeat, such as an alarm on every weekday? [timers]
3. What happens when the device that should ring is off or unreachable?
   [timers]
4. Lists: what can a list hold: plain items, amounts, check marks,
   notes? And is "remember this" a list like any other, or a separate
   kind of note? [lists]

### Notifications

5. Which actions can be taken on a notification from another device
    (dismiss, reply, open), and what if the source device is off?
    [notifications]

### Modules and system features

6. Can an assistant be given a module with some of its tools switched
    off? [modules]
7. Feedback: how does the server sign in to GitHub: a token the admin
    enters, a relay the project hosts, or a prefilled link only?
    [feedback]
8. Feedback: is a report always reviewed by a person before it is sent,
    and by whom: the reporter, or an admin? [feedback]
9. Feedback: may any member file a report, including by voice?
    [feedback]
10. Email: which providers: any IMAP server, Gmail, Outlook? [email]
11. Email: how does a person sign in to their account, and where is the
    credential kept? [email]
12. Clipboard: is sync on by default, and between which devices?
    [clipboard]
13. How long is history kept, for the clipboard and for events in
    general, and how are old events trimmed? [clipboard], [data]

### Screens

14. Who writes the spoken form of a screen: the system feature, or the AI
    model? [a2ui]
15. Which screens are hand-built and which are described with A2UI?
    [a2ui]
16. Can a generated surface be saved and reused, and by whom? [a2ui]
17. Are settings screens generated from each feature's description, as in
    the earlier voice assistant? [admin panel]
18. Can the voice page be typed to as well as spoken to? [voice page]
19. What is the list of actions a shortcut can be bound to, and how does
    the shortcut system work? [desktop]

### Server

20. How is the server installed and updated: a single binary, a container
    image, a package? [server]
21. How are backups made and restored? [server]
22. Is there any data to bring over from the earlier voice assistant?
    [data]

### Look

23. Three or four words for how it should feel, and products whose look
    you admire. [visual]
24. Do the existing characters and the amber and mint colour language
    carry over, or does the identity start fresh? [visual]
25. Can a person choose a different theme, and how far may it differ?
    [visual]
26. Light and dark: both, and which is the default? [visual]

### Working method

27. How is work reviewed and tested? The earlier project suffered from
    long review rounds, heavy tests and documents used as changelogs. It
    is already decided that implementation favours speed to a first
    working product over thorough testing. [repository]
28. Which machines are used to test the desktop client, the Android app
    and voice hardware? [repository]

## 3. Later

29. Which modules the default assistant starts with: all, or a few?
   [assistants]
30. How many voice recordings are needed, and whether a new wake word
   means recording again. [speaker identification]
31. Where lists are shown and edited in each client. [lists]
32. The number of seconds a device keeps listening after a "keep
   listening" tag. [reply tags]
33. What a restricted role for children may do, once it is added.
   [identity]
34. The level of certainty at which a voice counts as recognised.
   [speaker identification]
35. How long a pause ends a conversation. [assistants]
36. The build order of the parts. There is no roadmap yet; it is decided
    after the technical details are clear. [repository]
37. Whether to create the Cargo workspace and CI before planning is
    finished. For now the answer is no. [repository]
38. Building and publishing for iOS needs a Mac and an Apple developer
    account, and the App Store has friction with the GPL. How is that
    handled? [mobile]
39. Is preinstalling a vendor's AI command-line tool on hardware ever
    wanted? It would need that vendor's commercial terms. [licensing]
40. The silence timings, and whether a person can tune them.
    [speech to text]
41. How another language is added, for transcribing and for speaking.
    [speech to text], [text to speech]
42. The numbers that define "snappy" on the desktop, and the tests for
    them. [desktop]
43. The numbers for a fast voice turn, and how they are tested. [voice]
44. How false wakes and missed wakes are measured. [wake word]
45. Feedback: how duplicates are avoided. [feedback]
46. Email: how much mail is kept on the server and in each client's
    cache. [email]
47. Clipboard: how large items, such as images and files, are handled.
    [clipboard]
48. The contents of our A2UI catalog. [a2ui]
49. The full list of capabilities, and how a catalog version is
    expressed. [protocol]

## 4. To research or propose

These need investigation or a worked-out proposal. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

50. The summoning states and transitions themselves. [summoning]
51. Which database the server uses. [server]
52. How the event log handles household data that several people can
    see. [data]
53. The full list of protocol messages, and how the protocol is
    versioned. [protocol]
54. The exact pairing steps for a personal device and for a household
    device. [protocol], [identity]
55. How audio travels: on the device's connection or a separate one.
    [protocol], [voice]
56. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
57. How notifications reach a phone when the app is closed, without a
    cloud push service. [mobile]
58. Which wake word detector to use, and whether a detection is confirmed
    by transcribing the same audio. [wake word]
59. Where the desktop client detects the wake word. [wake word],
    [desktop]
60. Which local speech-to-text model is the default, given accuracy,
    speed on low-power hardware and licence. [speech to text]
61. Which local voices are offered, given quality and licence.
    [text to speech]
62. Which speech models and voices have licences that allow selling
    hardware. [licensing]
63. Echo: how a device avoids hearing its own answer. [voice]
64. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
65. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
66. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
67. What a generated surface may do when its content came from an
    untrusted source, such as an email. [a2ui]
68. How copied HTML and email HTML are drawn safely. [email],
    [clipboard]
69. How search stays fast over years of history. [data], [clipboard]
70. How the "copy the login code" behaviour works: where it runs, and how
     it finds a code in an email. [notifications], [email]
71. How a non-technical person gets a browser to trust the server's
     certificate authority. [networking]
72. How the server is found on the home network when a device is first
     paired. [networking]
73. How a reply tag is lined up with the moment in the speech where it
   stands. [reply tags]

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

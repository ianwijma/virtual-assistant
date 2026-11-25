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
- **C.** The switching passcode is four to six digits. [identity]
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

## 1. Now

### Assistants and what they may do

1. Is there always a household assistant? [assistants]
2. Does each person have a private memory with an assistant, separate
    from household memory? [assistants], [ai providers]
3. Who may assign an assistant to a device: can a person put their own
    assistant on a household device, or only an admin? [assistants]
4. Which devices may an assistant act on: only the speaker's own, or any
    device in the household? [assistants]
5. What may an assistant do without asking, and what needs confirmation?
    The earlier project's risk classes (read, change, message, money,
    security) are a candidate. [ai providers]
6. Which of the two ways to handle unrecognised voices is built, or both:
    a separate assistant for them, or one assistant that acts only when it
    recognises the person? [identity]
7. Can an assistant or a person override the household AI configuration
    with their own provider? [ai providers]
8. Where does a subscription's command-line tool run: on the server, or
    on a person's desktop? [ai providers]
9. Can one tool belong to several modules, and is a module only a
    grouping, or also where a tool is written? [modules]

### Answering by voice

10. Which device answers when several hear the wake word: the loudest,
    the first, the nearest? [summoning]
11. Is a follow-up without the wake word allowed, and for how long?
    [summoning]
12. How sure must speaker identification be before personal data is
    spoken, and what is the fallback: a PIN, or a confirmation on the
    phone? [summoning]

### Notifications

13. What is a routing rule made of: the kind of event, a schedule, the
    target devices? [notifications]
14. Besides a person's own devices, can a rule target a household device
    or another person? [notifications]

### Look

15. Does our own identity replace "mimic the host desktop" as the default
    look? The desktop brief asked for mimicry by default; the later
    decision for one recognisable look points the other way. If so,
    mimicry could remain as an optional theme. [visual]

## 2. Next

### People and sharing

16. A household device invite: how long is it valid, for how many
   devices, and can it be withdrawn? [identity]
17. Account switching: is the passcode per account, and is it also asked
    for when the computer wakes? [identity]
18. What may a child's restricted role do, as distinct from a guest?
    [identity]
19. Does a shared item appear in the other person's own views, or in a
    separate "shared with me" place? [identity]
20. Which things count as household things and are shared by default?
    [identity]
21. When is a soft-deleted person's data erased for good, and can it be
    restored? [identity]

### Voice

22. Which words work without a wake word, such as "stop" while an alarm
    rings? [summoning]
23. Can custom wake words be created by the household, and how?
    [wake word]
24. How does a person enrol their voice, and on which device?
    [speaker identification]
25. Is there a "probably this person" level between known and guest?
    [speaker identification]
26. Where is voice data stored, and how is it removed?
    [speaker identification]
27. Which cloud speech-to-text providers are supported first, beyond
    Deepgram? [speech to text]
28. Which cloud text-to-speech providers are supported first?
    [text to speech]

### Modules and timers

29. Timers, alarms and reminders are a system feature with no design
   document yet. What do they cover, and where do they ring? [modules]

### Notifications

30. What happens when no routing rule matches? [notifications]
31. Do quiet hours and "do not disturb" exist per person, per device, or
    both? [notifications]
32. Which actions can be taken on a notification from another device
    (dismiss, reply, open), and what if the source device is off?
    [notifications]

### Modules and system features

33. Can an assistant be given a module with some of its tools switched
    off? [modules]
34. Which tools need confirmation before they act? [modules]
35. Feedback: how does the server sign in to GitHub: a token the admin
    enters, a relay the project hosts, or a prefilled link only?
    [feedback]
36. Feedback: is a report always reviewed by a person before it is sent,
    and by whom: the reporter, or an admin? [feedback]
37. Feedback: may any member file a report, including by voice?
    [feedback]
38. Email: which providers: any IMAP server, Gmail, Outlook? [email]
39. Email: how does a person sign in to their account, and where is the
    credential kept? [email]
40. Clipboard: is sync on by default, and between which devices?
    [clipboard]
41. How long is history kept, for the clipboard and for events in
    general, and how are old events trimmed? [clipboard], [data]

### Screens

42. Who writes the spoken form of a screen: the system feature, or the AI
    model? [a2ui]
43. Which screens are hand-built and which are described with A2UI?
    [a2ui]
44. Can a generated surface be saved and reused, and by whom? [a2ui]
45. Are settings screens generated from each feature's description, as in
    the earlier voice assistant? [admin panel]
46. Can the voice page be typed to as well as spoken to? [voice page]
47. What is the list of actions a shortcut can be bound to, and how does
    the shortcut system work? [desktop]

### Server

48. How is the server installed and updated: a single binary, a container
    image, a package? [server]
49. How are backups made and restored? [server]
50. Is there any data to bring over from the earlier voice assistant?
    [data]

### Look

51. Three or four words for how it should feel, and products whose look
    you admire. [visual]
52. Do the existing characters and the amber and mint colour language
    carry over, or does the identity start fresh? [visual]
53. Can a person choose a different theme, and how far may it differ?
    [visual]
54. Light and dark: both, and which is the default? [visual]

### Working method

55. How is work reviewed and tested? The earlier project suffered from
    long review rounds, heavy tests and documents used as changelogs. It
    is already decided that implementation favours speed to a first
    working product over thorough testing. [repository]
56. Which machines are used to test the desktop client, the Android app
    and voice hardware? [repository]

## 3. Later

57. The build order of the parts. There is no roadmap yet; it is decided
    after the technical details are clear. [repository]
58. Whether to create the Cargo workspace and CI before planning is
    finished. For now the answer is no. [repository]
59. Building and publishing for iOS needs a Mac and an Apple developer
    account, and the App Store has friction with the GPL. How is that
    handled? [mobile]
60. Is preinstalling a vendor's AI command-line tool on hardware ever
    wanted? It would need that vendor's commercial terms. [licensing]
61. The silence timings, and whether a person can tune them.
    [speech to text]
62. How another language is added, for transcribing and for speaking.
    [speech to text], [text to speech]
63. The numbers that define "snappy" on the desktop, and the tests for
    them. [desktop]
64. The numbers for a fast voice turn, and how they are tested. [voice]
65. How false wakes and missed wakes are measured. [wake word]
66. Feedback: how duplicates are avoided. [feedback]
67. Email: how much mail is kept on the server and in each client's
    cache. [email]
68. Clipboard: how large items, such as images and files, are handled.
    [clipboard]
69. The contents of our A2UI catalog. [a2ui]
70. The full list of capabilities, and how a catalog version is
    expressed. [protocol]

## 4. To research or propose

These need investigation or a worked-out proposal. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

71. The summoning states and transitions themselves. [summoning]
72. Which database the server uses. [server]
73. How the event log handles household data that several people can
    see. [data]
74. The full list of protocol messages, and how the protocol is
    versioned. [protocol]
75. The exact pairing steps for a personal device and for a household
    device. [protocol], [identity]
76. How audio travels: on the device's connection or a separate one.
    [protocol], [voice]
77. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
78. How notifications reach a phone when the app is closed, without a
    cloud push service. [mobile]
79. Which wake word detector to use, and whether a detection is confirmed
    by transcribing the same audio. [wake word]
80. Where the desktop client detects the wake word. [wake word],
    [desktop]
81. Which local speech-to-text model is the default, given accuracy,
    speed on low-power hardware and licence. [speech to text]
82. Which local voices are offered, given quality and licence.
    [text to speech]
83. Which speech models and voices have licences that allow selling
    hardware. [licensing]
84. Echo: how a device avoids hearing its own answer. [voice]
85. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
86. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
87. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
88. What a generated surface may do when its content came from an
    untrusted source, such as an email. [a2ui]
89. How copied HTML and email HTML are drawn safely. [email],
    [clipboard]
90. How search stays fast over years of history. [data], [clipboard]
91. How the "copy the login code" behaviour works: where it runs, and how
     it finds a code in an email. [notifications], [email]
92. How a non-technical person gets a browser to trust the server's
     certificate authority. [networking]
93. How the server is found on the home network when a device is first
     paired. [networking]

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
[data]: design/technical/server/data-and-sync.md
[a2ui]: design/technical/a2ui.md
[server]: design/technical/server/README.md
[networking]: design/technical/server/networking.md
[protocol]: design/technical/server/protocol.md
[voice]: design/technical/voice/README.md
[speech to text]: design/technical/voice/speech-to-text.md
[text to speech]: design/technical/voice/text-to-speech.md
[licensing]: design/technical/licensing-and-hardware.md
[repository]: design/technical/repository.md
[visual]: design/visual/README.md

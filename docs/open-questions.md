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

## 1. Now

### What the first release is

1. What the server runs on for the first release: a home server, a
   Raspberry Pi, a container? Which processor types? [server]
2. Which features of each client must work with no server at all?
   [clients], [desktop]
3. Does speech run on the server only, or also on capable devices? This
   covers both transcribing speech and producing it. [speech to text],
   [text to speech]
4. Which modules are in the first release? [modules]
5. Is Home Assistant integration in the first release? [modules]

### Devices and signing in

6. What the sign-in flow of a household device is, what it asks for, and
   who may set one up: any member, or only an admin? [identity], [mobile]
7. Can a new device also be added without typing the password, such as
   with a code from a device that is already signed in? [identity]
8. Is the admin panel only for admins, or does every member use it for
   their own settings? [admin panel]
9. Is first-run setup done in the admin panel, and what does it cover?
   [admin panel]
10. Is a voice page a household device, a personal one, or either,
    depending on how it was opened? [voice page]
11. Does a voice page need a sign-in or pairing? In the earlier voice
    assistant it had no login at all. [voice page]

### Assistants and what they may do

12. Is there always a household assistant? [assistants]
13. Does each person have a private memory with an assistant, separate
    from household memory? [assistants], [ai providers]
14. Who may assign an assistant to a device: can a person put their own
    assistant on a household device, or only an admin? [assistants]
15. Which devices may an assistant act on: only the speaker's own, or any
    device in the household? [assistants]
16. What may an assistant do without asking, and what needs confirmation?
    The earlier project's risk classes (read, change, message, money,
    security) are a candidate. [ai providers]
17. Which of the two ways to handle unrecognised voices is built, or both:
    a separate assistant for them, or one assistant that acts only when it
    recognises the person? [identity]
18. Can an assistant or a person override the household AI configuration
    with their own provider? [ai providers]
19. Where does a subscription's command-line tool run: on the server, or
    on a person's desktop? [ai providers]
20. Can one tool belong to several modules, and is a module only a
    grouping, or also where a tool is written? [modules]

### Answering by voice

21. Which device answers when several hear the wake word: the loudest,
    the first, the nearest? [summoning]
22. Is a follow-up without the wake word allowed, and for how long?
    [summoning]
23. How sure must speaker identification be before personal data is
    spoken, and what is the fallback: a PIN, or a confirmation on the
    phone? [summoning]

### Notifications

24. What is a routing rule made of: the kind of event, a schedule, the
    target devices? [notifications]
25. Besides a person's own devices, can a rule target a household device
    or another person? [notifications]

### Look

26. Does our own identity replace "mimic the host desktop" as the default
    look? The desktop brief asked for mimicry by default; the later
    decision for one recognisable look points the other way. If so,
    mimicry could remain as an optional theme. [visual]

## 2. Next

### People and sharing

27. Account switching: is the passcode per account, and is it also asked
    for when the computer wakes? [identity]
28. What may a child's restricted role do, as distinct from a guest?
    [identity]
29. Does a shared item appear in the other person's own views, or in a
    separate "shared with me" place? [identity]
30. Which things count as household things and are shared by default?
    [identity]
31. When is a soft-deleted person's data erased for good, and can it be
    restored? [identity]

### Voice

32. Which words work without a wake word, such as "stop" while an alarm
    rings? [summoning]
33. Can custom wake words be created by the household, and how?
    [wake word]
34. How does a person enrol their voice, and on which device?
    [speaker identification]
35. Is there a "probably this person" level between known and guest?
    [speaker identification]
36. Where is voice data stored, and how is it removed?
    [speaker identification]
37. Which cloud speech-to-text providers are supported first, beyond
    Deepgram? [speech to text]
38. Which cloud text-to-speech providers are supported first?
    [text to speech]

### Notifications

39. What happens when no routing rule matches? [notifications]
40. Do quiet hours and "do not disturb" exist per person, per device, or
    both? [notifications]
41. Which actions can be taken on a notification from another device
    (dismiss, reply, open), and what if the source device is off?
    [notifications]

### Modules and system features

42. Can an assistant be given a module with some of its tools switched
    off? [modules]
43. Which tools need confirmation before they act? [modules]
44. Feedback: how does the server sign in to GitHub: a token the admin
    enters, a relay the project hosts, or a prefilled link only?
    [feedback]
45. Feedback: is a report always reviewed by a person before it is sent,
    and by whom: the reporter, or an admin? [feedback]
46. Feedback: may any member file a report, including by voice?
    [feedback]
47. Email: which providers: any IMAP server, Gmail, Outlook? [email]
48. Email: how does a person sign in to their account, and where is the
    credential kept? [email]
49. Clipboard: is sync on by default, and between which devices?
    [clipboard]
50. How long is history kept, for the clipboard and for events in
    general, and how are old events trimmed? [clipboard], [data]

### Screens

51. Who writes the spoken form of a screen: the system feature, or the AI
    model? [a2ui]
52. Which screens are hand-built and which are described with A2UI?
    [a2ui]
53. Can a generated surface be saved and reused, and by whom? [a2ui]
54. Are settings screens generated from each feature's description, as in
    the earlier voice assistant? [admin panel]
55. Can the voice page be typed to as well as spoken to? [voice page]
56. What is the list of actions a shortcut can be bound to, and how does
    the shortcut system work? [desktop]

### Server

57. How is the server installed and updated: a single binary, a container
    image, a package? [server]
58. How are backups made and restored? [server]
59. Is there any data to bring over from the earlier voice assistant?
    [data]

### Look

60. Three or four words for how it should feel, and products whose look
    you admire. [visual]
61. Do the existing characters and the amber and mint colour language
    carry over, or does the identity start fresh? [visual]
62. Can a person choose a different theme, and how far may it differ?
    [visual]
63. Light and dark: both, and which is the default? [visual]

### Working method

64. How is work reviewed and tested? The earlier project suffered from
    long review rounds, heavy tests and documents used as changelogs. It
    is already decided that implementation favours speed to a first
    working product over thorough testing. [repository]
65. Which machines are used to test the desktop client, the Android app
    and voice hardware? [repository]

## 3. Later

66. The build order of the parts. There is no roadmap yet; it is decided
    after the technical details are clear. [repository]
67. Whether to create the Cargo workspace and CI before planning is
    finished. For now the answer is no. [repository]
68. Building and publishing for iOS needs a Mac and an Apple developer
    account, and the App Store has friction with the GPL. How is that
    handled? [mobile]
69. Is preinstalling a vendor's AI command-line tool on hardware ever
    wanted? It would need that vendor's commercial terms. [licensing]
70. The silence timings, and whether a person can tune them.
    [speech to text]
71. How another language is added, for transcribing and for speaking.
    [speech to text], [text to speech]
72. The numbers that define "snappy" on the desktop, and the tests for
    them. [desktop]
73. The numbers for a fast voice turn, and how they are tested. [voice]
74. How false wakes and missed wakes are measured. [wake word]
75. Feedback: how duplicates are avoided. [feedback]
76. Email: how much mail is kept on the server and in each client's
    cache. [email]
77. Clipboard: how large items, such as images and files, are handled.
    [clipboard]
78. The contents of our A2UI catalog. [a2ui]
79. The full list of capabilities, and how a catalog version is
    expressed. [protocol]

## 4. To research or propose

These need investigation or a worked-out proposal. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

80. The summoning states and transitions themselves. [summoning]
81. Which database the server uses. [server]
82. How the event log handles household data that several people can
    see. [data]
83. The full list of protocol messages, and how the protocol is
    versioned. [protocol]
84. The exact pairing steps for a personal device and for a household
    device. [protocol], [identity]
85. How audio travels: on the device's connection or a separate one.
    [protocol], [voice]
86. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
87. How notifications reach a phone when the app is closed, without a
    cloud push service. [mobile]
88. Which wake word detector to use, and whether a detection is confirmed
    by transcribing the same audio. [wake word]
89. Where the desktop client detects the wake word. [wake word],
    [desktop]
90. Which local speech-to-text model is the default, given accuracy,
    speed on low-power hardware and licence. [speech to text]
91. Which local voices are offered, given quality and licence.
    [text to speech]
92. Which speech models and voices have licences that allow selling
    hardware. [licensing]
93. Echo: how a device avoids hearing its own answer. [voice]
94. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
95. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
96. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
97. What a generated surface may do when its content came from an
    untrusted source, such as an email. [a2ui]
98. How copied HTML and email HTML are drawn safely. [email],
    [clipboard]
99. How search stays fast over years of history. [data], [clipboard]
100. How the "copy the login code" behaviour works: where it runs, and how
     it finds a code in an email. [notifications], [email]
101. How a non-technical person gets a browser to trust the server's
     certificate authority. [networking]
102. How the server is found on the home network when a device is first
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

# Open questions

Every open question, in one list. This is the document the owner answers
from. Each question also sits at the end of the design document it belongs
to, which is linked in its heading.

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
unless corrected.

1. A device's wake word override is set per assistant on that device,
   in an advanced section. Is that the override you meant?
2. An admin can connect a source, such as a shared mailbox, for the whole
   household, and it is then a household thing. A source a person connects
   themselves is private to them.
3. The switching passcode is four to six digits.


## [Identity and sharing](design/technical/server/identity-and-sharing.md)

4. What the sign-in flow of a household device is, and who may set one up:
   any member, or only an admin?
5. Whether a new device can also be added without typing the password, such
   as with a code from a device that is already signed in.
6. Account switching: is the passcode per account, how long is it, and is it
   also asked for when the computer wakes?
7. Which of the two ways to handle unrecognised voices is built, or both.
8. What a child's restricted role may do, as distinct from a guest.
9. Does a shared item appear in the other person's own views, or in a
   separate "shared with me" place?
10. Which things count as household things and are shared by default.
11. When a soft-deleted person's data is erased for good, and whether it can
   be restored.

## [Assistants](design/technical/voice/assistants.md)

12. Is there always a household assistant?
13. Does each person have a private memory with an assistant?
14. Who may assign an assistant to a device: can a person put their own
   assistant on a household device, or only an admin?
15. Which devices an assistant may act on: only the speaker's own, or any
   device in the household?

## [Summoning](design/technical/voice/summoning.md)

16. The states and transitions themselves.
17. Which device answers when several hear the wake word: the loudest, the
   first, the nearest?
18. Whether a follow-up without the wake word is allowed, and for how long.
19. How sure speaker identification must be before personal data is spoken,
   and what the fallback is: a PIN, or a confirmation on the phone?
20. Which words work without a wake word, such as "stop" while an alarm
   rings.

## [Wake word](design/technical/voice/wake-word.md)

21. Which detector to use, and whether a detection is confirmed by
   transcribing the same audio.
22. Whether custom wake words can be created by the household, and how.
23. Where the desktop client detects the wake word.
24. How false wakes and missed wakes are measured.

## [Speaker identification](design/technical/voice/speaker-identification.md)

25. How a person enrols their voice, and on which device.
26. How sure a match must be, and whether there is a "probably this person"
   level between known and guest.
27. Where voice data is stored, and how it is removed.

## [Notifications and routing](design/technical/server/notifications-and-routing.md)

28. What a routing rule is made of: the kind of event, a schedule, the
   target devices?
29. Besides a person's own devices, can a rule target a household device or
   another person?
30. What happens when no rule matches.
31. Do quiet hours and "do not disturb" exist per person, per device, or
   both?
32. Which actions can be taken on a notification from another device
   (dismiss, reply, open), and what if the source device is off?
33. How the "copy the login code" behaviour works: on the server, on the
   desktop, or both.

## [AI providers](design/technical/server/ai-providers.md)

34. Can an assistant or a person override the household configuration with
   their own provider?
35. Where a subscription's command-line tool runs: on the server, or on a
   person's desktop?
36. What an assistant may do without asking, and what needs confirmation.
   The earlier project's risk classes (read, change, message, money,
   security) are a candidate.
37. Does each person have a private memory with an assistant, separate from
   household memory?
38. How each provider produces A2UI screens. See
   [A2UI](design/technical/a2ui.md).

## [Modules](design/technical/modules/README.md)

39. Which modules are in the first release.
40. Can one tool belong to several modules, and is a module only a grouping,
   or also where a tool is written?
41. Can an assistant be given a module with some of its tools switched off?
42. Which tools need confirmation before they act.
43. Whether Home Assistant integration is in the first release.

## [Clients](design/technical/clients/README.md)

44. Which features of each client must work with no server at all.

## [Desktop client](design/technical/clients/desktop.md)

45. Which features must work with no server at all.
46. Where the wake word is detected on a desktop.
47. How notifications, clipboard access, global hotkeys and window control
   work across Linux desktops on X11 and Wayland. This is research still to
   do, and the limits on Wayland are a known risk.
48. The numbers that define "snappy", and the tests for them.
49. The list of actions a shortcut can be bound to, and how the shortcut
   system works.

## [Phone and tablet app](design/technical/clients/mobile.md)

50. What the household set-up flow asks for, and who may complete it.
51. How notifications reach a phone when the app is closed, without a cloud
   push service.
52. Building and publishing for iOS needs a Mac and an Apple developer
   account, and the App Store has friction with the GPL.

## [Admin panel](design/technical/clients/web-admin.md)

53. Is the admin panel only for admins, or does every member use it for
   their own settings?
54. Is first-run setup done here, and what does it cover?
55. Are settings screens generated from each feature's description, as in
   the earlier voice assistant?

## [Voice page](design/technical/clients/web-voice.md)

56. Is a voice page a household device, a personal one, or either, depending
   on how it was opened?
57. Does it need a sign-in or pairing? In the earlier voice assistant the
   voice page had no login at all.
58. Can it be typed to as well as spoken to?

## [Feedback](design/technical/server/feedback.md)

59. How the server signs in to GitHub: a token the admin enters, a relay the
   project hosts, or a prefilled link only?
60. Is a report always reviewed by a person before it is sent, and by whom:
   the reporter, or an admin?
61. May any member file a report, including by voice?
62. How duplicates are avoided.

## [Email](design/technical/server/email.md)

63. Which providers: any IMAP server, Gmail, Outlook?
64. How a person signs in to their account, and where the credential is
   kept.
65. How much mail is kept on the server and in each client's cache.
66. How copied HTML and email HTML are drawn safely.
67. How the "copy the login code" behaviour finds a code in an email.

## [Clipboard](design/technical/server/clipboard.md)

68. Is clipboard sync on by default, and between which devices?
69. How large items, such as images and files, are handled.
70. How untrusted HTML is drawn safely.
71. How search stays fast over years of history.
72. How long history is kept.

## [Data and sync](design/technical/server/data-and-sync.md)

73. How the log handles household data that several people can see.
74. How long history is kept, and how old events are trimmed.
75. How search stays fast over years of history. This is research still to
   do.
76. Whether there is any data to bring over from the earlier voice
   assistant.

## [A2UI](design/technical/a2ui.md)

77. Who writes the spoken form of a screen: the system feature, or the AI
   model?
78. Which screens are hand-built and which are described with A2UI.
79. Whether a generated surface can be saved and reused, and by whom.
80. What a generated surface may do when its content came from an untrusted
   source, such as an email.
81. Whether any Rust implementation of A2UI exists, and whether the A2UI
   project would accept or list one.
82. Whether A2UI suits screens our own code defines locally, and what it
   costs in latency.
83. How each AI provider produces A2UI, including through a command-line
   tool.
84. The contents of our catalog.

## [Server](design/technical/server/README.md)

85. What the server runs on for the first release: a home server, a
   Raspberry Pi, a container? Which processor types?
86. How it is installed and updated: a single binary, a container image, a
   package?
87. How backups are made and restored.
88. Which database the server uses.

## [Networking](design/technical/server/networking.md)

89. How a non-technical person gets a browser to trust the server's
   certificate authority.
90. How the server is found on the home network when a device is first
   paired.

## [Protocol](design/technical/server/protocol.md)

91. The full list of messages, and how the protocol is versioned.
92. How audio travels: on the same connection or a separate one.
93. The exact pairing steps for a personal device and for a household
   device. See
   [identity-and-sharing.md](design/technical/server/identity-and-sharing.md).
94. The full list of capabilities, and how a catalog version is expressed.

## [Voice](design/technical/voice/README.md)

95. Echo: how a device avoids hearing its own answer.
96. Whether audio shares the device's connection or has its own.
97. What the numbers for a fast voice turn are, and how they are tested.

## [Speech to text](design/technical/voice/speech-to-text.md)

98. Which local model is the default, given accuracy, speed on low-power
   hardware and licence.
99. Which cloud providers are supported first, beyond Deepgram.
100. Whether transcription runs on the server only, or also on capable
   devices.
101. The silence timings, and whether a person can tune them.
102. How another language is added.

## [Text to speech](design/technical/voice/text-to-speech.md)

103. Which local voices are offered, given quality and licence.
104. Which cloud providers are supported first.
105. Whether speech is produced on the server only, or also on capable
   devices.
106. How another language is added.

## [Licensing and hardware](design/technical/licensing-and-hardware.md)

107. Which speech models and voices have licences that allow selling
   hardware. See [voice](design/technical/voice/README.md).
108. Whether preinstalling a vendor's AI command-line tool on hardware is
   ever wanted. It would need that vendor's commercial terms.

## [Repository layout](design/technical/repository.md)

109. The build order of the parts. There is no roadmap yet; it is decided
   after the technical details are clear.
110. How work is reviewed and tested. The earlier project suffered from long
   review rounds, heavy tests and documents used as changelogs.
111. Which machines are used to test the desktop client, the Android app and
   voice hardware.
112. Whether to create the Cargo workspace and CI before planning is
   finished. For now the answer is no.

## [Visual design](design/visual/README.md)

113. Three or four words for how it should feel, and products whose look you
   admire.
114. Does our own identity replace "mimic the host desktop" as the default
   look? The desktop brief asked for mimicry by default; the later decision
   for one recognisable look points the other way. If so, mimicry could
   remain as an optional theme.
115. Do the existing characters and the amber and mint colour language carry
   over, or does the identity start fresh?
116. Can a person choose a different theme, and how far may it differ?
117. Light and dark: both, and which is the default?

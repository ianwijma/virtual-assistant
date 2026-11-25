# Open questions

Every open question, in one list. This is the document the owner answers
from. Each question also sits at the end of the design document it belongs
to, which is linked in its heading.

How this list is kept:

- When a question is answered, it is removed here and from its design
  document, the answer is written into the design, and a line is added to
  [decisions.md](decisions.md).
- When an answer raises a new question, or leaves a point to confirm, it is
  added here and to its design document. It is not asked separately.
- Numbers are for answering by number. They change when the list changes.

Planning order: the technical details first, then modules. The roadmap
comes after that.

## To confirm

These are readings of earlier answers. Each stands as written in the design
unless corrected.

1. A household device announces only who a personal notification is for.
   It gives a person their own information when it recognises them and they
   ask. Should it also read content out unprompted once it knows the person
   is there?
2. A wake word belongs to an assistant, and the device setting switches
   listening on for the assistants assigned to that device. Or is the wake
   word itself chosen per device?
3. A personal assistant is on a household device only if it is assigned
   there. It does not follow its person automatically.
4. Household things are shared by default, and personal sources such as
   email stay private until shared. Or is everything shared by default?
5. Account switching on a computer covers both different people in one
   household and one person's accounts on different servers.
6. The switching passcode is four to six digits.


## [Identity and sharing](design/technical/server/identity-and-sharing.md)

7. What the sign-in flow of a household device is, and who may set one up:
   any member, or only an admin?
8. Whether a new device can also be added without typing the password, such
   as with a code from a device that is already signed in.
9. Account switching: is the passcode per account, how long is it, and is it
   also asked for when the computer wakes?
10. Which of the two ways to handle unrecognised voices is built, or both.
11. What a child's restricted role may do, as distinct from a guest.
12. Does a shared item appear in the other person's own views, or in a
   separate "shared with me" place?
13. Which things count as household things and are shared by default.
14. When a soft-deleted person's data is erased for good, and whether it can
   be restored.

## [Assistants](design/technical/voice/assistants.md)

15. Is there always a household assistant?
16. Does each person have a private memory with an assistant?
17. Who may assign an assistant to a device: can a person put their own
   assistant on a household device, or only an admin?
18. Which devices an assistant may act on: only the speaker's own, or any
   device in the household?

## [Summoning](design/technical/voice/summoning.md)

19. The states and transitions themselves.
20. Which device answers when several hear the wake word: the loudest, the
   first, the nearest?
21. Whether a follow-up without the wake word is allowed, and for how long.
22. How sure speaker identification must be before personal data is spoken,
   and what the fallback is: a PIN, or a confirmation on the phone?
23. Which words work without a wake word, such as "stop" while an alarm
   rings.

## [Wake word](design/technical/voice/wake-word.md)

24. Which detector to use, and whether a detection is confirmed by
   transcribing the same audio.
25. Whether custom wake words can be created by the household, and how.
26. Where the desktop client detects the wake word.
27. How false wakes and missed wakes are measured.

## [Speaker identification](design/technical/voice/speaker-identification.md)

28. How a person enrols their voice, and on which device.
29. How sure a match must be, and whether there is a "probably this person"
   level between known and guest.
30. Where voice data is stored, and how it is removed.

## [Notifications and routing](design/technical/server/notifications-and-routing.md)

31. What a routing rule is made of: the kind of event, a schedule, the
   target devices?
32. Besides a person's own devices, can a rule target a household device or
   another person?
33. What happens when no rule matches.
34. Do quiet hours and "do not disturb" exist per person, per device, or
   both?
35. Which actions can be taken on a notification from another device
   (dismiss, reply, open), and what if the source device is off?
36. How the "copy the login code" behaviour works: on the server, on the
   desktop, or both.

## [AI providers](design/technical/server/ai-providers.md)

37. Can an assistant or a person override the household configuration with
   their own provider?
38. Where a subscription's command-line tool runs: on the server, or on a
   person's desktop?
39. What an assistant may do without asking, and what needs confirmation.
   The earlier project's risk classes (read, change, message, money,
   security) are a candidate.
40. Does each person have a private memory with an assistant, separate from
   household memory?
41. How each provider produces A2UI screens. See
   [A2UI](design/technical/a2ui.md).

## [Modules](design/technical/modules/README.md)

42. Which modules are in the first release.
43. Can one tool belong to several modules, and is a module only a grouping,
   or also where a tool is written?
44. Can an assistant be given a module with some of its tools switched off?
45. Which tools need confirmation before they act.
46. Whether Home Assistant integration is in the first release.

## [Clients](design/technical/clients/README.md)

47. Which features of each client must work with no server at all.

## [Desktop client](design/technical/clients/desktop.md)

48. Which features must work with no server at all.
49. Where the wake word is detected on a desktop.
50. How notifications, clipboard access, global hotkeys and window control
   work across Linux desktops on X11 and Wayland. This is research still to
   do, and the limits on Wayland are a known risk.
51. The numbers that define "snappy", and the tests for them.
52. The list of actions a shortcut can be bound to, and how the shortcut
   system works.

## [Phone and tablet app](design/technical/clients/mobile.md)

53. What the household set-up flow asks for, and who may complete it.
54. How notifications reach a phone when the app is closed, without a cloud
   push service.
55. Building and publishing for iOS needs a Mac and an Apple developer
   account, and the App Store has friction with the GPL.

## [Admin panel](design/technical/clients/web-admin.md)

56. Is the admin panel only for admins, or does every member use it for
   their own settings?
57. Is first-run setup done here, and what does it cover?
58. Are settings screens generated from each feature's description, as in
   the earlier voice assistant?

## [Voice page](design/technical/clients/web-voice.md)

59. Is a voice page a household device, a personal one, or either, depending
   on how it was opened?
60. Does it need a sign-in or pairing? In the earlier voice assistant the
   voice page had no login at all.
61. Can it be typed to as well as spoken to?

## [Feedback](design/technical/server/feedback.md)

62. How the server signs in to GitHub: a token the admin enters, a relay the
   project hosts, or a prefilled link only?
63. Is a report always reviewed by a person before it is sent, and by whom:
   the reporter, or an admin?
64. May any member file a report, including by voice?
65. How duplicates are avoided.

## [Email](design/technical/server/email.md)

66. Which providers: any IMAP server, Gmail, Outlook?
67. How a person signs in to their account, and where the credential is
   kept.
68. How much mail is kept on the server and in each client's cache.
69. How copied HTML and email HTML are drawn safely.
70. How the "copy the login code" behaviour finds a code in an email.

## [Clipboard](design/technical/server/clipboard.md)

71. Is clipboard sync on by default, and between which devices?
72. How large items, such as images and files, are handled.
73. How untrusted HTML is drawn safely.
74. How search stays fast over years of history.
75. How long history is kept.

## [Data and sync](design/technical/server/data-and-sync.md)

76. How the log handles household data that several people can see.
77. How long history is kept, and how old events are trimmed.
78. How search stays fast over years of history. This is research still to
   do.
79. Whether there is any data to bring over from the earlier voice
   assistant.

## [A2UI](design/technical/a2ui.md)

80. Who writes the spoken form of a screen: the system feature, or the AI
   model?
81. Which screens are hand-built and which are described with A2UI.
82. Whether a generated surface can be saved and reused, and by whom.
83. What a generated surface may do when its content came from an untrusted
   source, such as an email.
84. Whether any Rust implementation of A2UI exists, and whether the A2UI
   project would accept or list one.
85. Whether A2UI suits screens our own code defines locally, and what it
   costs in latency.
86. How each AI provider produces A2UI, including through a command-line
   tool.
87. The contents of our catalog.

## [Server](design/technical/server/README.md)

88. What the server runs on for the first release: a home server, a
   Raspberry Pi, a container? Which processor types?
89. How it is installed and updated: a single binary, a container image, a
   package?
90. How backups are made and restored.
91. Which database the server uses.

## [Networking](design/technical/server/networking.md)

92. How a non-technical person gets a browser to trust the server's
   certificate authority.
93. How the server is found on the home network when a device is first
   paired.

## [Protocol](design/technical/server/protocol.md)

94. The full list of messages, and how the protocol is versioned.
95. How audio travels: on the same connection or a separate one.
96. The exact pairing steps for a personal device and for a household
   device. See
   [identity-and-sharing.md](design/technical/server/identity-and-sharing.md).
97. The full list of capabilities, and how a catalog version is expressed.

## [Voice](design/technical/voice/README.md)

98. Echo: how a device avoids hearing its own answer.
99. Whether audio shares the device's connection or has its own.
100. What the numbers for a fast voice turn are, and how they are tested.

## [Speech to text](design/technical/voice/speech-to-text.md)

101. Which local model is the default, given accuracy, speed on low-power
   hardware and licence.
102. Which cloud providers are supported first, beyond Deepgram.
103. Whether transcription runs on the server only, or also on capable
   devices.
104. The silence timings, and whether a person can tune them.
105. How another language is added.

## [Text to speech](design/technical/voice/text-to-speech.md)

106. Which local voices are offered, given quality and licence.
107. Which cloud providers are supported first.
108. Whether speech is produced on the server only, or also on capable
   devices.
109. How another language is added.

## [Licensing and hardware](design/technical/licensing-and-hardware.md)

110. Which speech models and voices have licences that allow selling
   hardware. See [voice](design/technical/voice/README.md).
111. Whether preinstalling a vendor's AI command-line tool on hardware is
   ever wanted. It would need that vendor's commercial terms.

## [Repository layout](design/technical/repository.md)

112. The build order of the parts. There is no roadmap yet; it is decided
   after the technical details are clear.
113. How work is reviewed and tested. The earlier project suffered from long
   review rounds, heavy tests and documents used as changelogs.
114. Which machines are used to test the desktop client, the Android app and
   voice hardware.
115. Whether to create the Cargo workspace and CI before planning is
   finished. For now the answer is no.

## [Visual design](design/visual/README.md)

116. Three or four words for how it should feel, and products whose look you
   admire.
117. Does our own identity replace "mimic the host desktop" as the default
   look? The desktop brief asked for mimicry by default; the later decision
   for one recognisable look points the other way. If so, mimicry could
   remain as an optional theme.
118. Do the existing characters and the amber and mint colour language carry
   over, or does the identity start fresh?
119. Can a person choose a different theme, and how far may it differ?
120. Light and dark: both, and which is the default?

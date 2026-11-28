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
| [4. Proposals to review](#4-proposals-to-review) | High-level designs written as proposals | The owner agrees or corrects |
| [5. To research](#5-to-research) | Questions that need investigation, not an opinion | An agent researches, the owner agrees |
| [6. Visual design](#6-visual-design) | Questions about the look and feel | The owner, in a separate thread |

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

A. "The frosted design of iOS 27" is read as Apple's Liquid Glass, the
   glass material of the current iOS and macOS. [glass]
B. "Heavy inspiration" is read as: the look is inspired by Apple's and
   is still our own, the same on every device, so the earlier decision
   that it is recognisable as ours stands. [visual identity]
C. Low-fidelity mockups and examples are kept as web pages in
   `docs/design/visual/`, which a person opens in a browser and an agent
   can read. [mockups]
D. All four feelings were chosen: calm, warm, precise and playful. This
   is read as: the interface is calm and precise, and the assistants are
   warm and playful. [visual identity]
E. An accent is read as two colours, a main one and a second one for
   the backdrop, so "two custom colours" makes one accent. [colour]
F. On a household device, a recognised person's accent shows for the
   length of the conversation, and then the device's or the household's
   accent returns. [colour]
G. The glass and the text are neutral, and colour comes from the
   accent. Our own backdrop takes the accent. [glass] [colour]
H. In the second review, the ticks are read as agreement: one shipped
   typeface, two densities and an open icon set are agreed. [typography]
   [shape]
I. A character shows seven states: idle, listening, thinking, speaking,
   muted, waiting and not recognised. This was decided by the agent and
   has not been reviewed. [assistant visuals]
J. "Two modes" of motion is read as: reduced motion follows the device's
   setting, can also be switched on per device in our settings, and is
   used on a device too slow for full motion. [motion]
K. One typeface family is used for everything; headings have no typeface
   of their own. This was decided by the agent. [typography]
L. The first values of the tokens were chosen by the agent: the greys,
   the five accents, the status colours, the type scale, the spacing, the
   corners and the timings. [tokens]
M. The desktop settings are read as: opened from the launcher and shown
   in the launcher's own window as another view, with the admin panel's
   side bar and page. [visual desktop]
N. The phone's bar is read as four buttons a person sets plus a fifth,
   fixed button for the overview of all areas, not four in all.
   [visual phone]
O. "As quiet as possible" is read with its bar for a lost connection,
   and the saved content under it stays usable, not only readable.
   [components]
P. Growing from what was touched is read as the rule for every sheet,
   pop-up and new page in every client, with titles and other shared
   parts moving into place. [motion]
Q. "Really platform specific" is read as five reasons: room on the
   screen, how the device is operated, how far away it is read, what the
   device cannot do, and what only that device has. [visual]
R. From the same answer, the setup of a new device is taken to be the
   same design as the first-run setup, and the question of saving a
   setting is asked once for every client. [visual admin panel]
   [components]
S. The request for home-like and Dutch names is read as: "Hearth" is
   dropped, not kept beside the new candidates. [visual identity]
T. "It depends on the device" is read as: desktop and admin panel start
   compact, phone and tablet start roomy, and the density is the thing
   that can be changed, not the layout. [shape]
U. "I like the Phosphor icons" is read as the choice of the set. Whether
   the chosen item is filled was not answered and stays a question.
   [shape]
V. The four devices of the accent preview are read as the phone app,
   the tablet, the desktop and the admin panel. [colour]
W. The answer on the accent picker is read as: pairs that go together
   first, with Shuffle, and the two-handle wheel behind the link for a
   free choice. Shuffle takes the place of picking two colours at
   random. [colour]
Z. The list of changes with before and after is read as planned and not
   part of the first designs. [components]
X. "A bit of both" is read as: the figure in the assistant's colour, and
   the backdrop and the buttons in the person's accent. [colour]
Y. From the answer on responsive layout, the app's own settings are
   taken to be the same design as the desktop settings and the admin
   panel, with fewer columns on a narrow screen. [visual]
AC. "The two-tone accent as the background of the panels" is read as:
   the plain base and panels carry a little of both colours of the
   accent. [colour]
AE. The tint was chosen from a board that showed it in dark too, so it
   is taken to hold in dark. [colour]
AH. "In the audit, agents, latency" is read as: the request timeline of
   the admin panel records that a screen was composed. [components]
AI. "Characters" is read as the preferred word for an assistant's look,
   with "figure" kept for its drawn body. [assistant visuals]

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
5. How the research threads are run after the merge: one thread that
   starts several others by area, each raising a pull request?
   [repository]

## 4. Proposals to review

None at the moment. A proposal is a section headed "Proposal" in a design
file, written for the owner to agree to or correct.

## 5. To research

These need investigation. An agent does the work
and writes the outcome into the design; the owner then agrees or
corrects it. They are sorted by how much depends on them.

This work is done in separate threads, after the planning pull request is
merged. It is not started from the planning thread.

How the threads are run is not settled. The likely form: one thread
starts several others, by area. Each does its research, raises a pull request that updates the design, and puts
anything that needs the owner's answer into this list.

Research is kept as small as possible. It is done online, from
documentation and other projects. A small prototype is made only when a
question cannot be settled otherwise. The aim is a quick first working
product, not a complete study.

6. Which database the server uses, and how search stays fast over years
   of history. The owner leans towards PostgreSQL, for being open source
   and for its extensions such as time series, unless there is a strong
   case for SQLite. [server], [data], [clipboard]
7. How notifications, clipboard access, global hotkeys and window
    control work across Linux desktops on X11 and Wayland. The limits on
    Wayland are a known risk. [desktop]
8. How notifications reach a phone when the app is closed. To compare:
   what works on Android without Google's push service, what iOS allows,
   and simply accepting Google's and Apple's push services with a small
   relay if one is needed. Include what happens when the connection is
   lost. [mobile]
9. Which wake word detector to use, and whether a detection is confirmed
   by transcribing the same audio. Wake words are typed in freely, so
   the detector must accept any word. Finding the wake word in the
   transcript is the fallback, though transcripts can get the word
   wrong. Also: whether training a device per person, from several
   places in the room, improves detection. [wake word]
10. Which small local speech-to-text model and small local voice are the
   defaults, which better ones are suggested in set-up, and which of
   them have licences that allow selling hardware. [speech to text],
   [text to speech], [licensing]
11. Which of the services the system suggests have a referral programme,
   and on what terms. [licensing]
12. Echo: how a device ignores its own voice while it speaks and still
   hears another voice, so that "stop" works. [voice]
13. How each AI provider produces A2UI screens, including through a
    command-line tool. [ai providers], [a2ui]
14. Whether any Rust implementation of A2UI exists, and whether the A2UI
    project would accept or list one. [a2ui]
15. Whether A2UI suits screens our own code defines locally, and what it
    costs in latency. [a2ui]
16. How copied HTML is drawn with its formatting, safely, on each
   platform: a sandboxed frame in a browser, and whatever the Rust
   desktop client and the phone apps can use. [clipboard]
17. How the admin panel and the voice page get HTTPS that a browser
   trusts, for a non-technical person. To compare: certificates through
   Tailscale, a proxy domain per installation that the project provides,
   the person's own certificates, accepting the browser's warning at
   first, and any other way found. An AI assistant could also walk a
   person through the set-up. [networking]
18. How a reply tag is lined up with the moment in the speech where it
   stands. [reply tags]
19. Signing in with Google or Microsoft for email, after the first
   release: who registers the application with each company, and what
   Google's review of applications that read mail involves. [email]
20. Can the development virtual machine run an Android emulator with
   sound and virtual machines inside it? Both need virtualisation inside
   a virtual machine. The Rust toolchain is not installed on it yet
   either. [repository]
21. How a vendor's command-line tool is installed and signed in to from
   the admin panel, including inside a container. [ai providers]
22. Whether a notification can open the email in the person's own email
   application, on a phone and on a desktop. [email]
23. How the vault encrypts its secrets, so that control of the running
   server does not expose them, and where that key is kept. Kept small;
   if it slows the work, the first release relies on disk encryption.
   [vault]
24. Whether finding the server by mDNS works reliably from the Android
   and iOS apps, and on home networks that separate Wi-Fi clients.
   [pairing]
25. Whether audio on the device's connection is fast enough, and whether
   JSON is fast enough for syncing large histories. To be measured when
   the first devices exist. [protocol]
26. How a desktop that listens always knows that it is being spoken to,
   and not a colleague or a call. [summoning]
27. How the server program replaces itself and restarts safely, and how
   it is rolled back when a new version fails to start. [server]

## 6. Visual design

These are answered in the visual design thread. The candidates that
several of them refer to are on
[the direction board](design/visual/examples/direction-board.html), a page
to open in a browser. Each group is needed before its part is designed in
detail.

### The feel and the name

28. Which products do you admire the look of, besides Apple's? [visual
   identity]
29. What should set the look apart from Apple's, so that it is
   recognisable as ours: the colour, the backdrop, the assistants, the
   shape, or something else? See the table above. [visual identity]
30. The web addresses heem.com, heem.app, heem.nl and heem.dev are
   taken. Which address does the project use? [visual identity]
31. Is the name said the Dutch way or the English way when it is spoken,
   such as in a video or by an assistant? [visual identity]
32. The glass drop is the faintest of the marks at the size of a small
   icon. Is it made bolder at small sizes, or does a solid form of it
   stand in there? [visual identity]

### The glass

33. What are the three levels of see-through: the designed glass, a
   thicker one and solid? Is the level set per device or per person?
   [glass]
34. Do the pictures of a gallery change by themselves, like a photo
   frame, and how often? [glass]
35. Can the launcher find out how bright the windows behind it are? This
   is to be looked into for after the first release. [glass]
36. With reduced motion, is the backdrop still, or does it drift slowly?
   [glass]
37. Does the backdrop also move on an old tablet and in low-power mode?
   [glass]
38. Where the desktop cannot blur, is the see-through launcher without
   blur something a person switches on, with our own backdrop as the
   default there? [glass]

### The colours

39. Where does the warning about a colour that is hard to read appear:
   under the wheel, where "Checked: text stays readable" is on the
   board? [colour]
40. Does the wheel set only the hue, or also how light and how strong a
   colour is? [colour]
41. How is the wheel used with a keyboard, and can a value be typed?
   [colour]
42. Where can an accent be chosen besides the admin panel: on the device
   itself, in its own settings? [colour]
43. Is a character's colour picked with the same picker as the accent,
   and who may change it? [colour]
44. What happens when an assistant's colour and the person's accent are
   the same, or clash? [colour]
45. Should the set have more built-in accents, such as a pink or a red?
   [colour]
46. Does Graphite return later as a built-in accent? [colour]
47. Are there colours to avoid, and is anyone in the household colour-
   blind? [colour]
48. Which setting for light and dark does a new household tablet start
   with? [colour]

### Typography

49. Which languages and scripts must be covered later, beyond what Inter
   covers? [typography]

### Shape, spacing and icons

50. Where is a device's density changed: in the admin panel, on the
   device itself, or both? [shape]
51. Is the density one setting for a whole device, or can it differ per
   app or area? [shape]
52. Can the density of a household tablet be changed, or is it always
   roomy, since it is read from a distance? [shape]
53. Is there an illustration style, for empty screens and first-run
   setup? [shape]

### Motion and sound

54. Is the sound of a timer or an alarm that ends also off unless
   switched on, or is it the one sound that is always on? [motion]
55. Which sounds are in the set, and who makes them? [motion]
56. Where are sounds and vibration switched on: per device, per person,
   or for the household? [motion]
57. Where a toolkit cannot grow a new page out of the thing that was
   touched, what is shown: the sheet rising from below, or a plain fade?
   [motion]
58. Does everything that opens end with the light overshoot, or only
   sheets? [motion]
59. How is a device found to be too slow for full motion: measured by
   the client, or switched by hand only? [motion]

### Tokens and components

60. Agree to the first values, after seeing them in the example
   components and the mockups. [tokens]
61. Agree to the example components as the base for the rest.
   [components]
62. Does a dangerous action, such as removing an assistant, go through
   the Save bar too, or does it ask and act at once? [components]
63. When two devices changed the same thing while one was out of reach,
   which change wins, and is the person told? [components]
64. Is a person told when changes that waited have been sent, or does
   the mark only disappear? [components]
65. Does the chat's history show that a screen was composed to everyone,
   or only in an advanced or debug mode? [components]
66. Does a sheet with unsaved input ask before it closes by a touch
   outside it? [components]
67. How long does a card that was asked for stay large, and is the large
   form the same as the sheet a touch opens? [components]
68. Which components come next? The proposal is the ones the mockups
   need: the launcher's search and results, a sheet, a menu, the tab bar
   and the side bar, a table for logs, the chat, and each card of the
   A2UI catalog. [components]

### Assistant visuals

69. In which style are the full figures drawn, when they are redesigned
   later? Five styles are on the figure style board. [assistant visuals]
70. Does a figure have a mouth that moves when it talks, and arms? Both
   are ideas for the thread on the figures. [assistant visuals]
71. Is the figure of the first release a rendered three-dimensional one,
   or the flat one for now? [assistant visuals]
72. How much more room does a screen keep for a later figure: how much
   wider and taller than the figure for now? [assistant visuals]
73. Who draws the figures, and how many are there in the first release?
   [assistant visuals]
74. How does a person give their own assistant a look: by choosing from
   a set of figures, by adjusting parts such as colour and clothing, or
   by supplying their own drawing? [assistant visuals]
75. How playful is the default household assistant: cute, friendly, or
   calm? [assistant visuals]
76. Is the voice page arranged like the tablet, with the figure on a
   stage? [assistant visuals]
77. May a card cover part of the character, or does it always sit clear
   of the head? [assistant visuals]
78. Does a whole figure move across the screen only while nothing else
   is shown, and stand still once a card appears? [assistant visuals]
79. What does an assistant without a figure show: a sound wave, as on
   the tablet board, or something else? [assistant visuals]
80. How large is the character where the assistant is not the subject,
   such as in the desktop launcher and on the phone's home screen?
   [assistant visuals]
81. May a person bring their own figure, such as a character they like
   from elsewhere? The project cannot ship characters that belong to
   others. [assistant visuals]
82. From the research: which of the three routes above do the first
   figures take? [assistant visuals]

### The clients

83. What makes one notification more important than another in the
   Overview's list: its kind, its age, or what a person set? [visual]
84. On a narrow screen, how is a new notification shown while another
   area than the Overview is open: a dot on the bar, or nothing?
   [visual]
85. At which width does a notification change from a row in the list to
   a card at the top right? [visual]
86. Does the household tablet, which nobody owns, have four pinned
   areas, and who sets them? [visual]
87. At which widths does the layout change? The board shows one column
   under 600, two from 600 to 1000 and three above. [visual]
88. In two columns, do the destinations become a rail of icons, as on
   the board? [visual]
89. Does the launcher of the desktop client, which has a fixed size,
   also follow this, or is it the one window that does not fold?
   [visual]
90. Which devices are the references for the designs: which phone, which
   tablet, which monitor size? [visual]
91. Are settings screens generated from each feature's description, so
   that one definition serves the phone app, the desktop client and the
   admin panel? A2UI makes this possible, but one solution may not suit
   every device. This is decided once there are visual designs of the
   app and the admin panel. [visual]
92. When the settings close by a click elsewhere with unsaved changes,
   are they kept for when the launcher is opened again, or is the person
   asked? [visual desktop]
93. After how long does the launcher return to its neutral state: one
   minute, or a time a person sets? [visual desktop]
94. What else does the tray icon's menu hold: the state of the
   connection, a way to quit? [visual desktop]
95. In the settings, does Esc first clear a search and only then return
   to the list? [visual desktop]
96. Can a notification on the desktop be answered from the keyboard?
   [visual desktop]
97. Does a question from an assistant stay on screen until it is
   answered? [visual desktop]
98. Which views of the launcher have a preview, and which are a list
   only? [visual desktop]
99. Is the order of the actions in the launcher taken from this person's
   own use, from the household's, or from both? [visual desktop]
100. Does the window change size when it goes from a list to a list with
   a preview, or is it always the wide size? [visual desktop]
101. What does the sheet show when there are more areas than fit: does
   it scroll, or grow taller? [visual phone]
102. Does the fixed button show a grid icon, the word "All", or both?
   [visual phone]
103. Which four are on the bar of a new person: Overview, the assistant,
   Timeline and Chat? [visual phone]
104. Can any area be put on the bar, a single list such as Shopping
   included? [visual phone]
105. Where is the line of text on the call screen switched on: in the
   settings, or with a button on the call screen itself? [visual phone]
106. Does the line of text also show what the person says, or only what
   the assistant says? [visual phone]
107. Where is the first screen chosen: in the app's own settings, or in
   the admin panel with a person's other settings? [visual phone]
108. What does a touch on a clipboard item do: copy it to this phone, or
   open it? [visual phone]
109. How often does the figure on the idle screen change, and can a
   touch on the dots change it? [visual tablet]
110. Which assistant is shown first: the one used last, or a fixed
   order? [visual tablet]
111. Does the clock move now and then, to protect the screen? [visual
   tablet]
112. How does a tablet without a light sensor know the room is dark: by
   the time of day, by its camera, or does a person set the hours?
   [visual tablet]
113. What can be set for the dark on a tablet: only which of the two
   screens is used, or also the hours and how dim it is? [visual tablet]
114. Is the time before a conversation closes 20 or 30 seconds at first?
   [visual tablet]
115. Does the character show that the conversation is about to close?
   [visual tablet]
116. Which figure greets in the welcome, before the household has chosen
   or named an assistant? [visual admin panel]
117. Which languages does the welcome show, and in which is the setup
   offered at first? [visual admin panel]
118. Is the language chosen on the welcome itself, as the board shows,
   or in a step after it? [visual admin panel]
119. Where on the phone app's call design do the two set-up choices and
   the note for guests go? Ideas are on the voice page board. [visual
   voice page]
120. On a wide screen, such as a tablet on its side, is the page
   arranged like the phone or like the tablet's stage? [visual voice
   page]

### The mockups

121. Agree to each mockup, or say what to change in it. [mockups]
122. Admin panel: is "Undo" offered for every change in the audit log,
   or only for changes that can be reversed safely? [mockups]
123. Voice page: does the page remember on that browser that it was set
   up as a personal or a household device? [mockups]

### To research

An agent does this work and the owner agrees to the outcome.

124. A search of the trade mark registers of the EU, the Benelux, the UK
   and the US for "Heem", in the classes for software and devices. The
   registers could not be reached in the checks so far. [visual
   identity]
125. How fast the blur is on an old tablet and in the launcher, measured
   on real devices. [glass]
126. Whether Slint, Jetpack Compose, SwiftUI and CSS can each grow a
   sheet or a page out of one element and keep a shared element, such as
   a title, moving between two screens. [motion]
127. How much power a three-dimensional figure uses on an old tablet
   that is on all day. No figures were found. [assistant visuals]

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
[pairing]: design/technical/server/pairing.md
[voice]: design/technical/voice/README.md
[reply tags]: design/technical/voice/reply-tags.md
[speech to text]: design/technical/voice/speech-to-text.md
[text to speech]: design/technical/voice/text-to-speech.md
[licensing]: design/technical/licensing-and-hardware.md
[repository]: design/technical/repository.md
[visual]: design/visual/README.md
[visual identity]: design/visual/identity.md
[glass]: design/visual/glass.md
[colour]: design/visual/colour.md
[typography]: design/visual/typography.md
[shape]: design/visual/shape-and-spacing.md
[motion]: design/visual/motion.md
[assistant visuals]: design/visual/assistant-visuals.md
[tokens]: design/visual/tokens.md
[components]: design/visual/components.md
[mockups]: design/visual/mockups/README.md
[visual desktop]: design/visual/desktop.md
[visual phone]: design/visual/phone.md
[visual tablet]: design/visual/tablet.md
[visual admin panel]: design/visual/admin-panel.md
[visual voice page]: design/visual/voice-page.md

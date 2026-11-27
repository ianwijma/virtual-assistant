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
E. The accent is chosen from a fixed set, not from any colour, so that
   each one can be checked for readable text. [colour]
F. On a household device, a recognised person's accent shows for the
   length of the conversation, and then the device's or the household's
   accent returns. [colour]
G. The glass and the base colours are neutral, and colour comes from the
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
30. Who is the design for first: the power user at the desktop, or the
   whole household at a tablet, guests and children included? When a
   dense screen and a friendly screen conflict, which wins? [visual
   identity]
31. Are there candidates for the product name? Does the visual work go
   on under the working title until there is one? [visual identity]
32. When are a logo and an app icon needed: now, or after the design
   language is settled? [visual identity]

### The glass

33. Who sets the wallpaper of a household tablet: an admin, in the admin
   panel? Is it one picture, or several that change? [glass]
34. Can a wallpaper also be set on a personal phone, in the settings
   window of the desktop client, or in the admin panel, or do those
   always show our own backdrop? [glass]
35. Does our own backdrop move slowly, or is it still? [glass]

### The colours

36. Which accent does a new household start with? [colour]
37. Should the set have more accents, such as a pink or a red, and how
   many is enough? [colour]
38. Does each assistant have its own colour? If so, which one shows
   while an assistant is active on a household device: the assistant's,
   or the accent of the person it recognised? [colour]
39. Is a person's accent also the colour that marks them elsewhere, such
   as on the account switch of a shared computer, or beside an item they
   added to a shared list? [colour]
40. Is light a pure white, or a slightly tinted, softer white? [colour]
41. Are there colours to avoid, and is anyone in the household colour-
   blind? [colour]
42. A tablet in a room has its light or dark setting fixed by whoever
   set it up. Should a household tablet go dark at night by itself?
   [colour]

### Typography

43. Which monospace typeface is shipped for logs and timelines?
   JetBrains Mono is a candidate with a fitting licence. [typography]
44. Which languages and scripts must be covered later, beyond what Inter
   covers? [typography]

### Shape, spacing and icons

45. Are icons outlined or filled, and which open set is used: Lucide,
   Phosphor, Tabler or another? [shape]
46. Is there an illustration style, for empty screens and first-run
   setup? [shape]

### Motion and sound

47. Are sounds part of the identity, such as a tone when an assistant
   starts listening or a timer ends? [motion]
48. Does the phone use vibration as part of the feel? [motion]
49. How is a device found to be too slow for full motion: measured by
   the client, or switched by hand only? [motion]

### Tokens and components

50. In which format is the source of the tokens kept in the repository,
   and which tool generates the four themes from it? The Design Tokens
   format of the W3C community group is a candidate. This is research
   still to do. [tokens]
51. Agree to the first values, after seeing them in the example
   components and the mockups. [tokens]
52. Agree to the example components as the base for the rest.
   [components]
53. Which components come next? The proposal is the ones the mockups
   need: the launcher's search and results, a sheet, a menu, the tab bar
   and the side bar, a table for logs, the chat, and each card of the
   A2UI catalog. [components]

### Assistant visuals

54. In which style are the figures drawn: flat and simple, soft and
   three-dimensional, or hand-drawn? Examples of each are to be made
   before this is answered. [assistant visuals]
55. Who draws the figures, and how many are there in the first release?
   [assistant visuals]
56. How does a person give their own assistant a look: by choosing from
   a set of figures, by adjusting parts such as colour and clothing, or
   by supplying their own drawing? [assistant visuals]
57. How playful is the default household assistant: cute, friendly, or
   calm? [assistant visuals]
58. How large is the character on each screen: the whole screen on the
   tablet, a small part of the launcher on the desktop? [assistant
   visuals]
59. Does a figure have a colour of its own, apart from the accent?
   [assistant visuals]

### The clients

60. What does a tablet in a room show when nobody is using it: the
   character, a clock, running timers, or nothing? [visual]
61. Does the admin panel use glass as much as the other clients, or is
   it plainer because it holds dense tables and logs? [visual]
62. Should a screen that an assistant composed look different from a
   built-in screen, so that a person can tell? [visual]
63. Which client's mockup is worked out in detail first, and which
   screens of it matter most? [visual]
64. Which devices are the references for the mockups: which phone, which
   tablet, which monitor size? [visual]
65. Are settings screens generated from each feature's description, so
   that one definition serves the phone app, the desktop client and the
   admin panel? A2UI makes this possible, but one solution may not suit
   every device. This is decided once there are visual designs of the
   app and the admin panel. [visual]

### The mockups

66. Agree to each mockup, or say what to change in it. [mockups]
67. Desktop: how does a person go from searching to talking to the
   assistant: the Tab key, a prefix, or a shortcut of its own? The
   mockup shows Tab and a shortcut. [mockups]
68. Desktop: does the launcher open on the screen that holds the
   pointer, or on the main screen? [mockups]
69. Desktop: is the settings window opened from the launcher only, or
   also from an icon in the system tray? [mockups]
70. Phone: the tab bar has five tabs: Home, Alerts, Clipboard, Lists and
   More. Are these the right five, and may "Notifications" be shortened
   to "Alerts" to fit? [mockups]
71. Phone: what does a touch on a clipboard item do: copy it to this
   phone, or open it? [mockups]
72. Tablet: does the clock on the idle screen move now and then, to
   protect the screen? [mockups]
73. Tablet: after how long without speech does the listening panel
   close? [mockups]
74. Admin panel: at phone width the side bar becomes a tab bar with
   People, Devices, Assistants and More. Is that the right choice?
   [mockups]
75. Admin panel: which accent does the admin panel show: that of the
   person signed in, or the household's? [mockups]
76. Admin panel: the request timeline shows the first words a person
   said. Who may see them? [mockups]
77. Admin panel: is "Undo" offered for every change in the audit log, or
   only for changes that can be reversed safely? [mockups]
78. Voice page: does the page remember on that browser that it was set
   up as a personal or a household device? [mockups]

### To research

An agent does this work and the owner agrees to the outcome.

79. What Slint, Jetpack Compose on older Android, SwiftUI and CSS can
   each draw: blur behind a surface, and at what speed. [glass]
80. Whether the launcher window can show the blurred desktop behind it
   on Linux, on X11 and on Wayland. [glass]
81. How each character is animated so that it runs in Slint, Jetpack
   Compose, SwiftUI and a browser from one source. [assistant visuals]

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

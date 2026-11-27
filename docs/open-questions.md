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
   can read. [visual]

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
to open in a browser. The first three groups are the current step; the
rest are needed before their part is designed.

### The feel

28. Three or four words for how it should feel. Some to choose from:
   calm, warm, friendly, playful, quiet, precise, technical, fast, soft,
   bold. [visual identity]
29. Which products do you admire the look of, besides Apple's?
   [visual identity]
30. What should set the look apart from Apple's, so that it is
   recognisable as ours: the colour, the backdrop, the assistants, the
   shape, or something else? [visual identity]
31. Who is the design for first: the power user at the desktop, or the
   whole household at a tablet, guests and children included? When a
   dense screen and a friendly screen conflict, which wins?
   [visual identity]
32. Should it feel like a thing for the home, warm and soft, or like a
   tool, cool and sharp? [visual identity]
33. Are there candidates for the product name? Does the visual work go on
   under the working title until there is one? [visual identity]
34. When are a logo and an app icon needed: now, or after the design
   language is settled? [visual identity]

### The glass

35. Where is glass used: on every surface, or only on what floats above
   the content, such as bars, the launcher, sheets and cards? Apple uses
   it only for the floating layer and keeps the content itself plain.
   [glass]
36. How far does the glass go: a plain frosted blur, or the full effect
   with bent light at the edges and moving highlights? The full effect
   is the most recognisable as Apple's, and the most work to draw outside
   Apple's devices. The direction board shows three strengths. [glass]
37. What is behind the glass: our own soft colour backdrop, a wallpaper
   the person chooses, the colour of the active assistant, or the real
   desktop behind the launcher? These can differ per client. [glass]
38. May a person choose the backdrop? A theme cannot be chosen; is a
   wallpaper a theme? [glass]
39. Is the glass clear and neutral, or does it carry a tint of the accent
   colour? [glass]
40. May a device that is too slow for the blur show a simpler material,
   such as a flat translucent tint? This would be the same look in colour
   and shape, without the blur. [glass]
41. Does the look follow the device's settings for reduced transparency
   and increased contrast, by making the glass more solid? [glass]
42. What does glass look like on the black, dimmed screen of a tablet in
   low-power mode? [glass]

### The colours

43. Which colour direction, A to E on the direction board, or which mix
   of them? [colour]
44. Agree to the proposed parts of the palette: backdrop, glass, text,
   accent, status and assistant colours. [colour]
45. Is there one accent colour for everyone, or may a person choose their
   own accent? A theme cannot be chosen; is an accent a theme? [colour]
46. Does each assistant have its own colour, and does the screen take
   that colour while the assistant is active? [colour]
47. Does each person have a colour, to show whose account is active on a
   shared computer, or who added an item to a shared list? [colour]
48. Is dark a true black, which saves power on a tablet with an OLED
   screen, or a dark grey with a slight tint? [colour]
49. Is light a pure white, or a slightly tinted, softer white? [colour]
50. Are the status colours the usual green, amber and red? [colour]
51. How readable must text be: the common standard of a contrast of 4.5
   to 1 for normal text, or stricter? [colour]
52. Are there colours to avoid, and is anyone in the household
   colour-blind? [colour]
53. A tablet in a room has its light or dark setting fixed by whoever set
   it up. Should a household tablet go dark at night by itself? [colour]
54. "Follows the device" means there is no switch for light and dark in
   our own settings. Is that right, or should a person be able to
   override it per device? [colour]

### Typography

55. Is one typeface shipped with every client, so that text looks the
   same everywhere? The other choice is each platform's own font, which
   is lighter but looks different per device. Apple's San Francisco
   cannot be used outside Apple's devices. [visual]
56. Which character should the typeface have: neutral (such as Inter or
   Geist), geometric and friendly (such as Manrope or Figtree), or
   rounded (such as Nunito)? [visual]
57. Do headings get their own typeface, or is one family used for
   everything? [visual]
58. Which languages and scripts must the typeface cover later? [visual]
59. Does text follow the text size set on the device? [visual]

### Shape, spacing and icons

60. How round are corners: slightly, clearly, or pill-shaped controls as
   in Apple's design? The direction board shows the three. [visual]
61. Is there one density, or a compact one for the desktop and the admin
   panel and a roomy one for touch and for the tablet across a room?
   [visual]
62. Are icons outlined or filled, and is an open icon set used (such as
   Lucide, Phosphor or Tabler) or do we draw our own? Apple's symbols
   cannot be used. [visual]
63. Is there an illustration style, for empty screens and first-run
   setup? [visual]

### Motion and sound

64. How much does the interface move: fluid and springy as in Apple's
   design, or quick and plain? The desktop must appear within 100 ms, so
   does the launcher appear with no animation at all? [visual]
65. Are sounds part of the identity, such as a tone when an assistant
   starts listening or a timer ends? [visual]
66. Does the phone use vibration as part of the feel? [visual]

### Assistant visuals

67. What is a character: an abstract shape such as an orb or a wave, a
   simple face, or a full illustrated figure? The reply tags include a
   wink, an eye roll, a nod and a shake of the head, which need eyes and
   a head. [visual]
68. How do two assistants differ: by colour only, by shape, or as fully
   different characters? [visual]
69. How does a person give their own assistant a look: by choosing from a
   set, by adjusting parts such as colour and eyes, or by supplying an
   image? [visual]
70. How playful is the default household assistant: cute, friendly, or
   calm and abstract? [visual]
71. Which states must a character show? The proposal is idle, listening,
   thinking, speaking, muted, waiting for the server, and voice not
   recognised. [visual]
72. How large is the character on each screen: the whole screen on the
   tablet, a small part of the launcher on the desktop? [visual]

### The clients

73. What does a tablet in a room show when nobody is using it: the
   character, a clock, running timers, or nothing? [visual]
74. Does the admin panel use glass as much as the other clients, or is it
   plainer because it holds dense tables and logs? [visual]
75. Should a screen that an assistant composed look different from a
   built-in screen, so that a person can tell? [visual]
76. Which client is drawn first as a mockup, and which screens of it
   matter most? [visual]
77. Which devices are the references for the mockups: which phone, which
   tablet, which monitor size? [visual]
78. Are settings screens generated from each feature's description, so
   that one definition serves the phone app, the desktop client and the
   admin panel? This is decided once there are visual designs of the app
   and the admin panel. [visual]

### To research

An agent does this work and the owner agrees to the outcome.

79. What Slint, Jetpack Compose on older Android, SwiftUI and CSS can
   each draw: blur behind a surface, bent light, and at what speed.
   [glass]
80. Whether the launcher window can show the blurred desktop behind it on
   Linux, on X11 and on Wayland. [glass]
81. How each character is animated so that it runs in Slint, Jetpack
   Compose, SwiftUI and a browser from one source. [visual]

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

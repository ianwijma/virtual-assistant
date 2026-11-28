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
AJ. "The choice screen we have on other devices" is read as the pane of
   the setup of a new device that asks: personal or household. [visual
   voice page]
AK. Decisions 334 to 383 in [decisions](decisions.md) were made by
   the agent on 28 November 2026, at the owner's request, and are to be
   validated by the owner. [visual]
AL. Vibration is read like sound: off in a conversation unless switched
   on, and otherwise on. [motion]

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

28. Which web address does the project use? heem.com, heem.app, heem.nl
   and heem.dev are taken. A prefix is likely, such as getheem.com. This
   is decided after the trade mark search. [visual identity]

### The glass

29. Can the launcher find out how bright the windows behind it are? This
   is to be looked into for after the first release. [glass]

### The colours

30. Which pink and which red are built in, with which second colour, and
   what are they called? [colour]

### Typography

31. Which language read from right to left comes first, and which
   typeface covers its script? [typography]

### Shape, spacing and icons


### Motion and sound


### Tokens and components

32. Agree to the first values, after seeing them in the example
   components and the mockups. [tokens]
33. Agree to the example components as the base for the rest.
   [components]

### Assistant visuals

34. In which style are the full figures drawn, when they are redesigned
   later? Five styles are on the figure style board. [assistant visuals]
35. Does a figure have a mouth that moves when it talks, and arms? Both
   are ideas for the thread on the figures. [assistant visuals]
36. Is the figure of the first release a rendered three-dimensional one,
   or the flat one for now? [assistant visuals]
37. How much more room does a screen keep for a later figure: how much
   wider and taller than the figure for now? [assistant visuals]
38. Who draws the figures, and how many are there in the first release?
   [assistant visuals]
39. How does a person give their own assistant a look: by choosing from
   a set of figures, by adjusting parts such as colour and clothing, or
   by supplying their own drawing? [assistant visuals]
40. How playful is the default household assistant: cute, friendly, or
   calm? [assistant visuals]
41. May a person bring their own figure, such as a character they like
   from elsewhere? The project cannot ship characters that belong to
   others. [assistant visuals]
42. From the research: which of the three routes above do the first
   figures take? [assistant visuals]

### The clients

43. In two columns, do the destinations become a rail of icons, as on
   the board? [visual]
44. Which devices are the references for the designs: which phone, which
   tablet, which monitor size? [visual]
45. Are settings screens generated from each feature's description, so
   that one definition serves the phone app, the desktop client and the
   admin panel? A2UI makes this possible, but one solution may not suit
   every device. This is decided once there are visual designs of the
   app and the admin panel. [visual]
46. When the settings close by a click elsewhere with unsaved changes,
   are they kept for when the launcher is opened again, or is the person
   asked? [visual desktop]
47. Which views of the launcher have a preview, and which are a list
   only? [visual desktop]
48. Does the window change size when it goes from a list to a list with
   a preview, or is it always the wide size? [visual desktop]
49. Does the line of text also show what the person says, or only what
   the assistant says? [visual phone]
50. Which languages does the welcome show, and in which is the setup
   offered at first? [visual admin panel]

### The mockups

51. Agree to each mockup, or say what to change in it. [mockups]

### To research

An agent does this work and the owner agrees to the outcome.

52. A search of the trade mark registers of the EU, the Benelux, the UK
   and the US for "Heem", in the classes for software and devices. The
   registers could not be reached in the checks so far. [visual
   identity]
53. How fast the blur is on an old tablet and in the launcher, measured
   on real devices. [glass]
54. Whether Slint, Jetpack Compose, SwiftUI and CSS can each grow a
   sheet or a page out of one element and keep a shared element, such as
   a title, moving between two screens. [motion]
55. How much power a three-dimensional figure uses on an old tablet that
   is on all day. No figures were found. [assistant visuals]

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

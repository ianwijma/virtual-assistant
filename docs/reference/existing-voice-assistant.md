# What the existing voice assistant teaches us

The earlier project is `ianwijma/personal-voice-assistance`: a TypeScript
voice assistant. It is not ported. This page records what it does, what to
keep as ideas, and what to avoid. It was surveyed on 25 November 2026 at its
`main` branch, commit `88a6cef0`.

Most findings were checked in its code. Its test counts, latency numbers and
review outcomes come from its documents only.

## What it is

- One Node.js process for one household. One port serves the voice page, the
  admin page, an admin API and a WebSocket.
- About 155,000 lines of code and 154,000 lines of tests in 45 packages. It
  was built in 12 days, almost entirely by agents.
- It has never been run on real hardware or against real services: no real
  microphone, no real Raspberry Pi, no real phone.

## Summoning

This is the part the owner finds hardest to understand in daily use.

- **There is no wake-word detector.** The server transcribes all audio, and
  a wake is a match on the transcript. A misheard word misses a wake or
  causes one. The default phrases include spellings of mishearings.
- **The phrase must start the utterance.** If background speech runs into
  it, the wake is missed.
- **Windows stack up.** A follow-up window opens on an accepted utterance as
  well as after a reply, and some modes answer everything.
- **The decision is spread over about nine places,** with settings from four
  layers: assistant, assignment, device type and device.
- **Nothing is recorded.** A dropped utterance is shown only to an admin
  page with a tester switched on, without the reason. A missed or false wake
  leaves no trace.
- **Nothing arbitrates between devices.** Every device that hears the phrase
  answers.
- **Echo is handled on text,** by comparing words. A reply that contains the
  wake phrase can stop itself.
- **A wake-word detector was tried and rejected.** The model missed 21% of
  wakes in a test with synthetic voices on a desktop processor.

For the new design: one state machine, every decision logged with its
reason, a real detector with a confidence score confirmed by transcription,
arbitration between devices, and speaker identification before permissions.

## Identity

- People are a list of names. There are no logins, roles or permissions.
- The voice page has no login. A device claims its own identity.
- The person for a request is the device's default person. There is no
  speaker identification.
- Because nobody is authenticated, actions that send messages, spend money
  or affect security are always refused.
- Anyone at any device can use the owner's Claude subscription.

This is the area the new system designs from scratch.

## Ideas worth keeping

- **One gateway for every tool call.** It checks who is acting, whether the
  module is on, and the risk of the tool (read, change, message, money,
  security) against a household policy.
- **One function per decision,** such as "may this device reveal this
  item", and it fails closed.
- **Settings screens generated from a schema,** where each page states where
  it belongs.
- **Typed services between modules,** instead of modules calling each other
  directly.
- **A spoken fallback for everything visual.**
- **Node pairing:** a one-time code, a credential the server stores only as
  a hash, and a pinned certificate.
- **The report design:** a draft first, secrets scrubbed, the conversation
  never included, the owner reviews it, and it is sent exactly once. Without
  a token it offers a prefilled link.
- **A trace of each voice turn** with timing marks, so latency claims rest
  on numbers.
- **The assistant record:** personality, voice, look, allowed modules and
  tools.
- **The visual characters:** 19 animated looks driven by the audio, and a
  colour language where amber is the assistant and mint is the user.
- **Tests:** in-memory fakes for the store, the clock and notifications, and
  one contract test suite run against every implementation.
- **Releases:** a dry run by default and an approval step.

## Things to avoid

- **Documents as a changelog.** The architecture document is 200 KB of
  review notes, and one paragraph in it is 25 KB.
- **Heavy host code.** The module host is 3,600 lines, and the presenting
  and notification engines are about 1,600 each.
- **Reviews that do not converge.** Some parts had 16 review rounds.
- **A hand-written mock server** of 4,000 lines that copies the real one.
- **Timing tests that fail on slow machines.** Four are switched off.
- **A database called on the audio thread,** which forced size limits
  everywhere.
- **Nested settings as JSON in a text box.**
- **Hard-coded repository and image names.**

## What it lacks against the new plan

| Need | State in the existing project |
|---|---|
| Users, roles, sharing | None |
| Sync between devices | Server push only; no event log |
| Notification rules | None; delivery targets devices, not people |
| Email | Deferred, never built |
| Accounts and OAuth | Deferred; a secret belongs to one module field |
| Dynamic UI | A closed set of five card kinds; A2UI was considered and not used |
| Codex | Researched, not built |
| Wake word on the device | Not built |

## Its modules

Clock, weather, Home Assistant, assistant controls, timers, alarms,
calculator, knowledge, system status, web search, lists, notifications,
kitchen, media, reminders, images, calendar, memory, broadcast, briefing,
bin day, presence, news, routines and report.

Which of these the new system needs is decided later.

## Licences to watch for hardware

- The default local voices are for non-commercial use only. Several other
  voices are free for commercial use.
- Some speech recognition models have no clear licence.
- The free weather service used is for non-commercial use.
- The pronunciation data for local voices is GPLv3, which fits this
  project.

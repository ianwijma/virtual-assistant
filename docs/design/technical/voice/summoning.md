# Summoning

The process that decides whether an assistant answers, for whom, and on
which device. Part of [the voice design](README.md).

Status: draft. This is designed fresh. The earlier voice assistant's rules
are not copied.

## Design

Summoning is one explicit state machine on the server:

1. **The wake word is detected.** See [wake-word.md](wake-word.md).
2. **The speaker is identified** against enrolled voices. See
   [speaker-identification.md](speaker-identification.md).
3. **Permissions are resolved.** The assistant acts as that person. An
   unrecognised voice gets guest abilities.
4. **One device answers.** If several devices heard the wake word, exactly
   one responds.

Every decision to wake or to ignore is logged with its reason and shown in
the [admin panel](../clients/web-admin.md).

A desktop client can also be set to listen always, and any client can be
typed to. Typing skips steps 1 and 2, because the device's owner is known.

## Why it is designed this way

In the earlier voice assistant it is hard to tell why an assistant did or
did not answer. A survey of its code found the causes:

- there is no wake-word detector; a wake is a match on transcribed text;
- the decision is spread over about nine places and four layers of
  settings;
- windows in which no wake word is needed open implicitly and stack up;
- nothing is recorded when an utterance is ignored;
- nothing arbitrates when several devices hear the same phrase.

See [the reference](../../../reference/existing-voice-assistant.md).

This leads to four rules:

- **One place decides.** The state machine is the only thing that starts
  or ends listening.
- **Every transition is recorded,** including the reason an utterance was
  ignored.
- **Windows are explicit.** If a follow-up needs no wake word, that is a
  named state with a visible end.
- **Settings stay shallow.** The effective behaviour of a device can be
  shown on one screen.

## Open questions

- The states and transitions themselves.
- Which device answers when several hear the wake word: the loudest, the
  first, the nearest?
- Whether a follow-up without the wake word is allowed, and for how long.
- How sure speaker identification must be before personal data is spoken,
  and what the fallback is: a PIN, or a confirmation on the phone?
- Which words work without a wake word, such as "stop" while an alarm
  rings.

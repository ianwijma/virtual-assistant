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
   unrecognised voice is answered only by a guest assistant, at guest
   level. Any other assistant gives a short refusal, such as "Sorry, I
   don't recognise your voice", and does nothing. The refusal is how it
   works for now: a voice can go unrecognised for innocent reasons, such
   as distance or a mask, so this will be looked at again.
4. **One device answers.** If several devices heard the wake word, exactly
   one responds: the one that heard it loudest and clearest, which is
   usually the one the person is nearest to. The choice is one replaceable
   step, so that a weighting per device can be added later, for a device
   that hears well from a corner.

A voice that is not matched with enough certainty counts as unrecognised.
There is no in-between level and no fallback such as a PIN. If this goes
wrong too often, speaker identification itself is improved.

Three words work without the wake word, each only in its own situation:

| Word | When |
|---|---|
| "Stop" | While a timer or an alarm rings on that device |
| "Stop" | While the assistant is speaking |
| "Snooze" | While an alarm rings on that device |

A follow-up without the wake word is possible only when the assistant's
reply asked for it, or just after a household device has spoken a
notification. See [reply tags](reply-tags.md).

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

## Proposal: the states

This section is proposed and waits for the owner's review.

Each device that can listen is in exactly one state. The server holds
the state and is the only thing that changes it.

| State | What happens | Leaves when |
|---|---|---|
| Idle | The device listens only for wake words | A wake word is heard |
| Choosing a device | The server waits a short moment, about 200 ms, for other devices that heard the same wake word, and picks the one that heard it best | A device is picked; the others go back to idle |
| Identifying | The voice is compared with enrolled voices | It is a known person, or unrecognised |
| Refusing | A non-guest assistant tells an unrecognised voice it cannot help | The refusal has been spoken |
| Listening | The request is turned into text | The person stops talking, or says nothing for a few seconds |
| Thinking | The AI provider works and may call tools | An answer is ready, or it fails |
| Speaking | The answer is spoken and any screen is shown | It finishes, or the person says "stop" or talks over it |
| Follow-up | The device listens without the wake word for a short time | Someone speaks, or the time runs out |
| Ringing | A timer or an alarm rings; only "stop" and "snooze" are heard | It is stopped or snoozed |

```text
Idle -> Choosing a device -> Identifying -> Listening -> Thinking -> Speaking -> Idle
                                  |                                      |
                                  v                                      v
                              Refusing -> Idle                       Follow-up -> Listening
                                                                         |
                                                                         v
                                                                        Idle
```

- **Follow-up** is entered after a reply with the "keep listening" tag,
  and after a household device has spoken a notification.
- **Typing** enters at Thinking. The device's owner is known, so the
  first three states are skipped.
- **A conversation** is the chain of turns that follow each other. Its
  context is kept until the pause that ends a conversation has passed.
- **Every change of state is logged,** with the device, the assistant,
  the person if known, and the reason. A wake that ends in Listening with
  nothing said is logged as a false wake.
- **A device that is not picked** logs "another device answered".

Still to be thought through: a desktop set to listen always has no wake
word. How it knows that it is being spoken to is not covered here.

## Open questions

- Agree to the proposed states, or correct them.
- How a desktop that listens always knows it is being spoken to.

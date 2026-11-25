# Timers, alarms and reminders

Part of [the server design](README.md).

Status: draft. Only the outline is decided.

## Design

- Timers, alarms and reminders are a system feature in the first release,
  with a [module](../modules/README.md) that gives an assistant the tools
  to set, list and cancel them.
- **One rings where it was set.** A person can ask for it to ring
  somewhere else, such as on their phone.
- Timers and alarms are household things: everyone can see them and stop
  them. See [identity and sharing](identity-and-sharing.md).
- "Stop" and "snooze" work without the wake word while one rings. See
  [summoning](../voice/summoning.md).

## Open questions

- What the three are, and how they differ: is a reminder a notification
  at a set time, routed like any other?
- What happens when the device that should ring is off or unreachable.
- Whether they repeat, such as an alarm on every weekday.

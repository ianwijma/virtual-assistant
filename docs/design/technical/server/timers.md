# Timers, alarms and reminders

Part of [the server design](README.md).

Status: draft. Only the outline is decided.

## Design

- Timers, alarms and reminders are a system feature in the first release,
  with a [module](../modules/README.md) that gives an assistant the tools
  to set, list and cancel them.
- **The three differ in what they do:**

  | Kind | What it does |
  |---|---|
  | Timer | Counts down, then rings on a device until stopped |
  | Alarm | Rings on a device at a set time, until stopped |
  | Reminder | Is a notification at a set time, routed by the person's rules like any other. See [notifications and routing](notifications-and-routing.md) |

- Alarms and reminders can repeat, such as on every weekday.
- **If the device that should ring is off or unreachable, it falls back
  like a notification.** It goes to the phone of the person who set it.
  If nobody was recognised, it goes to the other household devices. A
  device that holds its own copy still rings by itself when only the
  server is unreachable.
- **One rings where it was set.** A person can ask for it to ring
  somewhere else, such as on their phone.
- Timers and alarms are household things: everyone can see them and stop
  them. See [identity and sharing](identity-and-sharing.md).
- "Stop" and "snooze" work without the wake word while one rings. See
  [summoning](../voice/summoning.md).

## Open questions

None at the moment.

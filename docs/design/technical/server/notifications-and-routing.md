# Notifications and routing

The notification centre on the server and how a notification reaches a
device. Part of [the server design](README.md).

Status: draft.

## The notification centre

- Every notification lives on the server, per person, with its state:
  unread, dismissed or replied.
- State is shared. Dismissing or replying on one device updates the server,
  and every other device follows.

## Sources

- **On the server:** email, reminders, calendar and the assistants. These
  reach a device only when delivered.
- **On a desktop:** local applications, such as a chat program or a
  finished build. The desktop is the notification service of that machine,
  so it shows the popup at once. It then forwards the notification to the
  server, where it is routed like any other and kept in history.

## One notification centre, on every personal device

- Every personal device shows the notification centre: the person's own
  notifications and the household's.
- **Notifications are controlled from anywhere.** What a person does to a
  notification on one device, such as dismissing it, holds on all of
  them. It is one system, not a set of separate inboxes.
- **A notification can be acted on from another device,** in the first
  release: replied to, such as a chat message that arrived on the
  desktop, or opened on the device it came from.

## Routing

- Each person configures where their own notifications go.
- **A rule has four parts:**

  | Part | Meaning | Example |
  |---|---|---|
  | What | The kind of notification: a source, or everything | Email |
  | When | Always, or a schedule | Work hours |
  | Where | The targets | The home-office desktop |
  | How | How it arrives | Silently, with a sound, or spoken aloud |

  Rules are checked in order, and the first one that matches is used.
- **A rule can send to the person's own devices, to household devices and
  to other people.**
- **A household source has rules too.** A household email address, for
  example, can be routed to every household device and to people's own
  devices.
- **There is always a fallback.** A notification that matches no rule is
  never lost. A personal one goes to its owner's phone. A household one
  goes to the admin's phone and into the history.
- **Quiet hours exist per person and per device.** A person's quiet hours
  hold back their notifications everywhere. A device can also be set
  quiet, such as a bedroom tablet at night, whoever the notification is
  for.
- Routing can follow a schedule. For example: the home-office device
  during work hours, and the phone always.
- An admin can view and change a person's routing, to help when
  notifications do not arrive.
- The system does not rely on guessing the nearest device, because that is
  unreliable.

## Household devices

A household device says only who a personal notification is for, such as
"Ian, you have a new email". The content stays on the person's own
devices. The device gives that person the content only when they ask for
it with the wake word and their voice is recognised. It never reads the
content out unprompted, even when it knows the person is there. Household notifications, such as a broadcast, go to household
devices and to personal devices.

## When the server is down

- Local notifications still appear on the desktop and queue for upload.
- Server notifications wait on the server until the device reconnects.

## Open questions

- What happens to a reply or an "open" when the device the notification
  came from is off.

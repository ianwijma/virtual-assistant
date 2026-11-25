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

## Routing

- Each person configures where their own notifications go.
- **A rule can send to the person's own devices, to household devices and
  to other people.**
- **A household source has rules too.** A household email address, for
  example, can be routed to every household device and to people's own
  devices.
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

- What a routing rule is made of: the kind of event, a schedule, the
  target devices?
- What happens when no rule matches.
- Do quiet hours and "do not disturb" exist per person, per device, or
  both?
- Which actions can be taken on a notification from another device
  (dismiss, reply, open), and what if the source device is off?
- How the "copy the login code" behaviour works: on the server, on the
  desktop, or both.

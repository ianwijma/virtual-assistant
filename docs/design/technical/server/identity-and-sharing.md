# Identity and sharing

People, devices, roles, and who may see what. Part of
[the server design](README.md).

Status: draft. The earlier voice assistant had no users or roles, so this
is designed from scratch.

## People and roles

Every person has an account on the server, named by their email address.

| Role | What it is |
|---|---|
| Admin | Manages people, devices, assistants and the server |
| Member | An ordinary person in the household |

The first release has these two roles only. A restricted role, for
children, comes later. A guest is not a role: it is a voice the system
does not recognise.

## Signing in

**There are no passwords.** To sign in, a person enters their email
address, the server sends a one-time code to it, and they enter that code.
The short passcode for switching accounts on a computer is a separate,
local thing.

- **The server sends the codes through a mail account the admin enters**
  during first-run setup. A relay hosted by the project may come later; it
  is not built first, because abuse could get it blocked for everyone.
- **Without internet no email arrives.** A person can then sign in a new
  device with a code from a device where they are already signed in, or
  with a code an admin issues for them. If neither is available, they
  cannot sign in until the internet is back. Devices that are already
  signed in keep working.
- A code from a device that is already signed in also works when there is
  internet, as a quick way to add a device.

## Devices

There are two kinds of device:

| Kind | Example | Used by |
|---|---|---|
| Household | A tablet in the kitchen in kiosk mode | Everyone |
| Personal | A desktop or a phone | One person |

- **One app for both.** When the app is installed, the person chooses to
  set it up as a personal device or as a household device. Each choice has
  its own sign-in flow.
- A personal device is paired to one person.
- **Only an admin adds a household device.** A device announces itself to
  the server it finds on the network, or is set up with an invite the
  admin created: a code or a QR code that can be saved and passed on, for
  example in a group chat. See [pairing](pairing.md). The device does
  nothing until an admin approves it. For each invite the admin can set
  how many devices it may add and how long it is valid. Both are
  unlimited unless set. An admin can withdraw an invite at any time.
- **Several accounts on one device.** A computer can hold more than one
  account. Each account has its own passcode of four to six digits. It is
  asked for when switching to that account, when the client starts, and
  when the computer is unlocked. The accounts can be different people in
  one household, or one person's accounts on different servers.
- A personal device still receives household events, such as a "dinner is
  ready" broadcast.
- A personal device can be a direct target, such as a call to one person's
  phone.

## Ownership and sharing

- Everything belongs to one person or to the household.
- **Private by default.** Nothing is shared until its owner shares it.
- **Household things are shared by default.** A shopping list is one list
  for the whole household. Personal sources, such as email, stay private
  until shared.
- **Who connected a source decides which it is.** A source a person
  connects through their own account, such as their email or a chat
  service, is private to them. A source an admin connects for the
  household is a household thing.
- **These are household things, shared with everyone by default:** lists
  (such as a shopping list or the pantry), timers and alarms, household
  devices and assistants, and announcements.
- A share can be to named people or to the whole household.
- **A shared item appears in two places** for the person it is shared
  with: among their own items, marked with who shared it, and in a view
  that lists only what is shared with them.
- A person who is given a share can see it, and so can an assistant acting
  for that person.
- The owner shares one item or a whole source.

## Guests and unrecognised voices

What an unrecognised voice may do is configurable. As a starting point it
can do things that touch nobody's private data: set a timer, ask a
general question, ask for a joke, report a bug.

This is done with **guest assistants**. "Guest" is a setting of an
assistant:

- A guest assistant answers anyone, recognised or not. For an
  unrecognised voice it has only guest-level tools. When it recognises
  the speaker, it acts with that person's permissions, so it can answer
  "what is my name?".
- An assistant that is not a guest assistant gives an unrecognised voice
  a short refusal.
- There can be several guest assistants, each with its own wake words and
  modules. Examples are a "Hey Home" assistant for the house, and one
  whose wake word is "report feedback" and whose only job is to take a
  bug report or a suggestion.
- The default household assistant starts as a guest assistant.

See [assistants](../voice/assistants.md).

## Households and servers

- A household has one server.
- A second household means a second, separate server. Support for linking
  several servers is not needed for now.
- A person keeps things apart by having an account on each server, such as
  a personal account at home and a work account on a work server, and
  switching between them on the device.

## Removing a person

Removing a person is a soft deletion: their data is marked as removed. It
is never erased, and the person can always be restored. An admin has no
way to erase it from inside the system.

## Admin access

- An admin can read all data for now. Clipboard history is the
  exception: the admin panel has no screen for other people's. The person who deploys the system
  owns the box and the network.
- This is a server setting that can be tightened later.
- Admin access to other people's data is logged.

## Who is acting

This is worked out in layers, cheapest first:

1. **Device ownership,** on personal devices.
2. **Speaker identification,** on household devices. It is a convenience,
   not security, because a voice can be recorded and replayed. See
   [speaker identification](../voice/speaker-identification.md).

There is no PIN and no confirmation on a phone as a third layer. A voice
that is not recognised with enough certainty is simply unrecognised. See
[summoning](../voice/summoning.md).

On a household device:

- **Unprompted, personal content is not spoken.** A notification says
  "Ian, you have a new email" and nothing more, unless that person has
  allowed the device to say more. See [email](email.md).
- **Personal information is spoken only when its owner asks for it by
  voice.** The person must have used the wake word and their voice must
  have been recognised. That shows they want the information then and
  there. Recognising someone is never a reason to start reading things
  out.
- **Nobody is tracked through the home.** The system knows a person is at
  a device only at the moment they use the wake word and their voice is
  recognised.

## Open questions

- What a restricted role for children may do, once it is added.

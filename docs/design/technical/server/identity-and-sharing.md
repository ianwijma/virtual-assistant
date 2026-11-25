# Identity and sharing

People, devices, roles, and who may see what. Part of
[the server design](README.md).

Status: draft. The earlier voice assistant had no users or roles, so this
is designed from scratch.

## People and roles

Every person has an account on the server, named by their email address.

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

- **Admin:** manages people, devices and modules.
- **Member:** an ordinary person in the household.
- **Restricted:** for children and guests.

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
- **Only an admin adds a household device,** in two steps. The admin
  creates an invite, as a code or a QR code that can be saved and passed
  on, for example in a group chat. Whoever sets up the device scans or
  enters it, and the device registers with the server. The device does
  nothing until an admin approves it.
- **Several accounts on one device.** A computer can hold more than one
  account, and a person switches between them with a short passcode,
  possibly four to six digits. The accounts can be different people in one
  household, or one person's accounts on different servers.
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
- A share can be to named people or to the whole household.
- A person who is given a share can see it, and so can an assistant acting
  for that person.
- The owner shares one item, a rule (such as a sender or a label), or a
  whole source. For example, a person shares most of an inbox with a
  partner and keeps a birthday present private.

## Guests, children and unrecognised voices

What they may do is configurable. As a starting point, an unrecognised
voice can do things that touch nobody's private data: set a timer, ask a
general question, ask for a joke.

Two ways to set this up are being considered, and both may be offered:

- a separate assistant for people who are not recognised, with its own
  modules;
- one assistant for everyone that acts on personal things only when it
  recognises the person.

## Households and servers

- A household has one server.
- A second household means a second, separate server. Support for linking
  several servers is not needed for now.
- A person keeps things apart by having an account on each server, such as
  a personal account at home and a work account on a work server, and
  switching between them on the device.

## Removing a person

Removing a person is a soft deletion: their data is marked as removed, not
erased at once.

## Admin access

- An admin can read all data for now. The person who deploys the system
  owns the box and the network.
- This is a server setting that can be tightened later.
- Admin access to other people's data is logged.

## Who is acting

This is worked out in layers, cheapest first:

1. **Device ownership,** on personal devices.
2. **Speaker identification,** on household devices. It is a convenience,
   not security, because a voice can be recorded and replayed. See
   [speaker identification](../voice/speaker-identification.md).
3. **A confirmation** on the person's own device, or a PIN, for sensitive
   actions.

On a household device:

- **Unprompted, personal content is not spoken.** A notification says
  "Ian, you have a new email" and nothing more.
- **Personal information is spoken only when its owner asks for it by
  voice.** The person must have used the wake word and their voice must
  have been recognised. That shows they want the information then and
  there. Recognising someone is never a reason to start reading things
  out.
- **Nobody is tracked through the home.** The system knows a person is at
  a device only at the moment they use the wake word and their voice is
  recognised.

## Open questions

- A household device invite: how long is it valid, for how many devices,
  and can it be withdrawn?
- May an admin connect a source, such as a shared mailbox, for the whole
  household? It is written so for now.
- Account switching: is the passcode per account, how long is it, and is
  it also asked for when the computer wakes?
- Which of the two ways to handle unrecognised voices is built, or both.
- What a child's restricted role may do, as distinct from a guest.
- Does a shared item appear in the other person's own views, or in a
  separate "shared with me" place?
- Which things count as household things and are shared by default.
- When a soft-deleted person's data is erased for good, and whether it can
  be restored.

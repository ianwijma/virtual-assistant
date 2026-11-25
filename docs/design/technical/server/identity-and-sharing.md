# Identity and sharing

People, devices, roles, and who may see what. Part of
[the server design](README.md).

Status: draft. The earlier voice assistant had no users or roles, so this
is designed from scratch.

## People and roles

- **Admin:** manages people, devices and modules.
- **Member:** an ordinary person in the household.
- **Restricted:** for children and guests.

## Devices

There are two kinds of device:

| Kind | Example | Used by |
|---|---|---|
| Household | A tablet in the kitchen in kiosk mode | Everyone |
| Personal | A desktop or a phone | One person |

- A personal device is paired to one person.
- A personal device still receives household events, such as a "dinner is
  ready" broadcast.
- A personal device can be a direct target, such as a call to one person's
  phone.

## Ownership and sharing

- Everything belongs to one person or to the household.
- **Private by default.** Nothing is shared until its owner shares it.
- The owner shares one item, a rule (such as a sender or a label), or a
  whole source. For example, a person shares most of an inbox with a
  partner and keeps a birthday present private.

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

On a household device, personal content is not spoken. It says "Ian, you
have a new email" and nothing more.

## Open questions

- How a person signs in on a personal device: a password, a code from an
  already paired device, or something else?
- How a household device is added, and who may add one. Is it two apps, or
  one app with a household mode?
- Can one person be signed in on a shared computer, and how do they
  switch?
- What may a guest or a child do, and what may an unrecognised voice do?
- Once a household device recognises a voice, may it show or speak that
  person's own things?
- Is a share always to named people, or also to "the household"?
- Does a shared item appear in the other person's own views, or in a
  separate "shared with me" place?
- May an assistant used by one person read what another person shared with
  them?

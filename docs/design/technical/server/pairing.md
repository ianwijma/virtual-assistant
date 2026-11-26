# Pairing

How a device finds the server and becomes one of its devices. Part of
[the server design](README.md).

Status: draft. The rules it builds on are in
[identity and sharing](identity-and-sharing.md).

## Finding the server

1. The server announces itself on the home network (mDNS). An app lists
   the servers it finds, by household name.
2. If none is found, the person types the server's address, or scans a QR
   code that holds it.
3. A browser cannot search the network. The voice page and the admin panel
   are opened by their address.

A QR code or an invite carries the server's address and the fingerprint
of its key, so the device knows it is talking to the right server.

## A personal device

1. The app finds the server and shows its name. It remembers the server's
   key from now on.
2. The person enters their email address.
3. The server emails a one-time code, and the person enters it.
4. The server gives the device its own credential. The device keeps it in
   the operating system's secure storage. The server keeps only a hash.
5. The device reports its [capabilities](protocol.md), and sync starts.

Steps 2 and 3 can be replaced by a code or QR code from a device where the
person is already signed in, or by a code an admin issues. Both also work
without internet.

## A household device

It follows the personal flow as closely as it can. The difference is that
it ends by waiting for an admin's approval.

1. The app finds the server on the home network and shows its name, as
   for a personal device.
2. The person chooses "household device". The device announces itself to
   the server with a name and its capabilities: "I am here".
3. Its state is "waiting for approval", and it can do nothing yet.
4. Every admin is notified. One of them approves it in the admin panel,
   and can then name its room and assign assistants to it.
5. The server gives the device its credential, as for a personal device.

An invite, as a code or a QR code, is the other way to do steps 1 and 2.
It carries the server's address, so it also works when the server is not
found on the network. Approval is needed either way.

An admin can switch off announcing without an invite, so that only
invited devices can ask to join. That suits a network with strangers on
it.

## A voice page

1. The page is opened by its address. Without anything further it can
   talk to guest assistants.
2. The person chooses personal or household.
3. Personal follows steps 2 to 5 of a personal device. The credential is
   kept in the browser's storage.
4. Household follows steps 2 to 5 of a household device, or uses an
   invite that is typed in.

## Removing a device

- A person can remove their own devices. An admin can remove any device.
- Removing a device cancels its credential at once. The device returns to
  its first-run screen the next time it connects.

## Open questions

- Whether finding the server by mDNS works reliably from an Android app
  and an iOS app, and on home networks that separate Wi-Fi clients. This
  is research still to do.
- Whether a browser's storage is a good enough place for a voice page's
  credential, since clearing the browser's data signs the page out.

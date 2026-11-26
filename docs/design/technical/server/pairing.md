# Pairing

How a device finds the server and becomes one of its devices. Part of
[the server design](README.md).

Status: proposal. The rules it builds on are decided in
[identity and sharing](identity-and-sharing.md). The steps below are
proposed and wait for the owner's review.

## Proposal: finding the server

1. The server announces itself on the home network (mDNS). An app lists
   the servers it finds, by household name.
2. If none is found, the person types the server's address, or scans a QR
   code that holds it.
3. A browser cannot search the network. The voice page and the admin panel
   are opened by their address.

A QR code or an invite carries the server's address and the fingerprint
of its key, so the device knows it is talking to the right server.

## Proposal: a personal device

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

## Proposal: a household device

1. An admin creates an invite in the admin panel. It is a code and a QR
   code, and can be passed on.
2. The person setting up the device chooses "household device" and scans
   or enters the invite.
3. The device registers with a name and its capabilities. Its state is
   "waiting for approval", and it can do nothing yet.
4. Every admin is notified. One of them approves it in the admin panel,
   and can then name its room and assign assistants to it.
5. The server gives the device its credential, as for a personal device.

## Proposal: a voice page

1. The page is opened by its address. Without anything further it can
   talk to guest assistants.
2. The person chooses personal or household.
3. Personal follows steps 2 to 5 of a personal device. The credential is
   kept in the browser's storage.
4. Household follows steps 2 to 5 of a household device, with the invite
   typed in.

## Proposal: removing a device

- A person can remove their own devices. An admin can remove any device.
- Removing a device cancels its credential at once. The device returns to
  its first-run screen the next time it connects.

## Open questions

- Agree to these proposals, or correct them.
- Whether finding the server by mDNS works reliably from an Android app
  and an iOS app, and on home networks that separate Wi-Fi clients. This
  is research still to do.
- Whether a browser's storage is a good enough place for a voice page's
  credential, since clearing the browser's data signs the page out.

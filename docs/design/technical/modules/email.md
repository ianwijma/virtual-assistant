# Email module

Reading email in the system and reacting to its arrival. Part of
[the modules design](README.md).

Status: draft. Nothing like this exists in the earlier voice assistant.

## Design

- Email accounts are held by the server, and the server fetches the mail.
  It is always on, so an arriving email can be announced even when the
  desktop is off.
- Each account belongs to one person and is private by default. Its owner
  can share one email, a rule (such as a sender or a label), or the whole
  inbox. See [identity and sharing](../server/identity-and-sharing.md).
- A new email is an event. It becomes a notification that is routed like
  any other. See
  [notifications and routing](../server/notifications-and-routing.md).
- Clients read and search from a local cache.
- The system is for reading. Anything more opens the person's own email
  application.
- AI can summarise an email.

## Open questions

- Which providers: any IMAP server, Gmail, Outlook?
- How a person signs in to their account, and where the credential is
  kept.
- How much mail is kept on the server and in each client's cache.
- How copied HTML and email HTML are drawn safely.
- How the "copy the login code" behaviour finds a code in an email.

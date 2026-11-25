# Email

Reading email in the system and reacting to its arrival. Part of
[the server design](README.md).

Status: draft. Nothing like this exists in the earlier voice assistant.

## Design

Email is a feature of the system. A [module](../modules/README.md) gives
assistants the tools to use it.

- **Three ways to connect an account from the start:** any IMAP server,
  "Sign in with Google" and "Sign in with Microsoft".
- **The credential is kept on the server, encrypted, in the
  [vault](vault.md).** Devices never hold it.
- Email accounts are held by the server, and the server fetches the mail.
  It is always on, so an arriving email can be announced even when the
  desktop is off.
- Each account belongs to one person and is private by default. Its owner
  can share one email, a rule (such as a sender or a label), or the whole
  inbox. See [identity and sharing](identity-and-sharing.md).
- A new email is an event. It becomes a notification that is routed like
  any other. See
  [notifications and routing](notifications-and-routing.md).
- Clients read and search from a local cache.
- The system is for reading. Anything more opens the person's own email
  application.
- AI can summarise an email.

## Open questions

- Signing in with Google or Microsoft needs an application registered
  with each company, and Google reviews applications that read mail. Who
  registers them: the project, or each household's admin? This is
  research still to do.
- How much mail is kept on the server and in each client's cache.
- How copied HTML and email HTML are drawn safely.
- How the "copy the login code" behaviour finds a code in an email.

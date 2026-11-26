# Email

Telling a person that new email has arrived. Part of
[the server design](README.md).

Status: draft. Nothing like this exists in the earlier voice assistant.

## Design

The system does one thing with email: it notices that a new one has
arrived and notifies the person. It is not an email reader.

- **Mail is not stored.** The server does not keep a copy of anyone's
  mail, and clients have no mail cache. To read an email, a person opens
  their own email application.
- **Three ways to connect an account from the start:** any IMAP server,
  "Sign in with Google" and "Sign in with Microsoft".
- **The credential is kept on the server, encrypted, in the
  [vault](vault.md).** Devices never hold it.
- The server watches the account. It is always on, so an arriving email
  can be announced even when the desktop is off.
- Each account belongs to one person and is private by default. A
  household account is a household source. See
  [identity and sharing](identity-and-sharing.md).
- **What the notification says is configurable.** There are three
  levels:

  | Level | Example |
  |---|---|
  | The least | "Ian, you have a new email" |
  | With the title | Who it is from and its subject |
  | With a summary | A summary of the content, made by AI |

  For the higher levels the server reads the email as it arrives. It
  still does not keep it.
- A new email is an event. It becomes a notification that is routed like
  any other. See
  [notifications and routing](notifications-and-routing.md).

## Open questions

- Signing in with Google or Microsoft needs an application registered
  with each company, and Google reviews applications that read mail. Who
  registers them: the project, or each household's admin? This is
  research still to do.

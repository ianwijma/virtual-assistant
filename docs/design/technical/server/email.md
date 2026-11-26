# Email

Telling a person that new email has arrived, and acting on it. Part of
[the server design](README.md).

Status: draft. Nothing like this exists in the earlier voice assistant.

## Design

The system is built around new email: it notices that one has arrived,
notifies the person, and lets them act on it. It is not a full email
reader, and it does not mirror a mailbox.

- **New emails are kept for a while,** so that something can be done with
  them. By default the emails of the last week are kept. The person can
  change this.
- **What can be done with a new email:**
  - copy a login code it contains;
  - have it summarised;
  - ask an assistant questions about it;
  - reply to it.
- For anything else, a person opens their own email application.
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

  The person chooses the level, per account. The fuller levels are shown
  or spoken on their own devices. A household device keeps to the least,
  unless the person allows it to say more.
- A new email is an event. It becomes a notification that is routed like
  any other. See
  [notifications and routing](notifications-and-routing.md).

## Open questions

- How a login code is found in an email. This is research still to do.
- Whether an email is ever shown in full in a client, and if so how its
  HTML is drawn safely.
- How a reply is written and sent: typed, dictated or drafted by an
  assistant, and whether it is checked before it goes out.
- Signing in with Google or Microsoft needs an application registered
  with each company, and Google reviews applications that read mail. Who
  registers them: the project, or each household's admin? This is
  research still to do.

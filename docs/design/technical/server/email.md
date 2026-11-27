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
- **Only the text is kept:** the subject, who it is from and to, the
  date, and the text of the message. Styling, images and attachments are
  not kept and not processed. That an email has attachments is
  remembered, so the person can be told, for example, "this email has
  two attachments". The text is there so that it can be shown
  plainly and so that information can be taken from it.
- **The text can be shown as plain text** on the person's own devices,
  from the notification.
- **The email is never shown with its formatting.** To see the real
  thing, the person is pointed to their own email application.
- **What can be done with a new email:**
  - copy a login code it contains. A simple pattern finds the usual
    forms; the AI model is asked only when that finds nothing clear;
  - have it summarised;
  - ask an assistant questions about it;
  - reply to it. The reply is typed, dictated, or drafted by an
    assistant. The final text is always shown or read back to the person,
    and it is sent only after they say so, because an email leaves the
    house under their name and cannot be recalled.
- For anything else, a person opens their own email application.
- **An account is connected through IMAP in the first release.** Gmail
  and Outlook work that way with an app password. "Sign in with Google"
  and "Sign in with Microsoft" are added later.
- **The credential is kept on the server, in the
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

- Whether a notification can open the email in the person's own email
  application, on a phone and on a desktop. This is research still to do.
- Signing in with Google or Microsoft, after the first release: who
  registers the application with each company, and what Google's review
  of applications that read mail involves. This is research still to do.

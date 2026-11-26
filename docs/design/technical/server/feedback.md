# Feedback

Reporting a bug or suggesting a feature from inside any app. Part of
[the server design](README.md).

Status: draft. This is among the first features to be built. It is a
feature of the system; a [module](../modules/README.md) gives assistants
the tools to use it.

## Why it exists

Reports become issues on the project's GitHub repository. This collects
feedback quickly, and agents can be pointed at the issues to fix bugs and
add features. It is the main way the project iterates after the first
release.

## Design

- Every app has "Report a bug" and "Suggest a feature".
- **Anyone may file one:** any member, from an app or by voice, and also
  an unrecognised voice through a guest assistant. Everything waits for
  an admin's review.
- **A report goes to the admin panel first.** It is kept on the household
  server and nothing leaves the house yet.
- **An admin is notified** that a report or a suggestion has arrived.
- **An admin reviews it** in the
  [admin panel](../clients/web-admin.md), and sees a preview of the
  GitHub issue exactly as it will be created. The repository is public,
  and logs can contain email subjects or clipboard text.
- **The admin creates the issue,** and it is filed under their own GitHub
  account. Each admin enters their own GitHub token for this. An
  admin without a token can read reports but cannot send them on. No app
  carries a GitHub credential.
- Duplicate reports are not detected. They are sorted out on GitHub.
- **The admin panel explains how** to make a GitHub account and a token.
- Attached automatically: app version, platform, device type and recent
  logs.
- A report waits on the server until an admin sends it, and until there
  is internet.

## What exists to draw on

The earlier voice assistant has a working version, by voice only:

- the report is kept as a draft first;
- secrets are scrubbed, and the conversation is never included;
- the owner reviews it in the admin page and presses Send;
- it is sent exactly once, with a token the admin stored;
- without a token, the admin gets a prefilled "new issue" link.

Its repository name is hard-coded, which this design should avoid.

## Open questions

None at the moment.

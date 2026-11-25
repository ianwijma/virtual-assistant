# Feedback module

Reporting a bug or suggesting a feature from inside any app. Part of
[the modules design](README.md).

Status: draft. This is among the first modules to be built.

## Why it exists

Reports become issues on the project's GitHub repository. This collects
feedback quickly, and agents can be pointed at the issues to fix bugs and
add features. It is the main way the project iterates after the first
release.

## Design

- Every app has "Report a bug" and "Suggest a feature".
- The report goes to the household server, and the server files the
  GitHub issue. No app carries a GitHub credential.
- Attached automatically: app version, platform, device type and recent
  logs.
- The person sees exactly what will be sent and can edit it first. The
  repository is public, and logs can contain email subjects or clipboard
  text.
- Reports queue on the server until there is internet.
- The module has its own screen in the
  [admin panel](../clients/web-admin.md).

## What exists to draw on

The earlier voice assistant has a working version, by voice only:

- the report is kept as a draft first;
- secrets are scrubbed, and the conversation is never included;
- the owner reviews it in the admin page and presses Send;
- it is sent exactly once, with a token the admin stored;
- without a token, the admin gets a prefilled "new issue" link.

Its repository name is hard-coded, which this design should avoid.

## Open questions

- How the server signs in to GitHub: a token the admin enters, a relay
  the project hosts, or a prefilled link only?
- Is a report always reviewed by a person before it is sent, and by whom:
  the reporter, or an admin?
- May any member file a report, including by voice?
- How duplicates are avoided.

# Vault

The one place on the server where the system's secrets are kept. Part of
[the server design](README.md).

Status: draft. Only the outline is decided.

## Design

- The vault is a system feature. Every part of the system that needs a
  secret keeps it here, and nowhere else.
- What it holds:
  - the keys and sign-ins of the [AI providers](ai-providers.md) and the
    cloud speech providers;
  - the mail account the server sends sign-in codes from;
  - each admin's GitHub token, for [feedback](feedback.md);
  - people's [email](email.md) credentials.
- The server uses these when it needs them.
- **Data on disk is protected by the operating system's disk
  encryption.** The server does not encrypt its data itself. Hardware
  that is sold ships with disk encryption switched on.
- **Secrets deserve more than that.** Disk encryption does not help when
  someone gains control of the running server, and the API keys should
  not then lie open. Whether the vault encrypts its secrets itself is
  being researched. If that would slow the work down, the first release
  relies on disk encryption alone. Either way the vault is built so that
  encryption can be added later without a painful migration.

## Not in the first release

These were considered and are put off until after the first release:

- **Sealed data:** data that only a person's own devices can read, with
  keys the server never holds, a recovery sheet and a recovery copy.
- **A password manager,** with shared passwords.

They belong together, because a password manager should not be built
without sealed data.

## Open questions

- How the vault encrypts its secrets, so that control of the running
  server does not expose them, and where that key is kept. This is
  research still to do, kept small.

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
- **The server's data is encrypted where it is stored.** That protects
  everything on it, the clipboard history included, against a stolen disk
  or a copied backup.

## Not in the first release

These were considered and are put off until after the first release:

- **Sealed data:** data that only a person's own devices can read, with
  keys the server never holds, a recovery sheet and a recovery copy.
- **A password manager,** with shared passwords.

They belong together, because a password manager should not be built
without sealed data.

## Open questions

- How the server's data and its secrets are encrypted, and where the key
  is kept, so that a stolen disk or a copied backup gives nothing away.
  This is research still to do.

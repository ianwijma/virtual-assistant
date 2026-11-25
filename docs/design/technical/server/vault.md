# Vault

The one place on the server where credentials and other secrets are kept.
Part of [the server design](README.md).

Status: draft. Only the outline is decided.

## Design

- The vault is a system feature. Every part of the system that needs a
  secret keeps it here, and nowhere else.
- What it holds, to begin with:
  - a person's [email](email.md) credentials;
  - an admin's GitHub token, for [feedback](feedback.md);
  - the keys and sign-ins of the [AI providers](ai-providers.md) and the
    cloud speech providers;
  - the mail account the server sends sign-in codes from. See
    [identity and sharing](identity-and-sharing.md).
- Everything in it is encrypted.
- A secret belongs to a person or to the household, like everything
  else.

## Open questions

- Is the vault only the system's own store of secrets, or also a password
  manager that people put their own passwords in?
- How it is encrypted, and where the key is kept, so that a stolen disk
  or a copied backup gives nothing away. This is research still to do.
- Whether an admin can read a person's secrets. An admin can read all
  other data for now.

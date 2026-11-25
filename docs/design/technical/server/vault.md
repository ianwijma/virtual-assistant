# Vault

The one place where sensitive data is kept: the system's own secrets, and
each person's encrypted data. Part of [the server design](README.md).

Status: draft. The outline is decided; the cryptography is not.

## Design

The vault holds two kinds of thing. Both are stored on the server, and
both are encrypted, but they differ in who can read them.

| Kind | Examples | Who can read it |
|---|---|---|
| System secrets | Keys and sign-ins of the [AI providers](ai-providers.md) and cloud speech providers, the mail account for sign-in codes, an admin's GitHub token, [email](email.md) credentials | The server, which uses them when needed |
| A person's encrypted data | Their [clipboard](clipboard.md) history, their passwords | Only that person's devices |

- **A person's encrypted data is encrypted and decrypted on their
  devices,** with keys that person holds. The server only stores it. The
  server cannot read it, and so neither can an admin or an assistant.
- **The same keys serve everything of that person:** the clipboard
  history, and a password manager.
- **The person stays in control.** Their encrypted data is used by
  another part of the system, such as an assistant, only when they allow
  it. It is then sent from a device that holds the key, which is the
  preferred way, so the server never learns the content.
- Every part of the system that needs a secret keeps it here, and nowhere
  else.

## Open questions

- How a person's keys are made, how a new device of theirs gets them, and
  how they are recovered when every device is lost. There are no
  passwords to derive a key from. This is research still to do.
- Which data is a person's encrypted data, beyond the clipboard and
  passwords: email, notifications, lists?
- The web clients run in a browser. Do the admin panel and the voice page
  hold a person's keys?
- Is the password manager in the first release, and can passwords be
  shared with the household?
- How system secrets are encrypted, and where that key is kept, so that a
  stolen disk or a copied backup gives nothing away. This is research
  still to do.

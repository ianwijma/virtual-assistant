# Vault

The one place where sensitive data is kept: the system's own secrets, and
each person's most sensitive data. Part of [the server design](README.md).

Status: draft. The outline is decided. Who can read a person's sensitive
data, and the cryptography, are not.

## Design

The vault holds two kinds of thing. Both are stored on the server, and
both are encrypted.

| Kind | Examples |
|---|---|
| System secrets | Keys and sign-ins of the [AI providers](ai-providers.md) and cloud speech providers, the mail account for sign-in codes, an admin's GitHub token, [email](email.md) credentials |
| A person's sensitive data | Their [clipboard](clipboard.md) history, their passwords |

- **The server uses system secrets when it needs them.**
- **Only the clipboard and passwords are a person's sensitive data.**
  Anything an assistant must read on its own, such as email,
  notifications and lists, is not, because the server has to read it.
- **The vault is also a password manager,** in the first release.
  Passwords can be shared with the household.
- **An assistant can use the clipboard and passwords, but only with the
  person's approval:**

  | Data | Approval |
  |---|---|
  | Clipboard | The assistant first asks whether it may search the clipboard |
  | Passwords | Two steps: it asks whether it may search the passwords, and then asks again before a password is decrypted |

  These are the first actions that need a confirmation. Other tools do
  not ask, for now. See [AI providers](ai-providers.md).
- **Each person gets a recovery sheet:** a PDF with their key and the
  other details needed to get back in, like the emergency kit of
  1Password.
- **An admin should be able to help a person recover their key.**
- **Browsers do not get at a person's sensitive data in the first
  release.** The admin panel and the voice page do not show clipboard
  history or passwords; the desktop client and the phone app do.
- Every part of the system that needs a secret keeps it here, and nowhere
  else.

## Open questions

- Can the server read a person's sensitive data? Three wishes pull in
  different directions: the server should not know the content,
  assistants should be able to use it, and an admin should be able to
  recover it. The answer may differ for the clipboard and for passwords.
- Where the person gives an approval: by voice to the device they are
  talking to, or on one of their own devices?
- What an assistant may do with a password: say it, fill it in on a
  device, or use it to sign in somewhere by itself?
- How passwords are shared with the household: one shared vault, or
  sharing item by item?
- How a person's keys are made, how a new device of theirs gets them, and
  how recovery works. There are no account passwords to derive a key
  from. This is research still to do, and it depends on the first
  question.
- How system secrets are encrypted, and where that key is kept, so that a
  stolen disk or a copied backup gives nothing away. This is research
  still to do.

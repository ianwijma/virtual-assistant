# Vault

The one place where sensitive data is kept: the system's own secrets, and
each person's sealed data. Part of [the server design](README.md).

Status: draft. The outline is decided; the cryptography is not.

## Two kinds of content

Both are stored on the server, and both are encrypted. They differ in who
can read them.

| Kind | Examples | Who can read it |
|---|---|---|
| System secrets | Keys and sign-ins of the [AI providers](ai-providers.md) and cloud speech providers, the mail account for sign-in codes, an admin's GitHub token, [email](email.md) credentials | The server, which uses them when needed |
| A person's sealed data | Their [clipboard](clipboard.md) history, their passwords | Only that person's devices |

- **Only the clipboard and passwords are sealed.** Anything an assistant
  must read by itself, such as email, notifications and lists, is not,
  because the server has to read it.
- Every part of the system that needs a secret keeps it here, and nowhere
  else.

## Sealed data

- **It is encrypted and decrypted on the person's devices,** with a key
  only those devices hold. The server stores it and never holds the key.
  So the server cannot read it, and neither can an admin.
- **Browsers do not get at it in the first release.** The admin panel and
  the voice page do not show clipboard history or passwords; the desktop
  client and the phone app do.

## How an assistant uses sealed data

An assistant can use the clipboard and passwords, but only with the
person's approval, and only through one of their devices.

| Data | Approval |
|---|---|
| Clipboard | One step: it asks whether it may search the clipboard |
| Passwords | Two steps: it asks whether it may search the passwords, and asks again before a password is unsealed |

- **Every request explains itself.** The assistant says why it needs the
  access and what it will do with the result. This holds for each step.
- **The approval is given on a device of that person that holds the
  key.** That device then decrypts only what was asked for and hands it
  over. It needs one of the person's devices to be on.
- These are the first actions that need a confirmation. Other tools do
  not ask, for now. See [AI providers](ai-providers.md).

## Passwords

- The vault is also a password manager, in the first release.
- **A password can be shared, with limits,** as in 1Password: how many
  times it may be viewed, such as five, and for how long the share works.
- A password is shared with named people or with the whole household.
  There are no groups of people and no shared vaults, for now.
- **A password is never spoken, and never shown on a household device,**
  whatever was approved.

## Recovery

- **Each person gets a recovery sheet:** a PDF with their key and the
  other details needed to get back in, like the emergency kit of
  1Password.
- **An admin can release a recovery copy.** A sealed copy of a person's
  key is kept for recovery. An admin can release it to that person, for
  when both their devices and their sheet are lost.

## Open questions

- How a person's key is made, how a new device of theirs gets it, and how
  the recovery copy is sealed so that releasing it takes an admin and
  cannot happen silently. This is research still to do.
- How system secrets are encrypted, and where that key is kept, so that a
  stolen disk or a copied backup gives nothing away. This is research
  still to do.

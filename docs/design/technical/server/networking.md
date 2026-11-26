# Networking

The home network, remote access and certificates. Part of
[the server design](README.md).

Status: draft.

## Home network by default

By default the server is reachable only on the home network. Data stays in
the house unless the household chooses otherwise.

## Remote access

Remote access is opt-in, through Tailscale, and is hidden behind one
`tailnet` crate with three backends:

1. **The installed Tailscale app.** Works on every platform now. The
   server also listens on its Tailscale address.
2. **Embedded `tailscale-rs`,** on the server and the desktop, as an
   experimental setting.
3. **Embedded `libtailscale`,** on phones, if it proves workable from the
   Rust core.

A device stores the server's home-network address and its Tailscale
address at pairing, and tries the home network first.

## Certificates

- **Native apps** need no web certificate. They pin the server's key at
  pairing.
- **Browsers** need HTTPS to use the microphone. The server running its own
  certificate authority, which each browser device trusts once, needs no
  internet and is the starting idea. Which way is used is being
  researched.
- **Alternatives:** a real certificate from the household's own domain, or
  from Tailscale.

## Verified and assumed

Verified on 25 November 2026:

- `tailscale-rs` is version 0.7.1 and experimental. It does not support
  Android or iOS.
- `libtailscale` is an official C library that covers iOS and Android.

Assumed, needing a build to confirm:

- `libtailscale` works from a Rust core on phones.

## Open questions

- How the admin panel and the voice page get HTTPS that a browser trusts,
  for a non-technical person. To compare: certificates through
  Tailscale, a proxy domain per installation that the project provides,
  the person's own certificates, accepting the browser's warning at
  first, and the server's own certificate authority. This is research
  still to do.

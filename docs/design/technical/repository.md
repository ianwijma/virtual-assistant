# Repository layout

How the monorepo is organised. Part of [the technical design](README.md).

Status: draft. The repository holds documents only. No code is written
until the technical details are clear.

## Layout

One monorepo, with one shared Rust core used by every binary:

```text
crates/
  protocol/   # events, device messages, shared types
  core/       # users, shares, routing, event log, system features
  modules/    # sets of tools given to assistants
  voice/      # wake word, speaker identification, speech, voices
  ai/         # provider layer
  tailnet/    # remote access backends
  ui/         # shared screens, A2UI renderer
apps/
  server/  desktop/  mobile/  web-admin/  web-voice/
design/
  tokens/     # single source for all themes
docs/
```

Crates and binaries use the neutral prefix `va-` until the product has a
name.

## Rules

- Message types live in the `protocol` crate, which every Rust binary
  imports. There is no code generation between Rust parts.
- Native shells on phones reach the Rust core through generated bindings
  (UniFFI).
- A language other than Rust is allowed only in the UI and platform-glue
  layer. See principle 4 in [the overarching design](../README.md).

## Git

- Pull requests go into `develop`. `main` receives releases.
- The plan lives in `docs/` as Markdown, not in GitHub issues.
- "Virtual Assistant" is a working title.

## Open questions

- The build order of the parts. There is no roadmap yet; it is decided
  after the technical details are clear.
- How work is reviewed and tested. The earlier project suffered from long
  review rounds, heavy tests and documents used as changelogs.
- Which machines are used to test the desktop client, the Android app and
  voice hardware.
- Whether to create the Cargo workspace and CI before planning is finished.
  For now the answer is no.

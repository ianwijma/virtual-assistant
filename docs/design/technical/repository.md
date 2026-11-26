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

## Review and testing

Speed to a first working product comes before thorough testing.

- There are few tests. They run in CI, and they must pass.
- Each pull request is reviewed by an agent.
- **A review takes at most two rounds,** and fewer is better. What is
  still open after that is filed as an issue on GitHub, and the pull
  request is merged once CI is green.

## Test machines

Testing happens on the development virtual machine only, for now. It
should run an Android emulator, to test the app including sound, and
virtual machines of its own, to test other things such as Linux desktops.

## No code before planning is finished

The Cargo workspace and CI are created when planning is finished, not
before.

## Open questions

- How the research and write-up threads are run after the merge, and
  whether the design write-ups are written before building starts or by
  whoever builds each part.
- Can the development virtual machine run an Android emulator with sound
  and virtual machines inside it? Both need virtualisation inside a
  virtual machine. The Rust toolchain is not installed on it yet either.
  This is research still to do.
- The build order of the parts. There is no roadmap yet; it is decided
  after the technical details are clear.

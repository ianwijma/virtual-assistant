# Instructions for agents

This project is in planning. There is no code yet.

- Start with [docs/README.md](docs/README.md). The design is in
  `docs/design/`, split into `technical/` and `visual/`, one subject per
  file. Read the `README.md` of a folder first, then only the files for
  the subject you are working on.
- This is a clean rewrite in Rust. The earlier voice assistant
  (`personal-voice-assistance`) is a reference only. Do not port its code or
  copy its summoning rules.
- Do not decide open questions on your own. Each design file ends with its
  open questions, and `docs/open-questions.md` is the index; ask the owner.
- Keep one subject per file. Split a file that grows past one subject, and
  add new files to their folder's `README.md`.
- What a design file states is decided. When the owner decides something,
  write it into the design file it belongs to, remove the matching open
  question, and add a line to `docs/decisions.md`. Do not append review
  notes or history to a design document.
- `docs/sources/` is never edited.
- Work goes through pull requests into `develop`. `main` receives releases.
- The licence is GPLv3. Every dependency, model and voice must allow use in
  hardware that is sold.

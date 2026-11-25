# Instructions for agents

This project is in planning. There is no code yet.

- Start with [docs/README.md](docs/README.md). The design is in
  `docs/design/`, split into `technical/` and `visual/`, one subject per
  file. Read the `README.md` of a folder first, then only the files for
  the subject you are working on.
- This is a clean rewrite in Rust. The earlier voice assistant
  (`personal-voice-assistance`) is a reference only. Do not port its code or
  copy its summoning rules.
- Do not decide open questions on your own. `docs/open-questions.md` is
  the full list the owner answers from, and each question also sits at the
  end of its design file. Keep the two in step.
- When an answer raises a new question, or you had to interpret it, add
  the question to `docs/open-questions.md` and its design file. Do not ask
  the owner to clarify in conversation.
- Keep one subject per file. Split a file that grows past one subject, and
  add new files to their folder's `README.md`.
- What a design file states is decided. When the owner decides something,
  write it into the design file it belongs to, remove the matching open
  question, and add a line to `docs/decisions.md`. Do not append review
  notes or history to a design document.
- During implementation, getting things done comes before thorough
  testing and validation. The aim is to reach a minimum viable product as
  soon as possible; fixes and hardening come after it. Write the tests a
  change needs to be trusted, and no more. Do not add broad test suites,
  extra validation passes or polish that slows the path to a working
  product.
- `docs/sources/` is never edited.
- Work goes through pull requests into `develop`. `main` receives releases.
- The licence is GPLv3. Every dependency, model and voice must allow use in
  hardware that is sold.

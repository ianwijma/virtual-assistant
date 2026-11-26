# Design

This is the overarching design: the vision and the principles that every
part follows. The detail is split by kind of design, and then by subject,
so that work on one subject touches one or two files.

Status: draft. Nothing here is built yet.

## Kinds of design

| Kind | Folder | What it covers |
|---|---|---|
| Technical | [technical/](technical/README.md) | How the system is built: server, voice, modules, clients, screens sent to devices |
| Visual | [visual/](visual/README.md) | How the system looks and feels: identity, design tokens, assistant visuals |

A new kind of design, such as a description of how each feature behaves
for the person using it, gets its own folder beside these two.

## Vision

One self-hosted assistant ecosystem for a whole household. It runs on a
server in the home and reaches every device the household already owns:
desktops, phones, tablets and browsers. It aims for the continuity of the
Apple ecosystem, but local and self-owned, and installable on any device.

- **One system.** The server is the hub, and every client is a device of it.
- **Local.** The server is on the home network and needs no internet.
- **Voice and screen.** Assistants are characters you can talk to, and the
  same system powers a fast desktop hub.
- **Long-term goal:** sell hardware boxes with the software installed. This
  is well beyond the first release.

## Principles

1. **The server is the default home for data.** Data lives on a device only
   if it is tied to that machine or must respond within a frame.
2. **Never blocked by the server.** Clients write locally first, then sync.
3. **Private by default.** Nothing is shared until its owner shares it.
4. **Rust first.** Another language is allowed only for UI and platform
   glue, when an integration is impossible or clearly worse from Rust. Each
   such choice is recorded in the document of the client it concerns.
5. **Modular.** A module is a set of tools an AI agent can call, and
   adding one must be easy. People extend the system by forking and adding
   modules; there is no plugin system. Providers for speech and AI are
   swappable in the same spirit.
6. **Decide, then build.** No open-ended prototyping. Risky choices sit
   behind boundaries, so a wrong one is a contained rewrite.
7. **Build on established technology.** The exceptions are A2UI and young
   Rust libraries for new technologies. Depend on public crates, and
   contribute to an existing one before creating a new one. When
   something does not exist yet and we build it, we publish it as a crate
   so that others can use it.
8. **A screen for every setting.** No configuration files for users.
9. **One look.** Every app is recognisable as ours.
10. **A clean rewrite.** The earlier voice assistant is a
    [reference](../reference/existing-voice-assistant.md) only.

## How these documents work

- **One subject per file.** A file should be readable whole. When a file
  grows past one subject, split it, and give a folder to a subject that
  needs several files.
- **Each folder has a `README.md`** with the overview of its area and a
  list of its files.
- **Each file has the same shape:** what it covers, the design, then
  "Verified and assumed" where it applies, then "Open questions".
- **Open questions sit at the end of the file they belong to,** and all of
  them are listed in [../open-questions.md](../open-questions.md), which is
  the document the owner answers from. A new question raised by an answer
  goes into both.
- **Decisions live in the design.** What a document states is decided.
  What is not decided is under its "Open questions".
- **Answering a question** means removing it from "Open questions",
  writing the answer into the design, and adding a line to
  [../decisions.md](../decisions.md), in the same change.
- **A new module, client or provider gets its own file** in the matching
  folder, and a line in that folder's `README.md`.

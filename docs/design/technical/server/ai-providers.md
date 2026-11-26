# AI providers

The AI models behind assistants and features, and how one is chosen for a
request. Part of [the server design](README.md).

Status: draft.

## Design

AI is part of the core of the system, not an addition at the end. It
answers assistants, performs actions through module tools, and powers
features such as summaries.

Providers supported from day one:

| Provider | Notes |
|---|---|
| Claude Code subscription | Uses a subscription instead of paying per request |
| Codex subscription | Uses a subscription instead of paying per request |
| OpenRouter | Any model, paid per request |
| Ollama | Local and private; on the server or elsewhere on the home network |

## What the model is told about the device

Each request carries the [capabilities](protocol.md) of the device it
came from: whether it has a screen, whether it can draw A2UI, whether it
can speak. The model shapes its reply to fit, such as a described screen
for a tablet and plain words for a device that only speaks.

## Providers and assistants

- **Several providers can be configured** on the server, by an admin.
- **Each assistant uses exactly one of them.** It is chosen when the
  assistant is set up, to match what the assistant must do. An assistant
  with demanding tools, such as coding, gets a strong model.
- **Nobody overrides it per person or per request.** That would let a weak
  model be put behind tools it cannot handle, with unintended results.
- The step that decides which provider serves a request is kept as one
  replaceable step.
- Ollama is the likely brain of a future hardware box, so the system must
  be fully usable with a local model only.

## Where a subscription runs

A Claude or Codex subscription is used through its command-line tool. The
tool runs on the server. It is not installed by default, in any form of
the server: the program, the container image or a sold box. The
[admin panel](../clients/web-admin.md) has a button that downloads and
installs it when wanted, and it carries the tool's sign-in, so an admin
never needs a terminal.
Every device can then use it, and nothing depends on a desktop being on.

## Confirmation

An assistant does not ask for confirmation before it acts, for now, with
one exception: using a person's clipboard or passwords needs their
approval. See [vault](vault.md). The
first tools carry no real risk: nothing buys anything, and a message or a
broadcast to the household goes out directly. Confirmation is added when
a tool arrives that needs it, or when use shows that one does. The gateway
every tool call passes is where it would be added.

## Open questions

- How a vendor's command-line tool is installed and signed in to from
  the admin panel, including inside a container. This is research still
  to do.
- How each provider produces A2UI screens. See [A2UI](../a2ui.md).

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

## One configuration for the household

- There is one AI configuration for the whole household. It can be any of
  the four providers.
- The step that decides which provider serves a request is kept as one
  replaceable step. If needed later, it can choose a subscription by the
  recognised voice.
- Ollama is the likely brain of a future hardware box, so the system must
  be fully usable with a local model only.

## Open questions

- Can an assistant or a person override the household configuration with
  their own provider?
- Where a subscription's command-line tool runs: on the server, or on a
  person's desktop?
- What an assistant may do without asking, and what needs confirmation.
  The earlier project's risk classes (read, change, message, money,
  security) are a candidate.
- How each provider produces A2UI screens. See [A2UI](../a2ui.md).

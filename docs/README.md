# Documentation

| Path | What it is | Changes? |
|---|---|---|
| [design/](design/README.md) | The vision and principles |  Yes, kept current |
| [design/technical/](design/technical/README.md) | How the system is built, one subject per file | Yes, kept current |
| [design/visual/](design/visual/README.md) | How the system looks and feels | Yes, kept current |
| [decisions.md](decisions.md) | The log of decisions, each with the design document it is written into | Append only |
| [open-questions.md](open-questions.md) | Every open question in one list, for the owner to answer from | Yes |
| [reference/existing-voice-assistant.md](reference/existing-voice-assistant.md) | Findings from the earlier voice assistant project | Rarely |
| [sources/](sources/) | The original brief and design conversation, unedited | Never |

## Rules for these documents

- What a design document states is decided. What is not decided is under
  its "Open questions".
- Answering a question means removing it from "Open questions", writing
  the answer into the design, and adding a line to `decisions.md`, in the
  same change.
- A section whose heading starts with "Proposal" is not decided yet. It
  was written for the owner to review, and its file lists "agree to the
  proposal" under "Open questions".
- Say what is verified and what is assumed.
- The plan lives here as Markdown for now, not in GitHub issues.

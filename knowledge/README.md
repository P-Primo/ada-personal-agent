# Knowledge base

These are the curated docs your agent **reads before answering**. The goal is for the
agent to consult written, current facts about your system instead of reconstructing
them from memory (where it will guess and be wrong).

## Principles

- **One topic per file.** Small, focused docs are easier to keep accurate.
- **Keep it current.** When reality and a doc disagree, reality wins — fix the doc.
- **Write the *why*, not just the *what*.** Decisions and their reasons are the part an
  agent (or a new teammate) can't infer from the system itself.
- **Never put secrets here.** Credentials belong in `.env`. Sheet IDs, internal URLs,
  and other sensitive specifics belong in a **private** location if the system isn't
  yours to publish.

## A suggested set of docs

Adapt to your system — this is a starting shape, not a mandate:

| File | What it holds |
|------|---------------|
| `01-overview.md` | What the system is, who it serves, the goal |
| `02-architecture.md` | The components/stages, their inputs/outputs, failure modes |
| `03-rules.md` | Business/operational rules the agent must respect |
| `04-data-model.md` | Where the data lives, key fields, invariants |
| `05-patterns.md` | Hard-won platform lessons and gotchas |
| `06-decision-log.md` | Notable decisions and *why*, in date order |
| `07-known-issues.md` | Open bugs, blockers, what's untested |
| `08-glossary.md` | People, tools, statuses, key terms |

Start with **overview**, **known-issues**, and **glossary** — those three alone make
the agent noticeably more useful. Use `00-template.md` as a starting point.

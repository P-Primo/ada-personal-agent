# Ada — Personal Agent Starter

A template for building a **disciplined monitoring & diagnostic AI agent** on top of
[Claude Code](https://claude.com/claude-code). Point it at a system you operate — an
automation pipeline, a set of data workflows, a fleet of scheduled jobs — and it
watches the system, diagnoses problems against a curated knowledge base, and proposes
fixes under an explicit human-approval gate.

This repo is the **framework**, not a running agent. It ships the persona, the
operating discipline, and the folder structure. You supply the domain knowledge and
your own credentials, on your own machine.

> **No secrets, no third-party data.** Everything here is generic scaffolding. Real
> API keys and any system-specific knowledge live in files this repo is configured to
> **never commit** (see `.gitignore`). Read the [Security](#security) section before
> you add anything.

---

## Why an agent needs *discipline*, not just access

An LLM with tool access will happily act on stale data, guess at IDs, trust a crashed
run's fabricated output, or apply a fix nobody approved. The value of this template is
the **guardrails** that stop that:

| Principle | What it prevents |
|---|---|
| **Fetch live data first** | Diagnosing from stale snapshots and being confidently wrong |
| **Identify components by stable name, not stored ID** | Acting on the wrong thing after a refactor renumbers IDs |
| **Distrust crashed / partial runs** | Treating fabricated recovery output as real telemetry |
| **Read-only by default; supervised-write with a per-change veto** | Unreviewed mutations to live systems |
| **Stop after a diagnosis — don't assume next steps** | Runaway action chains from one vague instruction |
| **Verify by reading back after any write** | Claiming success that never happened |
| **Never print, log, or commit secrets** | Credential leaks |

These aren't domain-specific — they transfer to any operational system worth
monitoring. That's the reusable part.

---

## What's in the box

```
ada-personal-agent/
├── CLAUDE.md              # the agent config — persona, operating modes, rules (a TEMPLATE)
├── SETUP.md              # zero-to-running: install, authenticate, adapt
├── .env.example          # placeholder credential names — copy to .env (never committed)
├── .gitignore            # blocks .env, memory, and other secret-bearing paths
├── knowledge/            # the curated docs your agent reads before answering
│   ├── README.md         #   how to structure your knowledge base
│   └── 00-template.md    #   a starter knowledge doc
└── skills/               # reusable task playbooks the agent can invoke
    └── README.md         #   the skill patterns + how to add your own
```

## Quickstart

See **[SETUP.md](SETUP.md)** for the full walkthrough. In short:

1. Install Claude Code and authenticate with your own Anthropic account.
2. Copy this folder into (or clone it as) your project.
3. Fill in the `[PLACEHOLDERS]` in `CLAUDE.md` for your system.
4. `cp .env.example .env` and add **your** credentials (never commit `.env`).
5. Write a few `knowledge/` docs about your system.
6. Open the folder in Claude Code and start asking it to run health checks.

## Adapting it

The template is deliberately domain-agnostic. To target *your* system, edit three
things: the **persona** (who the agent is and what it watches), the **working rules**
(the non-negotiables for your platform), and the **knowledge base** (the facts it
reads before acting). Everything else — the governance model, the problem-solving
loop, the folder layout — you keep as-is.

## Security

- **Never put real credentials in this repo.** They go in `.env`, which `.gitignore`
  excludes. Double-check with `git status` before every commit.
- **Never commit knowledge that isn't yours to publish.** If you point this at a system
  owned by an employer or client, keep that knowledge in a private location and treat
  the confidential parts as off-limits for a public repo.
- If you ever see a real token staged for commit, stop and remove it from history —
  keys persist in git history even after you delete the file.

## License

MIT — see [LICENSE](LICENSE). Built by Paolo Barboza Primo as a reusable agent-design framework.

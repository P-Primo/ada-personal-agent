# Skills

Skills are **reusable task playbooks** — named procedures the agent follows for
recurring jobs, so you get consistent results instead of re-explaining the task each
time. In Claude Code these can be invoked directly; at minimum, describing them here
gives the agent a repeatable recipe to follow.

## Example skill types (adapt to your system)

| Skill | What it does | When to use |
|------|---------------|-------------|
| **health-monitor** | A one-screen, read-only status digest of the whole system | "health check", "morning digest", "what's it doing right now" |
| **pre-activation-verifier** | Audits one not-yet-live component against your rules and known issues; pass/fail report | "is X safe to turn on" |
| **prompt-builder** | Generates a tight, token-efficient prompt for a specific build/debug task | before you hand the agent a big build task |
| **visualizer** | Turns a description of a stage / process / pipeline into an interactive visual map | "visualize this", "map out how this works" |

## Writing your own

A good skill definition states:

1. **Trigger** — the phrases or situations that should invoke it.
2. **Inputs** — what it needs (a component name, a date range, a config).
3. **Procedure** — the ordered steps, including which live data to fetch first.
4. **Output** — the exact shape of the result (a digest, a pass/fail report, a diff).
5. **Guardrails** — what it must not do (e.g. "read-only; never mutate").

Keep each skill focused on one job. A skill that tries to do everything is a skill the
agent applies inconsistently.

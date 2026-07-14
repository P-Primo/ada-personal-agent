# Setup — from zero to a running agent

## 1. Install Claude Code

Follow the official instructions at **https://claude.com/claude-code**. Claude Code
runs in your terminal (and has VS Code / JetBrains integrations). You authenticate
with **your own** Anthropic account — this template does not include and never should
include anyone else's credentials.

## 2. Get this template into your project

Either clone it and work inside it, or copy the files into an existing project folder:

```bash
git clone https://github.com/P-Primo/ada-personal-agent.git my-agent
cd my-agent
```

## 3. Make it yours

- Open `CLAUDE.md` and replace every `[PLACEHOLDER]`. Decide your operating mode
  (start **READ-ONLY**).
- Add any platform-specific working rules under the non-negotiables.

## 4. Add your credentials (never commit them)

```bash
cp .env.example .env
```

Edit `.env` with the real values for whatever your agent needs to reach (your
automation platform's API, a spreadsheet API, etc.). `.env` is listed in
`.gitignore`, so it will not be committed — confirm with `git status` before your
first commit that `.env` is **not** in the list.

## 5. Populate the knowledge base

Write a few short docs in `knowledge/` describing your system — see
`knowledge/README.md` and the `00-template.md` starter. Even three or four good docs
(overview, architecture, known issues, glossary) dramatically improve the agent's
answers.

## 6. Use it

Open the folder in Claude Code and try:

- *"Give me a health check of the system."*
- *"Why did the last run fail?"*
- *"Is component X safe to turn on?"*

The agent will read `CLAUDE.md`, pull live data, consult `knowledge/`, and respond
under the discipline you configured.

## A note on connecting to live systems

If your platform has an API or an MCP server, wire it up per Claude Code's MCP docs and
reference the credential from `.env`. Keep the agent **read-only** until you've watched
it work and trust its judgment. The per-change approval gate in `CLAUDE.md` exists
precisely because live systems are easy to corrupt and hard to un-corrupt.

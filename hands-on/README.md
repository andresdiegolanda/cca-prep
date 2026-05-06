# Hands-on Baseline (Week 0)

**Goal:** close the gap between theoretical understanding and operational use of Claude Code.

Without this work, Domain 3 (20%) and parts of Domain 2 (18%) will be fragile — I'll recognise the right option in MCQ format but lose scenario questions that test setup decisions I've never actually made.

## Time budget

10 hours. If it takes 15, that's fine. If it takes 30, the exam date pushes back. Domain 2 cannot be faked.

## What this is NOT

- Not a project to ship
- Not a framework
- Not for `design-first-ai`
- Not commitable production code

This is a **disposable practice repo** for calibration. Throw it away after Week 0 ends. Copy artifacts (CLAUDE.md, .mcp.json, settings.json, notes.md) into this `hands-on/` directory before deleting the practice repo.

## Checklist

### Setup (1 hour)

- [ ] Install Claude Code CLI on local machine — note exact install command in `notes.md`
- [ ] Authenticate
- [ ] Verify `claude --version`, `claude /help`
- [ ] Create a small private repo (NOT design-first-ai). A toy project: a local todo CLI in Python, a markdown note organiser, anything I can throw away.

### Core CLI (3 hours)

- [ ] Run `claude` in the practice repo and complete one real task end-to-end (e.g. add a feature, fix a bug, write tests)
- [ ] Write a `CLAUDE.md` for the practice repo
- [ ] Configure `.claude/settings.json`:
  - [ ] `allowedTools` — be specific
  - [ ] `disallowedTools`
  - [ ] permission rules (allow/deny per tool, per pattern)
- [ ] Use slash commands at least once each, note behaviour in `notes.md`:
  - [ ] `/init`
  - [ ] `/clear`
  - [ ] `/compact`
  - [ ] `/cost`
  - [ ] `/memory`
  - [ ] `/model`

### Subagents and multi-agent (2 hours)

- [ ] Spawn a subagent via Task tool — what's the subagent prompt look like, what context does it inherit, what does it return
- [ ] Run a workflow that needs 2+ subagents in parallel
- [ ] Document the orchestrator pattern I observed in `notes.md`

### MCP server (3 hours)

- [ ] Build a minimal MCP server (5 tools max), Python (`mcp` SDK) or Node (`@modelcontextprotocol/sdk`)
- [ ] Tools should do something trivial — read a file, list directory, search a string. Operational mechanics matter, not tool utility.
- [ ] Add `.mcp.json` to wire the server to Claude Code
- [ ] Restart Claude Code, verify tools are available
- [ ] Run an end-to-end task using the MCP server's tools
- [ ] Break something on purpose — bad schema, missing tool, server crash — and observe how Claude Code reports it

### Review (1 hour)

- [ ] Write `notes.md` with at minimum:
  - [ ] 5 things that surprised me about Claude Code behaviour
  - [ ] 3 places where my prior mental model from Copilot was wrong
  - [ ] What I now know that I couldn't have known from reading

## Files I should end up with in `hands-on/`

- `CLAUDE.md` — the actual one I wrote, with comments showing what I'd change in v2
- `.mcp.json` — actual MCP wiring
- `settings.json` — actual permission config
- `mcp-server/` (optional) — minimal MCP server source if I want to keep it as reference
- `notes.md` — the surprises log

## Gate to Week 1

`notes.md` must have at least 5 concrete observations about Claude Code behaviour that differed from my prior assumptions. If 10 hours of practice produced nothing surprising, I am running on autopilot — extend hands-on by 5 more hours before starting Domain 1.

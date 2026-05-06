# Hands-on Baseline (Week 0)

**Goal:** close the gap between theoretical understanding and operational use of Claude Code AND the Claude Agent SDK.

Without this work, Domain 1 (27%, agentic patterns), Domain 2 (18%, MCP and tool design), and Domain 3 (20%, Claude Code config) will all be fragile — recognising the right MCQ option without operational understanding fails on scenario questions. Anthropic's stated bar for this credential is 6+ months production experience; this checklist is the minimum viable substitute.

## Time budget

~12 hours across ~12 one-hour sessions. Original plan said 10 hours; revised after Session 001 verification when Claude Agent SDK was confirmed as a first-class exam topic separate from Claude Code CLI.

## What this is NOT

- Not a project to ship
- Not a framework
- Not for `design-first-ai`
- Not commitable production code

This is a **disposable practice repo** for calibration. Throw it away after Week 0 ends. Copy artifacts (CLAUDE.md, .mcp.json, settings.json, agent code, notes.md) into this `hands-on/` directory before deleting the practice repo.

## Track A — Claude Code CLI fluency (~3 hours)

Some of this is already done from setting up cca-prep (Sessions 001+). The rest closes gaps.

- [ ] Confirm install: `claude --version`, note version in `notes.md`
- [ ] Confirm auth: `claude auth status`
- [ ] Run `claude --help` and `/help` inside a session — read both outputs end to end, note anything that surprises you
- [ ] Use slash commands at least once each, note behaviour in `notes.md`:
  - [ ] `/init` — creates a CLAUDE.md
  - [ ] `/clear` — clears session
  - [ ] `/compact` — compacts context
  - [ ] `/cost` — shows session cost
  - [ ] `/memory` — manages memory
  - [ ] `/model` — switches model (try Opus, Sonnet, Haiku)
  - [ ] `/plan` — one-off plan for next prompt
  - [ ] `/review` — code review on staged changes
- [ ] Toggle Plan Mode (`Shift+Tab` twice). Run a non-trivial task in Plan Mode. Read the plan. Approve or reject. Note the difference vs no-plan execution.
- [ ] Try one-shot mode: `claude -p "summarize the README"` (non-interactive)
- [ ] Try resume: start a session, exit, resume with `claude -c`

## Track B — Configuration depth (~3 hours)

Domain 3 (20%) tests these specifically. Build a small disposable project (e.g. `claude-code-sandbox/`) and configure it.

- [ ] Create `CLAUDE.md` at project root with: stack, build commands, conventions, "don't"s
- [ ] Understand the **CLAUDE.md hierarchy**: project (`./CLAUDE.md`), user (`~/.claude/CLAUDE.md`), system. Note in `notes.md` how they merge.
- [ ] Create `.claude/settings.json` with at least:
  - `permissions.allow` (specific tools and bash patterns)
  - `permissions.deny` (e.g. `Read(./.env)`, `Write(./production.config.*)`)
  - One `hooks.PostToolUse` entry (e.g. run a formatter after Edit)
- [ ] Create a custom slash command via the **skills** approach: `.claude/skills/my-skill/SKILL.md` with YAML frontmatter (name, description) and a markdown body.
- [ ] Test: invoke the skill manually as `/my-skill`, then trigger it via natural-language match.
- [ ] Document `notes.md`: what's the difference between a built-in command, a bundled skill, a custom skill, and a plugin command? Anthropic's exam will ask.

## Track C — Claude Agent SDK basics (~3 hours)

The exam treats this as a first-class topic, separate from Claude Code CLI.

- [ ] Install: `pip install claude-agent-sdk` (Python) — preferred, since you have 26 years of backend experience and Python is more familiar territory
- [ ] Note the rename: this used to be `claude-code-sdk`. Old name appears in older blog posts and docs — exam will use new name.
- [ ] Run the official quickstart from platform.claude.com/docs/en/agent-sdk/quickstart — the bug-fixing agent. Get it working end to end.
- [ ] Modify the agent: change `allowed_tools`, change `permission_mode` (try `acceptEdits` vs default), add a `system_prompt` override.
- [ ] Switch from `query()` to `ClaudeSDKClient` for an interactive session
- [ ] Define a custom tool using the `@tool` decorator and `create_sdk_mcp_server`. This is an in-process MCP server — different from Track D's separate-process MCP server. Make sure you understand both.
- [ ] Add a hook (function called by Claude Code at specific points of the agent loop). See the SDK docs for hook events.
- [ ] Document in `notes.md`: how does the agent loop work? What does each iteration of `async for message in query(...)` yield?

## Track D — MCP server (~3 hours)

Domain 2 (18%) tests this. Both transport types matter.

- [ ] Build a **separate-process MCP server** (Python or Node), 3–5 trivial tools (read file, list directory, search string)
- [ ] Wire via `.mcp.json` in the practice project
- [ ] Restart Claude Code, verify tools appear (try `/mcp` to inspect)
- [ ] Run a task that uses the MCP tools end to end
- [ ] **Break it on purpose** — bad schema, missing tool, server crash, malformed JSON response. Observe how Claude Code reports each failure mode. This is exam material — Domain 2 lists "MCP error structure" as a subtopic.
- [ ] Compare to the in-process MCP server from Track C: when would you use one vs the other?
- [ ] Document `notes.md`: transport types (stdio, SSE, HTTP), tool description style, scoping (project vs user vs system MCP config)

## Files I should end up with in `hands-on/`

- `notes.md` — surprises log, observations, vocabulary divergences I noticed
- `claude-code/CLAUDE.md` — the actual one I wrote
- `claude-code/.claude/settings.json` — the actual permission/hooks config
- `claude-code/.claude/skills/<name>/SKILL.md` — at least one custom skill
- `agent-sdk/quickstart.py` — modified version of the bug-fixing agent
- `agent-sdk/custom_tool_example.py` — the in-process MCP custom tool
- `mcp-server/` — minimal separate-process MCP server source

## Gate to Domain 1 lessons (Session XX onwards)

Before any Domain teaching starts, `notes.md` must contain at least:

- 5 concrete observations about Claude Code behaviour that differed from prior assumptions
- 3 places where my mental model from Copilot was wrong
- 2 vocabulary divergences between practitioner usage and Anthropic's official terms
- One break-it-on-purpose finding from Track D

If 12 hours produces fewer than this, I'm running on autopilot — extend hands-on by 3 more hours before starting Domain 1.

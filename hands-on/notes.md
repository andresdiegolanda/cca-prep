# Hands-on notes
Started: 2026-05-07

This file is the running log for Track A through D. Prose-style — only write what's worth thinking through, not exhaustive documentation.

---

## Track A — Claude Code CLI fluency (2026-05-07)

Spent ~30 min in Claude Code (sandbox repo) walking through slash commands and Plan Mode. Most of it matched my mental model from Copilot. Two things worth keeping:

**Plan Mode is keyboard-toggled, not a slash command.** Typed `/plan` — not in the command list. Plan Mode is reached via Shift+Tab twice (or UI toggle). Slash command list does not include `/plan`. This is exam-relevant: a question like "which slash command initiates Plan Mode?" will have `/plan` as a plausible distractor and the correct answer will be that there is no such command.

**Slash command parser fuzzy-matches silently.** Typed `/plan`, got `/batch` help text returned without any "did you mean" prompt. The parser appears to route unknown commands to the nearest known one. Don't trust that "Claude Code responded" means "Claude Code understood my command." Worth verifying in the next CLI session.

**Plan Mode worked well on a real task.** Asked it to add a `--name` CLI argument parser to hello.py. Plan Mode wrote the plan, executed, then surfaced a "deviation from approved plan" note explaining it had to switch from UTF-16 to UTF-8 because Python source files can't be UTF-16. That's the kind of self-correcting behaviour I hadn't seen in Copilot — Plan Mode preserves the trace of the deviation rather than hiding it.

**Other commands:** /init, /clear, /compact, /cost, /memory, /model, /review all worked as expected. Nothing surprising. /model switching between opus, sonnet, haiku was instant and the cost in /cost reflected the per-token pricing of the active model.

**One-shot mode** (`claude -p "..."`) and **resume** (`claude -c`) both worked. One-shot prints output and exits — useful for scripting. Resume restored conversation history and CLAUDE.md.

### Vocabulary divergences noticed

| Practitioner term | Anthropic term | Notes |
|-------------------|----------------|-------|
| "edit mode" / "code mode" (Copilot terms) | Plan Mode vs default execution | Different concept — Plan Mode is about pre-execution approval, not about what the agent is allowed to edit |

### Mental model corrections from Copilot

- Slash commands in Claude Code are operational (control behaviour, switch models, manage context), not just shortcuts for natural-language requests. In Copilot, `/explain` and `/fix` are conveniences. In Claude Code, `/clear` and `/compact` do things you cannot achieve with a prompt.
- Plan Mode is closer to "human-in-the-loop pre-execution review" than to a chat mode. It changes the agent's protocol, not just its tone.

### Open question

- Is the fuzzy-match-to-nearest-command behaviour documented somewhere, or is it incidental? Worth checking in Track B if it surfaces again.

---

## Track B (TBD)
## Track C (TBD)
## Track D (TBD)

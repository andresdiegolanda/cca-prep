# Mistakes

Append-only log of wrong answers from Practice Coach, Mock Exam, or any external practice (Skilljar, CertSafari, claudecertifications.com).

Each entry is reviewed at intervals: **+3 days, +7 days, +14 days**. Compute review dates at the time of logging.

## Format

```
## MNNN — YYYY-MM-DD — Domain N — [topic]
**Source:** Practice Coach $quiz / $drill / Skilljar mock / CertSafari / claudecertifications.com
**Question (paraphrased):**
> ...

**My answer:** [letter / option]
**Correct answer:** [letter / option]

**Why I got it wrong:**
- [ ] genuine misunderstanding of the concept
- [ ] careless reading
- [ ] vocabulary divergence (my framework term ≠ Anthropic's)
- [ ] distractor trap (plausible-sounding wrong option)
- [ ] scenario misidentification
- [ ] knowledge gap (never learned this)

**Mental model (one sentence I'll remember next time):**
> ...

**Reviews:**
- +3 days (YYYY-MM-DD): [ ] passed / [ ] failed
- +7 days (YYYY-MM-DD): [ ] passed / [ ] failed
- +14 days (YYYY-MM-DD): [ ] passed / [ ] failed

**Status:** Open / Closed
```

## Rules

1. Every wrong answer goes in. No exceptions, even "I knew this, just clicked wrong."
2. The mental model must be one sentence. If I can't compress it to one sentence, I haven't understood it yet.
3. Three passed reviews → status: Closed. Anything else stays Open.
4. Failed review → reset the cadence: +3, +7, +14 from the failure date.
5. Pattern check at the end of each week: if 3+ entries share the same root cause (e.g. vocabulary divergence in Domain 4), that's a domain-file update, not just an isolated mistake.

---

## M001 — 2026-05-07 — Domain 3 — Skill frontmatter context option
**Source:** Practice Coach $drill domain-3 (Q3)
**Question (paraphrased):**
> A skill needs to perform an isolated subtask without polluting the parent agent's context. Which skill frontmatter option achieves this?

**My answer:** capacity scaling option
**Correct answer:** context: fork

**Why I got it wrong:**
- [x] knowledge gap (never learned this — Track B territory, not yet covered)
- [x] distractor trap — "capacity-over-architecture" instinct: defaulted to scaling rather than architectural isolation

**Mental model (one sentence I'll remember next time):**
> `context: fork` in skill frontmatter isolates a skill's context window so the parent loop's context isn't polluted — it's about preventing context contamination, not about scaling capacity.

**Reviews:**
- +3 days (2026-05-10): [ ] passed / [ ] failed
- +7 days (2026-05-14): [ ] passed / [ ] failed
- +14 days (2026-05-21): [ ] passed / [ ] failed

**Status:** Open

---

## M002 — 2026-05-07 — Domain 3 — MCP config file responsibility
**Source:** Practice Coach $drill domain-3 (Q4)
**Question (paraphrased):**
> Which file is used to declare an MCP server for a project?

**My answer:** settings.json
**Correct answer:** .mcp.json

**Why I got it wrong:**
- [x] knowledge gap (Track B/D territory, not yet covered)
- [x] right-concept-wrong-file — got the scope reasoning right (project-level, committable) but assigned the responsibility to the wrong file

**Mental model (one sentence I'll remember next time):**
> Four config files, four jobs: CLAUDE.md = behaviour and rules; settings.json = permissions, hooks, env; .mcp.json = MCP server wiring; ~/.claude.json = personal/global config. The scope question (project vs user) is a second axis, not the primary one.

**Reviews:**
- +3 days (2026-05-10): [ ] passed / [ ] failed
- +7 days (2026-05-14): [ ] passed / [ ] failed
- +14 days (2026-05-21): [ ] passed / [ ] failed

**Status:** Open

---

## M003 — 2026-05-07 — Domain 3 — Model inheritance in skills
**Source:** Practice Coach $review skill-frontmatter (Q2)
**Question (paraphrased):**
> A skill should run on the same model as the parent agent unless overridden. How do you express this in the frontmatter?

**My answer:** model: inherit
**Correct answer:** omit the model key entirely

**Why I got it wrong:**
- [x] right-instinct-wrong-syntax — assumed there would be an explicit "inherit" value because that's how most config systems work; Claude Code's default is "omitted = use parent"
- [x] vocabulary divergence — "inherit" is a common term in config DSLs (Kubernetes, Terraform, etc.); not used here

**Mental model (one sentence I'll remember next time):**
> In Claude Code skill frontmatter, default behaviour comes from OMITTING the key, not from setting it to an "inherit" or "default" value. If you write `model: inherit`, you're literally trying to use a model named "inherit" — which doesn't exist.

**Reviews:**
- +3 days (2026-05-10): [ ] passed / [ ] failed
- +7 days (2026-05-14): [ ] passed / [ ] failed
- +14 days (2026-05-21): [ ] passed / [ ] failed

**Status:** Open

---

## M004 — 2026-05-08 — Domain 3 — Permission system tri-state semantics
**Source:** Practice Coach $drill domain-3 round 2 (Q1)
**Question (paraphrased):**
> A `.claude/settings.json` has both an `allow` list and a `deny` list. A user asks Claude to run `git commit`, which matches neither list. What happens?

**My answer:** The commit succeeds automatically; unmatched tools fall through to a default that auto-approves common git operations.
**Correct answer:** The commit prompts the user for approval. Three-state priority: deny is checked first, allow is checked second, unmatched falls through to the standard interactive permission prompt.

**Why I got it wrong:**
- [x] Implicit-helpful-default pattern: assumed an unstated "auto-approve common git operations" behaviour exists
- [x] Conflated "not denied" with "permitted without asking"

**Mental model (one sentence I'll remember next time):**
> Three states, strict priority: deny blocks, allow skips prompt, unmatched prompts. `allow` is convenience (skip the prompt), not gating. The harness has no semantic awareness of command categories — it's pure pattern matching on `Bash(...)` strings.

**Pattern this fits:** Implicit-helpful-default — trusting the system does more than it documents.

**Reviews:**
- +3 days (2026-05-11): [ ] passed / [ ] failed
- +7 days (2026-05-15): [ ] passed / [ ] failed
- +14 days (2026-05-22): [ ] passed / [ ] failed

**Status:** Open

---

## M005 — 2026-05-08 — Domain 3 — Headless invocation statelessness in ephemeral CI
**Source:** Practice Coach $drill domain-3 round 2 (Q2)
**Question (paraphrased):**
> A team runs `claude -p` in GitHub Actions for PR reviews. Cold context costs 30-90s per run, and large PRs exceed attention budget. Which approach fixes both?

**My answer:** Use `--session-id <persistent-id>` to resume context across CI runs, and `--continue` for diff chunks within a PR.
**Correct answer:** Accept that cold context is inherent to headless invocations on ephemeral runners — mitigate with lean CLAUDE.md and scoped working dir. For attention budget, decompose semantically (logical groups), one `claude -p` per chunk with chunk-aware prompts, then a final aggregation step.

**Why I got it wrong:**
- [x] Implicit-helpful-default pattern: assumed `--session-id` would persist state across ephemeral runners that have no place for it to live
- [x] "Real flags applied to the wrong execution model" — both flags exist, neither solves the stated problem
- [x] `--continue` worsens the attention-budget problem rather than fixing it (still one Claude holding all the context)

**Mental model (one sentence I'll remember next time):**
> Headless `claude -p` is stateless across invocations — no warmup, no carryover. On ephemeral CI runners (fresh VM per run), session state has nowhere to live, so `--session-id` resumption is impossible by physics, not by feature gating. When a flag is proposed in a CI context, ask: "where would that state physically live?"

**Pattern this fits:** Implicit-helpful-default + real-flags-wrong-context — applying real mechanisms to problems they don't solve.

**Reviews:**
- +3 days (2026-05-11): [ ] passed / [ ] failed
- +7 days (2026-05-15): [ ] passed / [ ] failed
- +14 days (2026-05-22): [ ] passed / [ ] failed

**Status:** Open

---

## M006 — 2026-05-08 — Domain 3 — Hook exit-code contract
**Source:** Practice Coach $drill domain-3 round 2 (Q3)
**Question (paraphrased):**
> A `PreToolUse` hook runs and detects a protected path, but the edit goes through anyway. Most likely cause?

**My answer:** PreToolUse hooks run advisory/parallel; a stricter `PreToolBlocker` hook type is needed for synchronous blocking.
**Correct answer:** The hook printed a warning to stdout but exited with code 0. Hooks signal blocking via exit codes, not stdout content. Exit 0 = approved; exit 2 = block (with stderr as the reason).

**Why I got it wrong:**
- [x] Invented-feature pattern: fabricated a `PreToolBlocker` hook type that doesn't exist
- [x] Recast the real `PreToolUse` mechanism as "advisory/parallel" — it's actually synchronous, that's the whole point of "pre"
- [x] Didn't check the contract of the real mechanism before reaching for a fabricated stricter one

**Mental model (one sentence I'll remember next time):**
> Hooks are processes. Processes signal to their callers via exit codes — stdout is data, stderr is messages, exit code is the decision. When a hook "ran but didn't block," check exit code first, not script logic. Block = exit 2 with stderr reason. `PreToolUse` is already synchronous and blocking — there is no stricter variant to reach for.

**Pattern this fits:** Invented-feature — when the known mechanism appears to fail, imagining a stricter named variant rather than verifying the actual contract.

**Reviews:**
- +3 days (2026-05-11): [ ] passed / [ ] failed
- +7 days (2026-05-15): [ ] passed / [ ] failed
- +14 days (2026-05-22): [ ] passed / [ ] failed

**Status:** Open

---

## Meta-pattern across M004, M005, M006

**Single failure mode:** trusting the system does more than it documents.

- M004: assumed unstated "auto-approve common git operations" default
- M005: assumed unstated cross-invocation state persistence
- M006: assumed unstated stricter hook variant

**Counter-heuristic, applied to every future answer:**
> "Can I point to this behaviour in the docs? If no, but it would make sense if it worked this way — that's a red flag, not a feature."

Claude Code is explicit contracts and pattern matching. No hidden helpful defaults, no semantic categorization, no auto-inference of intent. The boring contract-based answer beats the clever inferred-behaviour answer most of the time on this exam.

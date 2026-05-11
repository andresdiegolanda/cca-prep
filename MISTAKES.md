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

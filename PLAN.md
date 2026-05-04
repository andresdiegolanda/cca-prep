# CCA-F Study Plan

> **Version:** 1.0.0
> **Created:** 2026-05-03
> **Last updated:** 2026-05-03

---

## 0. Verification first (before locking anything)

Before any study begins, verify on anthropic.com and Skilljar:

- [ ] Exact credential name (assumed: **Claude Certified Architect — Foundations**, code **CCA-F**)
- [ ] Pass threshold (assumed: **720/1000 scaled**)
- [ ] Number of questions on the real exam (assumed: 60)
- [ ] Time limit (assumed: 120 minutes)
- [ ] Current domain weights:
  - [ ] Domain 1 — Agentic Architecture (assumed 27%)
  - [ ] Domain 2 — Claude Code Configuration (assumed 20%)
  - [ ] Domain 3 — Prompt Engineering (assumed 20%)
  - [ ] Domain 4 — Tool Design & MCP (assumed 18%)
  - [ ] Domain 5 — Context Management (assumed 15%)
- [ ] Practice exam length and policy (one-time vs replayable)
- [ ] The six exam scenarios — names and any updates

If any value differs from the assumption, update this file and bump version in `CHANGELOG.md`.

---

## 1. Total budget

**30 hours over 5 weeks.** Plans slip. Real life — production support, Turco articles, framework PRs — eats roughly 30% of any planned schedule. Week 5 is buffer, not extra.

Daily minimum: 1 hour. Daily maximum recommendation: 2 hours. Beyond 2 hours retention drops sharply.

---

## 2. Anti-rules

Non-negotiable. Re-read at the start of every session.

1. **This repo is not a framework.** No infrastructure, no tooling, no automation. Markdown only.
2. **No design-first-ai work during a study session.** Repo closed locally. The framework is not the exam.
3. **No Turco / Ibrahim Ferreyra writing during a study session.** Different identity, different time.
4. **No LinkedIn during a study session.** Browser profile without LinkedIn logged in is the only reliable defence.
5. **Phone in another room** during the study hour. Cognitive discipline at hour 23 of an exhausting day is not a real plan; environmental discipline is.
6. **The Skilljar official 60-question practice exam is taken ONCE, COLD, in Week 3.** Repeated exposure invalidates it as measurement. The 900+ target from the original plan is dropped.
7. **AI-generated practice (Practice Coach) is calibration, not measurement.** It trains me on Claude's distractor style. Anthropic's exam writers write differently.
8. **Never used Claude Code is a defect, not a footnote.** Week 0 closes it before any domain study begins.

---

## 3. Vocabulary risk

I have a personal AI collaboration framework with parallel terminology to Anthropic's. The exam tests Anthropic's vocabulary, not mine. Concrete divergences I already know exist:

| My framework term | Likely Anthropic term | Risk |
|-------------------|------------------------|------|
| "Six-layer context architecture" | _(verify — Anthropic uses different framing)_ | High |
| "Two-document rule" | _(not Anthropic's terminology)_ | High |
| "Skill files" | Anthropic has its own definition of skills (skill-creator etc.) | Critical |
| "Knowledge priming" | _(Garg's term, may not be Anthropic's)_ | Medium |
| "Design-first collaboration" | _(my term)_ | Medium |

**Discipline:** Each domain file in `domains/` has a **Vocabulary mapping** table. Fill it as I study. If a Learning Coach explanation uses different wording from mine, that goes in the table. Fluency in my own framework is **not** fluency in Anthropic's.

---

## 4. Week 0 — Hands-on baseline (10 hours, GATING)

**Goal:** close the practical gap. I have not used Claude Code directly. Domain 2 (20%) and parts of Domain 4 (18%) test configuration decisions and MCP setup that cannot be learned by reading.

Tasks (track in `hands-on/README.md`):

- Install Claude Code CLI on local machine
- Run a real session against a small private repo (NOT design-first-ai — disposable)
- Write a `CLAUDE.md` for that repo
- Configure `.claude/settings.json` with `allowedTools`, `disallowedTools`, permission rules
- Use slash commands at least once each: `/init`, `/clear`, `/compact`, `/cost`, `/memory`, `/model`
- Spawn a subagent via Task tool
- Build a minimal MCP server (5 tools max, Python or Node)
- Wire it via `.mcp.json`
- Run end-to-end task using the MCP server's tools
- Document what surprised me in `hands-on/notes.md`

**Gate:** No Domain study starts until `hands-on/notes.md` has at least 5 concrete observations about Claude Code behaviour that differed from theory. If 10 hours produces nothing surprising, I'm doing it wrong — extend.

---

## 5. Week 1 — Cold diagnostic + Domains 1 & 4

### Day 1 — Cold diagnostic (2 hours)

- Practice Coach: `$quiz 20` across all five domains, weighted, with no prep
- Log results in `mocks/YYYY-MM-DD-baseline-quiz.md`
- This drives the rest of the schedule. If a "weak" domain comes back stronger than assumed, reallocate.

### Day 2-3 — Domain 1: Agentic Architecture (27%)

- Learning Coach: `$domain 1` from start
- Update `domains/01-agentic-architecture.md` as concepts land
- Fill **Vocabulary mapping** for every concept where Anthropic's term differs from common practitioner terminology

### Day 4 — Domain 4: Tools & MCP (18%)

- Learning Coach: `$domain 4`
- Cross-reference with my Week 0 MCP server — annotate `domains/04-tools-mcp.md` with where theory matched practice and where it didn't

### Day 5 — Practice + first spaced repetition

- 15 min: re-state Domain 1 concepts from memory in my own words, then check `domains/01-*.md`
- Practice Coach: `$drill domain-1` (5 questions)
- Practice Coach: `$drill domain-4` (5 questions)
- Every wrong answer → `MISTAKES.md`

---

## 6. Week 2 — Remaining domains

### Day 1 — SR + Domain 2 (20%)

- 15 min: Domain 1 + 4 review (re-state from memory, check, log gaps)
- Learning Coach: `$domain 2`
- Cross-reference with Week 0 hands-on artifacts

### Day 2 — SR + Domain 3 (20%)

- 15 min: Domain 2 review
- Learning Coach: `$domain 3`
- This is my strong area. Go fast. Focus on Anthropic vocabulary divergence — that's the actual risk.

### Day 3 — SR + Domain 5 (15%)

- 15 min: Domain 3 review
- Learning Coach: `$domain 5`
- Same pattern: strong area, vocabulary check

### Day 4 — Practice consolidation

- Practice Coach: `$quiz 20`
- All wrong answers → `MISTAKES.md`

### Day 5 — `$weak` on quiz mistakes

- Learning Coach: `$weak [topic]` for every recurring miss
- Update domain files

---

## 7. Week 3 — Scenarios + cold mock

### Day 1-2 — Scenarios (one per session, three sessions)

- Practice Coach: `$scenario` for each of the six exam scenarios
- For each, note which domains it stresses and what the typical traps are

### Day 3 — Pressure tests

- Practice Coach: `$traps` (1 question per distractor class)
- Practice Coach: `$blind` (2 questions, hidden scenario)
- Practice Coach: `$hard` (1 question on weakest area)

### Day 4 — Skilljar official 60-question mock — COLD

- No source review the day before
- Take in one sitting, ~120 minutes
- Log full results in `mocks/YYYY-MM-DD-skilljar-official.md`
- This is the calibrated measurement. Not the AI quizzes.

### Day 5 — `$weak` on every Skilljar mistake

- Learning Coach: `$weak [topic]` for each
- Update domain files

---

## 8. Week 4 — Closing gaps

### Day 1 — Drill lowest-scoring Skilljar domain

- Practice Coach: `$drill [worst domain]` — 10 questions

### Day 2 — Mistakes review pass

- Walk through every entry in `MISTAKES.md` flagged for review
- Re-test the concept by re-stating from memory; if I can't, re-add to review queue

### Day 3 — Light review only

- No new material
- 15 min per domain re-stating mental models out loud

### Day 4 — Rest

- No prep. Sleep.

### Day 5 — Real exam

---

## 9. Week 5 — Buffer

Reserved for slip. Not "extra study time." If Weeks 0–4 stayed on track, Week 5 is unused.

---

## 10. Daily session structure

| Block | Duration | Purpose |
|-------|----------|---------|
| Re-read anti-rules (top of this file) | 1 min | Friction against drift |
| Spaced repetition (Week 2+) | 15 min | Re-state previous domain from memory |
| New material or drill | 30–40 min | Coach interaction |
| Update MISTAKES.md | as needed | Every wrong answer logged with mental model |
| Update SESSIONS.md | 5 min | Append session entry |
| Commit | 1 min | `session NNN: [focus]` |

---

## 11. Abort / re-plan triggers

- **If diagnostic (Week 1 Day 1) shows >40% wrong:** extend Week 0 hands-on by 5 hours, push exam date.
- **If Skilljar mock (Week 3 Day 4) <70%:** do not schedule the real exam. Re-plan from `MISTAKES.md`. Add another full week.
- **If Skilljar mock >85%:** schedule the real exam. Skip Week 4 Day 1 drill, keep Day 2 review.
- **If three consecutive sessions miss the daily minimum:** the plan is broken. Stop, diagnose, write a `CHANGELOG.md` v1.1.0 entry explaining why.

---

## 12. Resources

- **Anthropic Academy** (Skilljar, free): https://anthropic.skilljar.com
- **Official Exam Guide PDF**: inside Skilljar after enrollment
- **Official 60-question practice exam**: inside Skilljar (used ONCE, cold)
- **claudecertifications.com**: free study guides and practice questions (calibration only)
- **CertSafari**: 610 practice questions (calibration only)

---

## 13. What this plan deliberately does not do

- No "watch every video" task list. Reading the exam guide and one pass of the relevant Skilljar courses is enough; coaches drive the rest.
- No flashcards as a separate system. `MISTAKES.md` with spaced review IS the flashcard system.
- No study group, no peer review. This is a solo prep, optimised for compressed time.
- No documentation polish on this repo. Anti-rule #1.

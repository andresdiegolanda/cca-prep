# Sessions

Append-only log of every study session. Never edit past entries — append corrections as new entries.

## Format

```
## YYYY-MM-DD — Session NNN — Week W Day D
**Duration:** Xh Ym
**Focus:** [domain or activity]
**Coach used:** Learning / Practice / Mock / none
**What I did:**
- ...

**What I learned:**
- ...

**What I struggled with:**
- ...

**Mistakes added to MISTAKES.md:** [count, IDs]

**Next session:** [what's queued]
```

---

## 2026-05-03 — Session 000 — Week 0 Day 0
**Duration:** —
**Focus:** Repo setup
**Coach used:** none

**What I did:**
- Created repo with README, PLAN, CHANGELOG, SESSIONS, MISTAKES, .gitignore
- Coach prompts in `coaches/` (Learning, Practice, Mock)
- Domain stubs in `domains/` (1 through 5)
- Hands-on checklist in `hands-on/README.md`
- Mocks log structure in `mocks/README.md`

**What I learned:**
- The plan has three real holes that almost shipped invisible: no hands-on, AI-generated practice as primary drill, no diagnostic baseline
- The repo itself is a procrastination vector — anti-rules in README and PLAN are the brake

**What I struggled with:**
- _(none yet — no study)_

**Mistakes added to MISTAKES.md:** 0

**Next session:**
- Verify exam name, pass threshold, domain weights, question count from anthropic.com / Skilljar
- If verified, start Week 0 hands-on Task 1: install Claude Code CLI

## 2026-05-06 — Session 001 — Week 0 — Verification
**Duration:** 1h (target)
**Focus:** Verify exam parameters, fix domain ordering, set up Practice Coach
**Coach used:** none (procedural session)

**What I did:**
- Architect verified exam parameters against tutorialsdojo, claudecertifiedarchitect, panaversity, and multiple corroborating sources
- Renamed 4 domain files to match official ordering
- Expanded domain names to full official titles
- Bumped CHANGELOG to 1.1.0
- Set up Practice Coach chat in CCA Exam Prep project

**What I learned:**
- Domain ordering and names in my plan were partially wrong — weights were right, ordering was off
- Exam launched March 2026, restricted to Anthropic Partner Network employees, $99 ($0 for first 5,000 partners)
- Credential valid 2 years; no guessing penalty
- Agent SDK is a first-class exam topic — Week 0 hands-on scope must expand beyond Claude Code CLI
- Anthropic expects 6+ months production experience; my 0 hands-on hours is below their bar — Week 0 cannot be skipped

**What I struggled with:**
- (none — procedural session)

**Mistakes added to MISTAKES.md:** 0

**Open issue:**
- Partner Network eligibility — verified by Andrés during this session, result recorded separately

**Next session:**
- Session 002: Week 0 hands-on scope expansion (Agent SDK + Claude Code), corrected hands-on/README.md
- Eligibility outcome: not Partner Network member yet, deferred to later — exam date not scheduled until resolved

## 2026-05-06 — Session 001 — Closeout
**Duration:** session 001 closed out same day
**Focus:** Verification session wrap-up

**Result:**
- All 10 Claude Code operations completed cleanly
- Commit 3f05fcd staged and ready to push
- Practice Coach chat created and standing by
- Eligibility blocker logged: not Partner Network member, not blocking prep
- Repo state confirmed consistent with PLAN.md v1.1.0 and CHANGELOG v1.1.0

**Open issue to track:**
- Partner Network membership — periodic check (monthly) until resolved. If Fidelity joins, register immediately.

**Next session:** Session 002 — Week 0 hands-on scope expansion. Date TBD by Andrés.

## 2026-05-07 — Session 003 — Track A: Claude Code CLI fluency
**Duration:** ~30 min (under 60-min budget)
**Focus:** Slash commands, Plan Mode, one-shot/resume modes
**Coach used:** Practice Coach (handoff at end of session)

**What I did:**
- Created sandbox repo (claude-code-sandbox, sibling to cca-prep) with a hello.py and README.md
- Walked through 8 slash commands: /init, /clear, /compact, /cost, /memory, /model, /plan, /review
- Toggled Plan Mode via Shift+Tab on a CLI argument parser task; observed real "deviation from plan" trace
- Tested one-shot mode (claude -p) and resume (claude -c)

**Findings:**
- Plan Mode is keyboard-toggled, not slash-command-accessible. /plan does not exist in current Claude Code.
- Slash command parser appears to fuzzy-match unknown commands silently (typed /plan, got /batch response). Worth verifying in Track B.
- Plan Mode produced substantive behaviour: deviated from plan when UTF-16 encoding conflicted with Python file requirements, then surfaced the deviation transparently.

**What I learned:**
- Plan Mode preserves deviation traces — different from Copilot's silent corrections.
- Slash commands in Claude Code are operational (control behaviour, switch models), not just conveniences. /clear and /compact do things prompts cannot.

**Format change agreed for Session 004 onwards:**
- Drop fill-in-the-blank notes template
- Prose-only notes, written when worth thinking through, not for memorization
- Trust learner to manage time within the 60-min budget
- Practice Coach quiz at end of each session remains the verification check

**Mistakes added to MISTAKES.md:** TBD — depends on Practice Coach $drill domain-3 result. Andrés to log post-quiz.

**Next session:**
- Session 004: Track B — Configuration depth (CLAUDE.md, settings.json, hooks, skills). Date: TBD by Andrés before next chat.

## 2026-05-07 — Session 004 — Reviews + Track B (partial)
**Duration:** 40 min (under 60-min budget)
**Focus:** $review skill-frontmatter + $review config-files; Track B Exercises 1, 2, 3
**Coach used:** Practice Coach (two reviews; end-of-session drill deferred to Session 005)

**What I did:**
- $review skill-frontmatter: 1/2 (missed model inheritance — logged as M003)
- $review config-files: 2/2 (M002 mental model stuck)
- Exercise 1 (CLAUDE.md): confirmed working — Claude Code respected written conventions on the next prompt
- Exercise 2 (settings.json permissions + hook): did not work as expected; specifics not retained — deferred to Session 005
- Exercise 3 (custom skill with frontmatter): did not work as expected; specifics not retained — deferred to Session 005

**Findings:**
- Spaced repetition works: M002 stuck (config-files 2/2 today vs missed yesterday)
- Domain 3 cumulative: 4/7 = 57% across two sessions — below pass threshold, still needs work
- Behavioural finding: when something didn't work, moved on rather than investigating. Exam-prep antipattern — Session 005 reopens both failed exercises with a debugging-first stance

**What I learned:**
- Model inheritance in skill frontmatter is by omission, not by `model: inherit` (M003)
- CLAUDE.md genuinely shapes Claude Code's next-prompt behaviour — exercise 1 was the operational confirmation

**Mistakes added to MISTAKES.md:** 1 (M003)

**Next session:**
- Session 005: $drill domain-3 (5 fresh questions for calibration) + reopen Exercises 2 and 3 with debugging-first approach. Date: TBD by Andrés before next chat.

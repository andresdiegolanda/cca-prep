# CCA Exam Prep

Tracking my preparation for the **Claude Certified Architect — Foundations (CCA-F)** exam.

> ⚠️ **Verify before locking the plan**: exam name, pass threshold (assumed 720/1000), domain weights, and practice exam length. Pull these directly from anthropic.com / Skilljar. If anything differs, update [PLAN.md](PLAN.md) and bump the version in [CHANGELOG.md](CHANGELOG.md).

## Anti-rule (read this every time I open the repo)

**This repo is not a framework.** No tooling, no automation, no CI, no GitHub Actions, no contribution guides, no badges, no fancy README. The deliverable is a passing exam score. Every minute spent making this repo nicer is a minute not spent studying.

If I find myself writing infrastructure here, I am procrastinating with intellectual cover.

## Current status

- **Week:** 0 (hands-on baseline — gate before any domain study)
- **Last session:** see [SESSIONS.md](SESSIONS.md)
- **Open mistakes for review:** see [MISTAKES.md](MISTAKES.md)
- **Target exam date:** _TBD — set after Week 0 hands-on completes_

## Files

| File | Purpose |
|------|---------|
| [PLAN.md](PLAN.md) | Full study plan, week by week, with corrections from baseline review |
| [SESSIONS.md](SESSIONS.md) | Append-only log of every study session |
| [MISTAKES.md](MISTAKES.md) | Wrong answers tracked for spaced repetition |
| [CHANGELOG.md](CHANGELOG.md) | Versioned changes to plan and method |
| [coaches/](coaches/) | The three Claude coach prompts (Learning, Practice, Mock) |
| [domains/](domains/) | Notes per exam domain — fill in as I learn |
| [hands-on/](hands-on/) | Week 0 Claude Code baseline checklist and artifacts |
| [mocks/](mocks/) | One file per mock exam attempt |

## Repo conventions

- Markdown only. No code, no build tooling.
- Append-only logs: `SESSIONS.md` and `MISTAKES.md` are never edited, only appended.
- Semantic versioning of the plan in `CHANGELOG.md`. Bump on real changes, not typos.
- One commit per session minimum. Commit message: `session NNN: [focus]`.

## What "done" looks like

- All five domain files in `domains/` have a populated **Vocabulary mapping** table.
- `MISTAKES.md` has every wrong answer logged, each reviewed at +3, +7, +14 days.
- One Skilljar official mock taken cold in Week 3, ≥85% before scheduling the real exam.
- Hands-on `notes.md` exists and documents what was different from theory.

When all four are true, schedule the real exam. Not before.

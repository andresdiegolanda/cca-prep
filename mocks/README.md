# Mock Exams

One file per mock attempt. Naming: `YYYY-MM-DD-source-NN.md`.

## Sources I'll use

| Source | Purpose | Frequency |
|--------|---------|-----------|
| Practice Coach `$quiz 20` | Cold diagnostic (Week 1 Day 1) | Once |
| Practice Coach `$start 20` | Mid-prep calibration | As needed |
| **Skilljar official 60-question practice** | **Calibrated measurement** | **Once, cold, Week 3** |
| Mock Exam `$start` (full 60) | Endurance training | 1-2 times max |
| CertSafari | Bonus calibration | Optional |
| claudecertifications.com | Bonus calibration | Optional |

## Ground rules

1. The Skilljar official mock is taken **once, cold, in Week 3**. Repeated exposure invalidates the measurement.
2. AI-generated mocks (Practice Coach, Mock Exam) are **calibration only** — they reflect Claude's writing style, not Anthropic's exam writers.
3. After every mock, every wrong answer goes into `MISTAKES.md` with a unique ID.
4. The mock's own file in this directory captures the score, breakdown, and pattern observations — not the wrong answers themselves (those live in `MISTAKES.md`).

## File template

```markdown
# Mock: [source] — YYYY-MM-DD

**Source:** Practice Coach generated / Skilljar official / Mock Exam generated / CertSafari / claudecertifications.com
**Question count:** N
**Duration taken:** Xh Ym (target was 2 minutes per question)
**Raw score:** X/N
**Scaled score (if available):** Z/1000
**Pass threshold:** 720/1000 (verify against actual)
**Result:** Pass / Fail

## Domain breakdown

| Domain | Questions | Correct | % | Pass% req'd |
|--------|-----------|---------|---|-------------|
| 1. Agentic Architecture (27%) | | | | |
| 2. Claude Code Configuration (20%) | | | | |
| 3. Prompt Engineering (20%) | | | | |
| 4. Tool Design & MCP (18%) | | | | |
| 5. Context Management (15%) | | | | |

## Scenario breakdown (if applicable)

| Scenario | Questions | Correct | % |
|----------|-----------|---------|---|
| Customer Support Resolution Agent | | | |
| Code Generation with Claude Code | | | |
| Multi-Agent Research System | | | |
| Developer Productivity with Claude | | | |
| Claude Code for CI/CD | | | |
| Structured Data Extraction | | | |

## Mistake IDs added to MISTAKES.md

- MNNN
- MNNN

## What surprised me

-

## Patterns in my mistakes

- (Vocabulary divergence? Distractor traps? Knowledge gap in a specific subdomain? Time pressure?)

## Next actions

- (Specific Learning Coach `$weak` or `$drill` commands queued for next session)
```

## Pass-readiness criteria

Before scheduling the real exam, the Skilljar official mock score must meet:

- Overall ≥ 85% (assumed scaled equivalent ≥ 850/1000)
- No single domain below 70% (assumed scaled ≥ 700/1000)

If overall is ≥85% but one domain is <70%, that domain gets one focused drill week before scheduling.

If overall is <70%, do not schedule. Add a full week and re-plan from `MISTAKES.md`.

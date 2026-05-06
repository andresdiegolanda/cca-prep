# Changelog

All notable changes to the study plan and method.

Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), SemVer.

---

## [1.1.0] — 2026-05-06

### Verified against current Anthropic sources
- Exam name, format, duration, pass threshold, scoring all match assumptions
- Cost, validity, guessing-penalty policy, score-report timing now documented
- Closed-book / no-AI-assistance policy documented

### Changed
- Domain ordering corrected to match official: D1 Agentic, D2 Tool/MCP, D3 Claude Code, D4 Prompt Eng, D5 Context Mgmt
- Domain names expanded to official full forms (& Orchestration / & MCP Integration / & Workflows / & Structured Output / & Reliability)
- Renamed 3 domain files in domains/ to reflect corrected ordering
- PLAN.md verification checklist moved from "to do" to "done" with verification date
- hands-on/README.md updated to reference corrected domain numbers

### Open issue
- Eligibility: exam currently restricted to Claude Partner Network employees. Andrés to verify Fidelity status and personal registration path. If blocked, re-plan from scratch.

### Deferred to later session
- Week 0 hands-on scope expansion to include Claude Agent SDK (currently scoped only to Claude Code CLI)
- Domain file content correction in lower sections (vocabulary tables, cross-refs) — to be done as each domain is studied

---

## [1.0.0] — 2026-05-03

### Added
- Initial repo structure: README, PLAN, SESSIONS, MISTAKES, coaches/, domains/, hands-on/, mocks/
- Three coach prompts: Learning Coach, Practice Coach, Mock Exam
- Domain stub files (1 through 5) with vocabulary mapping table
- Week 0 hands-on baseline as gating prerequisite for any domain study
- Cold diagnostic (Week 1 Day 1) to drive scheduling
- Spaced repetition cadence from Week 2 onwards
- Anti-rules: no framework infrastructure, no Turco/LinkedIn during sessions, phone away
- Vocabulary-mapping discipline per domain (my framework's terms vs Anthropic's)
- Single-cold-attempt rule for Skilljar official mock
- Abort/re-plan triggers based on quiz/mock thresholds

### Verified pending
Items still to confirm against anthropic.com / Skilljar before locking:
- Exam name (assumed CCA-F)
- Pass threshold (assumed 720/1000)
- Number of questions (assumed 60)
- Time limit (assumed 120 minutes)
- Domain weights

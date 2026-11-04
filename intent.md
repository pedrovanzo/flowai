# Intent

Source: https://www.aihero.dev/cohorts/software-factories-for-real-engineers-xdy1m (Matt's cohort "Software Factories for Real Engineers").

Not buying cohort. Reading page only, reverse-engineering own learning path from what Matt mentions, same pattern as `ddemo` (Desktop): self-documenting project, built in numbered Levels, own vocabulary pinned in CONTEXT.md, decisions locked in ROADMAP.md, hard calls get ADRs.

## Page summary (captured 2026-11-04)

Core thesis: quality/reliability/waste in AI coding are engineering problems, solvable with engineering, not babysitting. Goal: engineer stops being bug-catcher, becomes delegator.

Curriculum as stated:
- Week 1: domain glossary + ADRs, large-scale planning via "Wayfinder" skill, three review layers (automated, automated-adversarial, human), codebase design for agent collaboration.
- Week 2: automated quality gates (linters, mutation testing), GitHub Actions for triage/delegation, custom factories per team context.

Tools named: Claude Code CLI (primary), GitHub Actions, custom lint rules, mutation testing, Copilot/Cursor/Windsurf (compat only).

Page is marketing copy, not a spec — doesn't explain Wayfinder, the adversarial review layer, or the lint/mutation setup in implementable detail.

## Assembly plan

1. Reverse-engineer each named concept (Wayfinder skill, 3-layer review, glossary+ADR practice, GH Actions triage/delegation, custom factories) by pulling from Matt Pocock's public git repos — find where these actually ship as code/skills, not just named.
2. Build own Level-by-Level demo (CONTEXT.md glossary, ROADMAP.md with locked decisions + Level table, docs/adr for hard-to-reverse calls), mirroring ddemo's structure, topic = agent-driven software factory instead of Docker.
3. Each Level = one concept made concrete and testable, not a page read.

## Resolved: source repo found

`github.com/mattpocock/skills` ("Skills for Real Engineers," installable via `npx skills@latest add mattpocock/skills` or `claude plugin install mattpocock-skills@claude-plugins-official`). Confirmed real, same author, updated 2026-11-04. Already uses ddemo's own pattern (GLOSSARY.md, docs/adr/, SCOPE.md) — so no need to invent structure, just follow his.

Cohort concept to repo mapping, confirmed by reading each `SKILL.md`:

| Cohort concept | Repo path | What it actually is |
|---|---|---|
| Wayfinder skill | `skills/engineering/wayfinder/SKILL.md` | Plans oversized work as a map of decision tickets (research/prototype/grilling/task types) on the issue tracker; frontier = unblocked unclaimed tickets |
| Domain glossary + ADRs | `skills/engineering/domain-modeling/SKILL.md` + `GLOSSARY-FORMAT.md` + `ADR-FORMAT.md` | Active glossary-sharpening discipline; ADR only when hard-to-reverse + surprising + real tradeoff |
| Codebase design for agents | `skills/engineering/codebase-design/SKILL.md` | Deep-module vocabulary: Module/Interface/Seam/Adapter/Depth/Leverage/Locality |
| Three review layers | `skills/engineering/code-review/SKILL.md` (automated, two-axis: Standards+Spec, parallel sub-agents) + `skills/engineering/triage/SKILL.md` (state machine: needs-triage to ready-for-agent/ready-for-human/wontfix, human decides) | automated + automated-adversarial + human |
| "Software factory" itself | `skills/in-progress/software-factory/SKILL.md` | Literally named the same. Vocabulary: Task/Trigger/Run/Runner, Ticket tracker/Ticket source/Git host/Orchestrator/Observability platform. Philosophy: every trigger is an accelerator, three brakes (automated checks, automated review, human review), start throttled, open up as trust earns it |

Also present in repo, not named on cohort page but adjacent: `engineering/improve-codebase-architecture`, `engineering/diagnosing-bugs`, `engineering/tdd`, `engineering/implement-spec`/`to-spec`/`to-tickets`, `engineering/retro`, `engineering/pr`, `engineering/grill-with-docs`, `misc/git-guardrails-claude-code`, `misc/setup-pre-commit`.

## Open fog

- Deliverable shape deliberately deferred: (a) own ddemo-style demo repo that installs and exercises mattpocock/skills level by level, (b) own set of hand-written skills inspired by his vocabulary, or (c) both. Not deciding now — reading his material first, on own time, before picking a direction. Resume here when ready to shape actual builds.
- Lint/mutation testing specifics from cohort Week 2 not yet located in a single skill — may live in `misc/setup-pre-commit` or be assembled from `software-factory`'s "automated checks" brake rather than a dedicated skill. Confirm by reading `misc/setup-pre-commit` when resuming.

## Status

Reading/reverse-engineering phase done for now (2026-11-04). Everything needed to pick up later is above: source repo, concept mapping, adjacent skills list, open fog. Next session starts from "Open fog" once direction is picked.

---

[^1]: `flowai` initially based after public aihero.dev content by Matt Pocock (cohort page above).

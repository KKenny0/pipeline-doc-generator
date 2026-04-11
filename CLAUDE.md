# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A **Claude Code skill** (not a traditional codebase) that generates Pipeline-level architecture evolution documentation. Produces structured 13-section architecture docs capturing system-wide changes, cross-stage data contracts, and dataflow evolution. No build system, no dependencies, no code — purely markdown-based skill definitions.

- **Invocation**: `/pipeline-doc-generator`
- **Output**: `pipeline-evolution-v{version}.md`

## File Map

- `SKILL.md` — Skill definition: trigger conditions, workflow, visual documentation guidelines, writing constraints
- `references/pipeline-doc.md` — 13-section template specification (Chinese) read by the skill at runtime
- `evals/` — Skill evaluation test cases (gitignored)

## Key Concepts

**Pipeline Doc vs Stage Doc**: This skill covers system-wide architecture (how stages connect, data contracts, evolution history). The companion skill [`stage-doc-generator`](https://github.com/KKenny0/stage-doc-generator) covers single-stage internals. When editing this skill, maintain this boundary.

**13 Sections**: Document Meta → Context → Pipeline Snapshot → Goals → Changes → Contracts → Dataflow → Trade-offs → Impact → Evaluation → Rollout → Risks → History → References. Full spec in `references/pipeline-doc.md`.

**Core constraints** (enforced by the skill):
- Pipeline-level only — no stage internals
- All changes must have Before/After
- All problems must be verifiable
- No code or prompt details
- ASCII diagrams using Unicode box-drawing characters (width ≤ 80)

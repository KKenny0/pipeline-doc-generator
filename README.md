# Pipeline Doc Generator

A [Claude Code](https://claude.ai/claude-code) skill for generating **Pipeline-level architecture evolution documentation**. It produces structured, 13-section architecture docs that capture system-wide changes, cross-stage data contracts, and dataflow evolution.

## How It Works

Invoke the skill in Claude Code:

```
/pipeline-doc-generator
```

Or trigger it naturally by asking to write pipeline architecture docs, system evolution docs, or cross-stage design documents (supports both English and Chinese).

The skill will guide you through:

1. Gathering context — evolution scope, affected stages, triggers
2. Reading the reference template (`references/pipeline-doc.md`)
3. Documenting all 13 sections with Before/After comparisons
4. Outputting a `pipeline-evolution-v{version}.md` file

## Document Structure (13 Sections)

| # | Section | Purpose |
|---|---------|---------|
| 0 | Document Meta | Version, author, impacted stages |
| 1 | Context and Problem Statement | Why this evolution is needed |
| 2 | Current Pipeline Snapshot | System state before changes |
| 3 | Evolution Goals and Design Principles | What we're achieving and how |
| 4 | Key Architectural Changes | Before/After comparisons |
| 5 | Cross-Stage Contract Changes | Data contract changes between stages |
| 6 | Dataflow and Artifact Evolution | How data flows through the system |
| 7 | System-Level Trade-offs | Gain vs Cost analysis |
| 8 | Impact Analysis | Quality, efficiency, stability metrics |
| 9 | Evaluation and Verification Strategy | How to validate changes |
| 10 | Migration and Rollout Plan | Deployment strategy |
| 11 | Known Risks and Failure Modes | What could go wrong |
| 12 | Versioned Evolution History | Historical tracking |
| 13 | References and Source of Truth | Authoritative sources |

## Key Design Principles

- **Pipeline-level focus** — describes how stages work together, not individual stage internals
- **Before/After required** — every change must show clear evolution
- **Verifiable problems** — all issues must be testable, no vague descriptions
- **No code or prompts** — architecture and data flow only
- **ASCII diagrams** — uses Unicode box-drawing characters for pipeline topology, data flow, and cross-stage contracts

## Project Structure

```
pipeline-doc-generator/
├── SKILL.md                    # Skill definition and writing workflow
├── references/
│   └── pipeline-doc.md         # 13-section template specification
└── evals/
    └── evals.json              # Evaluation test cases
```

## Companion Skill

This skill is designed to work alongside [stage-doc-generator](https://github.com/KKenny0/stage-doc-generator), which handles individual Stage implementation documentation. The key difference:

- **Pipeline Doc** (this skill) — system-wide architecture, cross-stage relationships, evolution history
- **Stage Doc** — single stage's internal implementation, inputs/outputs, validation logic

## License

MIT

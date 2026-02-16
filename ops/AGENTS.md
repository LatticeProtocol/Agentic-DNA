---
type: directory_index
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: [directory_index, ops]
---

# ops/ — Operations (Agent Reference)

## Purpose

`ops/` holds operations — the **HOW** of this project. Plans, sessions, templates, and optionally backlog, pipelines, tasks, skills, processes, and deliverables all live here.

## Subdirectories

| Folder | Purpose | Status |
|--------|---------|--------|
| `plans/` | Build plans for multi-session work | Required |
| `sessions/` | Session tracking and audit trail | Required |
| `templates/` | Reusable templates for all content types | Required |
| `backlog/` | Durable ideation and improvement tracking | Recommended |
| `pipelines/` | Content-as-code folder workflows | Optional |
| `tasks/` | Discrete work items | Optional |
| `skills/` | One-time or repeatable agent recipes | Optional |
| `processes/` | Documented human/agent procedures | Optional |
| `deliverables/` | Output artifacts | Optional |

## Key Distinctions

| Type | What It Is | Execution Model |
|------|-----------|----------------|
| **Plan** | Multi-session project decomposed into tasks | Agent sessions with handoff |
| **Pipeline** | Folder-based workflow where file location = state | Automated / agent-driven |
| **Skill** | Standalone recipe for a specific capability | Agent (one-time or repeatable) |
| **Task** | Discrete work item | Plugin/agent tracked |

## Naming

All files follow `type_descriptive_name.md` (underscores only, never hyphens).

## Cross-References

- [ops/plans/AGENTS](ops/plans/adna_standard/template_bare/ops/plans/AGENTS.md) — Build plan protocol
- [ops/sessions/AGENTS](ops/plans/adna_standard/template_bare/ops/sessions/AGENTS.md) — Session lifecycle and tracking
- [obs/AGENTS](ops/plans/adna_standard/template_bare/obs/AGENTS.md) — Knowledge objects (WHAT)
- [org/AGENTS](ops/plans/adna_standard/template_bare/org/AGENTS.md) — Organization (WHO)

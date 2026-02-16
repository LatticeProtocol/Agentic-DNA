---
type: directory_index
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: [directory_index, obs]
---

# obs/ — Knowledge Layer (Agent Reference)

## Purpose

`obs/` holds knowledge objects — the **WHAT** of this project. Context library, decisions, reference material, and domain-specific entities all live here.

## Subdirectories

| Folder | Purpose | Status |
|--------|---------|--------|
| `context/` | Agent context library — synthesized knowledge agents load before domain work | Required |
| `decisions/` | Architecture Decision Records — significant decisions and rationale | Recommended |

Add project-specific subdirectories as needed (e.g., `models/`, `hardware/`, `datasets/`, `specs/`).

## Registry Pattern

obs/ serves as a registry layer. Entries describe and link to objects — they do not duplicate source material. Each entry has frontmatter with type, status, and links to the implementation or source.

## Naming

All files follow `type_descriptive_name.md` (underscores only, never hyphens).

## Cross-References

- [obs/context/AGENTS](ops/plans/adna_standard/template_bare/obs/context/AGENTS.md) — Context library protocol and topic index
- [ops/AGENTS](ops/plans/adna_standard/template_bare/ops/AGENTS.md) — Operations (HOW)
- [org/AGENTS](ops/plans/adna_standard/template_bare/org/AGENTS.md) — Organization (WHO)

---
type: directory_index
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: [directory_index, governance]
---

# org/governance/ — Governance (Agent Reference)

## Purpose

Team governance for this project. Defines roles, decision authority, and operational policies that govern how the project operates.

## Key Files

| File | Purpose |
|------|---------|
| `governance_roles.md` | Team members, responsibilities, and areas of ownership |
| `governance_decision_authority.md` | Decision authority matrix — who approves what category of change |
| `governance_policies.md` | Operational policies — collision prevention, naming, sessions, escalation |

Create governance files as the project matures. Start with roles and policies, add decision authority when the team grows.

## Conventions

- **Naming**: `governance_{topic}.md` (underscores only)
- **Frontmatter**: All files require `type: governance` plus base fields
- **Updates**: Changes to governance files should be coordinated — read before write, confirm with user if `updated` is recent
- **Scope**: Governance files define rules that all agents and users must follow. Treat as authoritative.

## Cross-References

- [CLAUDE.md](ops/plans/adna_standard/template_bare/CLAUDE.md) — Master agent context (references governance rules)
- [org/coordination/AGENTS](ops/plans/adna_standard/template_bare/org/coordination/AGENTS.md) — Cross-agent ephemeral notes
- [ops/sessions/AGENTS](ops/plans/adna_standard/template_bare/ops/sessions/AGENTS.md) — Session protocol

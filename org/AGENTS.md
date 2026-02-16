---
type: directory_index
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: [directory_index, org]
---

# org/ — Organization (Agent Reference)

## Purpose

`org/` holds organization records — the **WHO** of this project. People, teams, coordination notes, governance policies, and optionally customers, partners, contacts, and communications.

## Subdirectories

| Folder | Purpose | Status |
|--------|---------|--------|
| `coordination/` | Cross-agent ephemeral notes — handoffs, urgency signals | Required |
| `governance/` | Roles, decision authority, policies | Required |

Add project-specific subdirectories as needed (e.g., `customers/`, `partners/`, `contacts/`, `team/`, `communications/`, `roadmap/`).

## Naming

All files follow `type_descriptive_name.md` (underscores only, never hyphens).

## Cross-References

- [org/coordination/AGENTS](ops/plans/adna_standard/template_bare/org/coordination/AGENTS.md) — Cross-agent coordination protocol
- [org/governance/AGENTS](ops/plans/adna_standard/template_bare/org/governance/AGENTS.md) — Governance reference
- [obs/AGENTS](ops/plans/adna_standard/template_bare/obs/AGENTS.md) — Knowledge objects (WHAT)
- [ops/AGENTS](ops/plans/adna_standard/template_bare/ops/AGENTS.md) — Operations (HOW)

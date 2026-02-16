---
type: directory_index
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: [directory_index, root]
---

# {PROJECT_NAME} — Agent Guide

## Project Purpose

{ONE_LINE_DESCRIPTION}

## Directory Overview

| Directory | Layer | Contents |
|-----------|-------|----------|
| `obs/` | WHAT — Knowledge | Context library, decisions, domain entities |
| `ops/` | HOW — Operations | Plans, sessions, templates |
| `org/` | WHO — Organization | People, teams, coordination, governance |

## Key Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Agent master context — persona, project map, safety rules, protocols |
| `MANIFEST.md` | Project overview — identity, architecture, entry points |
| `STATE.md` | Dynamic state — current phase, blockers, next steps |
| `AGENTS.md` | This file — root agent guide |
| `README.md` | Human navigation guide |

## Naming

All content files use `type_descriptive_name.md` (underscores only, never hyphens).

Governance files use ALLCAPS: `CLAUDE.md`, `MANIFEST.md`, `STATE.md`, `AGENTS.md`, `README.md`.

## Frontmatter

Every content file requires YAML frontmatter with base fields:

```yaml
---
type: {entity_type}
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: []
---
```

## Agent Startup

1. Read `CLAUDE.md` → structure, rules, persona
2. Read `STATE.md` → current phase, blockers, next steps
3. Check `ops/sessions/active/` → conflicting sessions
4. Check `org/coordination/` → urgent cross-agent notes
5. Create session file in `ops/sessions/active/` → begin work

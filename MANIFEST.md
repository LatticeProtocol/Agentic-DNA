---
type: manifest
created: YYYY-MM-DD
updated: YYYY-MM-DD
last_edited_by: agent_{username}
tags: [manifest, governance]
---

# {PROJECT_NAME} — Project Manifest

## Project Identity

**{PROJECT_NAME}** — {ONE_LINE_DESCRIPTION}

{2-3 sentence expanded description: what this project does, who it serves, what makes it distinctive.}

## Architecture

This project uses the **aDNA (Agentic DNA)** knowledge architecture — a bare triad deployment.

```
{PROJECT_NAME}/
├── obs/    # WHAT — Knowledge objects, context library, decisions
├── ops/    # HOW — Plans, sessions, templates
└── org/    # WHO — People, teams, coordination, governance
```

| Layer | Question | Contains |
|-------|----------|----------|
| **obs/** | WHAT does this project know? | Context library, decisions, domain entities |
| **ops/** | HOW does this project work? | Plans, sessions, templates, pipelines |
| **org/** | WHO is involved? | People, teams, coordination, governance |

## Entry Points

| Audience | Start Here | Then |
|----------|-----------|------|
| **Agents** | `CLAUDE.md` (auto-loaded) | `STATE.md` → `ops/sessions/active/` → work |
| **Humans** | `README.md` | `MANIFEST.md` → browse triad → `STATE.md` |

## Active Builds

| Plan | Status | Description |
|------|--------|-------------|
| *(none yet)* | | |

See `ops/plans/` for build plan details and `STATE.md` for current operational state.

---
type: dashboard
name: "Project Home"
tags: [dashboard, homepage]
cssclasses: [dashboard]
status: active
created: 2026-02-15
updated: 2026-02-15
last_edited_by: agent_{username}
---

# {PROJECT_NAME}

*Your project tagline here.*

> An AI-native knowledge vault built on the **aDNA paradigm** — where humans browse in Obsidian and agents operate via Claude Code.

---

## Operational State

> [!info] Current Phase
> **Phase 0 — Setup.** Vault initialized from the aDNA-Obsidian starter kit. Customize `CLAUDE.md`, `MANIFEST.md`, and `STATE.md` with your project identity, then begin your first build plan.
>
> [[STATE|Operational State]] | [[MANIFEST|Project Overview]] | [[CLAUDE|Agent Context]]

---

## Recent Sessions

```dataview
TABLE WITHOUT ID
  link(file.path, session_id) AS "Session",
  intent AS "Focus",
  status AS "Status"
FROM "ops/sessions"
WHERE type = "session"
SORT created DESC
LIMIT 5
```

---

## Active Plans

```dataview
TABLE WITHOUT ID
  link(file.path, title) AS "Plan",
  status AS "Status",
  owner AS "Owner"
FROM "ops/plans"
WHERE type = "plan" AND status != "completed"
SORT created DESC
```

---

## Vault Overview

| Layer | Files | Purpose |
|-------|-------|---------|
| **obs/** | `$= dv.pages('"obs"').length` | Knowledge objects, context library |
| **ops/** | `$= dv.pages('"ops"').length` | Operations, plans, sessions, templates |
| **org/** | `$= dv.pages('"org"').length` | People, teams, coordination, governance |

---

## Quick Start

> [!abstract] Getting Started
> 1. **Customize governance** — Edit `CLAUDE.md`, `MANIFEST.md`, and `STATE.md` with your project details
> 2. **Create your first plan** — Use the plan template in `ops/plans/`
> 3. **Start a session** — Create a session file in `ops/sessions/active/`
> 4. **Build context** — Add knowledge topics to `obs/context/`

### Templates

| Template | Location | Creates in |
|----------|----------|-----------|
| Session | `ops/templates/template_session.md` | `ops/sessions/active/` |
| Build Plan | `ops/templates/template_plan.md` | `ops/plans/` |
| Context Entry | `ops/templates/template_context.md` | `obs/context/` |

---

## Navigation

> [!quote]
> **[[obs/AGENTS|Knowledge (obs/)]]** — what you know, what you've learned, what you've decided
> **[[ops/AGENTS|Operations (ops/)]]** — how you work, plans, sessions, templates
> **[[org/AGENTS|Organization (org/)]]** — who's involved, coordination, governance

---

## Key Documents

| Document | Purpose |
|----------|---------|
| [[CLAUDE]] | Agent master context — project identity, safety rules, protocol |
| [[MANIFEST]] | Project overview — architecture, entry points, active builds |
| [[STATE]] | Operational state — current phase, blockers, next steps |
| [[AGENTS]] | Root agent guide — directory overview, naming, startup |

---

<div class="homepage-footer">

{PROJECT_NAME} — powered by the [aDNA paradigm](https://github.com/lat-labs/adna-obsidian)

</div>

---
type: state
created: YYYY-MM-DD
updated: YYYY-MM-DD
status: active
last_edited_by: agent_{username}
tags: [state, governance]
---

# Operational State

Dynamic operational snapshot for cold-start orientation. Updated each session.

## Current Phase

**Phase 0 — Setup.** aDNA skeleton deployed. Next: customize CLAUDE.md with project identity, create first build plan, begin work.

## Recent Decisions

| Date | Decision | Source |
|------|----------|--------|
| *(none yet)* | | |

## Active Blockers

None.

## What's Working

- aDNA skeleton deployed (obs/ops/org triad, governance files, starter templates)
- Session tracking ready (`ops/sessions/active/`)
- Build plan system ready (`ops/plans/`)
- Context library ready (`obs/context/`)

## Next Steps

1. **Customize CLAUDE.md** — fill in `{PROJECT_NAME}`, `{DESCRIPTION}`, safety rules, optional domain knowledge
2. **Customize MANIFEST.md** — fill in project identity and architecture details
3. **Create first build plan** in `ops/plans/` if the initial work spans multiple sessions
4. **Begin first session** — create session file, start work, close with SITREP

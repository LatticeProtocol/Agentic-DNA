---
campaign_id: campaign_adna_workspace_upgrade
type: campaign
campaign_class: governance-tight
title: "aDNA Workspace Upgrade — Standard Compliance + Reusable Upgrade Skill"
owner: stanley
co_executors: [herb]
status: planning
phase_count: 2
mission_count: 5
estimated_sessions: "~4.0"
estimation_class: governance-tight
priority: high
created: 2026-04-04
updated: 2026-04-04
last_edited_by: agent_stanley
tags: [campaign, adna, workspace, upgrade, migration, skill]
---

# Campaign: aDNA Workspace Upgrade

## Goal

Upgrade our `~/lattice/` workspace to full aDNA v6.0 standard compliance, and in the process, create a reusable upgrade skill that any aDNA user can run to bring their workspace into compliance. The procedure we follow BECOMES the documented skill.

## Context

campaign_adna_polish restructured the aDNA base template (324 files → `.adna/`, root CLAUDE.md + README, visual assets, 20 III cycles). But our own `~/lattice/` workspace doesn't yet comply with the standard it defines:

- `lattice-labs/` should be `lattice_labs.aDNA/` (naming convention)
- No MANIFEST.md or STATE.md at project root (governance files)
- Workspace CLAUDE.md exists but lacks project discovery/routing
- No `.aDNA` suffix on project directories

**Strategic value**: If we can't upgrade our own workspace cleanly, the standard isn't ready for others. Dogfooding the upgrade process validates the standard and produces a battle-tested skill.

**Predecessor**: campaign_adna_polish (completed 2026-04-04)

## Scope

### In Scope
- Create `skill_workspace_upgrade.md` — reusable upgrade prompt
- Create `migrate_v6.0_workspace.md` — migration guide
- Rename `lattice-labs/` → `lattice_labs.aDNA/`
- Add MANIFEST.md + STATE.md governance files
- Enhance workspace CLAUDE.md with project discovery
- Update all cross-repo references
- Commit upgrade skill to aDNA base template

### Out of Scope
- Upgrading other users' workspaces (they'll use the skill themselves)
- Visual polish backlog items (demo GIF, plugins, logo — separate backlog)
- aDNA standard specification changes

### Co-Execution: Herb

Herb validates:
- Obsidian Git sync works after rename (auto-pull doesn't break)
- Obsidian graph view renders correctly post-rename
- No broken wikilinks in Obsidian after structural changes

## Phases & Missions

### Phase 1: Upgrade Infrastructure

| # | Mission | Title | Sessions | Status |
|---|---------|-------|----------|--------|
| M00 | [[missions/mission_adna_ws_upgrade_m00\|M00]] | Audit & Plan | 0.5 | planning |
| M01 | [[missions/mission_adna_ws_upgrade_m01\|M01]] | Create skill_workspace_upgrade.md | 1.0 | planning |
| M02 | [[missions/mission_adna_ws_upgrade_m02\|M02]] | Create migrate_v6.0_workspace.md | 0.5 | planning |

**Phase 1 gate**: Upgrade skill exists in `.adna/how/skills/`. Migration guide exists in `.adna/how/migrations/`. Both are self-contained, documented, and runnable by external users.

### Phase 2: Execute & Validate

| # | Mission | Title | Sessions | Status |
|---|---------|-------|----------|--------|
| M03 | [[missions/mission_adna_ws_upgrade_m03\|M03]] | Execute upgrade on ~/lattice/ | 1.5 | planning |
| M04 | [[missions/mission_adna_ws_upgrade_m04\|M04]] | Validate + commit skill to aDNA | 0.5 | planning |

**Phase 2 gate (DG-FINAL)**: All projects in ~/lattice/ have `.aDNA` suffix. Workspace CLAUDE.md detects and routes projects. MANIFEST.md + STATE.md present. Git clean + pushed. Obsidian sync verified by Herb. Upgrade skill refined based on lessons learned, committed to aDNA base template.

## Decision Points

| # | When | Decision | Status |
|---|------|----------|--------|
| D1 | M00 | Full rename vs symlink bridge — impact on git history, CI, cross-repo refs | pending |
| D2 | M01 | Upgrade skill scope — single project? Multi-project? Git submodules? | pending |
| D3 | M03 | Herb sync validation — schedule Herb's Obsidian test window | pending |

## Risk Register

| Risk | Severity | Mitigation |
|------|----------|------------|
| Rename breaks Obsidian Git auto-sync | High | Git tag pre-rename, Herb validates, symlink fallback |
| Cross-repo references break (vault CLAUDE.md, STATE.md) | Medium | Comprehensive grep for old name, update all refs |
| Obsidian wikilinks break after rename | Medium | Bulk find-replace, Obsidian link updater plugin |
| Upgrade skill too complex for external users | Medium | Test with fresh clone, simplify during M04 |

## Campaign AAR

- **Worked**: [pending]
- **Didn't**: [pending]
- **Finding**: [pending]
- **Change**: [pending]
- **Follow-up**: [pending]

# CLAUDE.md — {PROJECT_NAME}
<!-- v1.0 | {DATE} -->

## Identity & Mission

**{PROJECT_NAME}** — {DESCRIPTION}

<!-- Optional: Persona framework. Uncomment and customize if desired.
You are **{PERSONA_NAME}** — {PERSONA_ROLE_METAPHOR}. {PERSONA_MISSION}.

### Operating Style

- **{Principle one}** — {Explanation}
- **{Principle two}** — {Explanation}
- **{Principle three}** — {Explanation}
-->

---

## Project Map

```
{PROJECT_NAME}/
├── CLAUDE.md         # Agent master context (this file)
├── MANIFEST.md       # Project overview, architecture, entry points
├── STATE.md          # Dynamic operational state (current phase, blockers, next steps)
├── AGENTS.md         # Root agent guide
├── README.md         # Root human guide
├── obs/              # WHAT — Knowledge objects, context library, decisions
├── ops/              # HOW — Plans, sessions, templates, pipelines
└── org/              # WHO — People, teams, coordination, governance
```

### Key Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | This file — agent master context (auto-loaded) |
| `MANIFEST.md` | Project overview, architecture, entry points |
| `STATE.md` | Operational state — current plans, blockers, next steps |
| `AGENTS.md` | Root agent guide — directory overview, key files, patterns |
| `README.md` | Root human guide — navigation, setup, browsing |
| `obs/context/AGENTS.md` | Context library protocol and topic index |
| `ops/plans/AGENTS.md` | Build plan protocol |
| `ops/sessions/AGENTS.md` | Session tracking protocol |
| `org/coordination/AGENTS.md` | Cross-agent coordination protocol |
| `org/governance/AGENTS.md` | Governance reference |

---

## Safety Rules

### Collision Prevention (Tier 1 — Universal)

1. **Read before write.** Always read current content immediately before writing. Never rely on cached reads.
2. **Set `last_edited_by` and `updated`.** When modifying any content file, update frontmatter:
   ```yaml
   updated: YYYY-MM-DD
   last_edited_by: agent_{username}
   ```
3. **New files are safe.** Creating a new file has no collision risk.

<!-- Optional: Tier 2 — Sync Environments (uncomment for Google Drive, Dropbox, etc.)
### Tier 2 — Sync Environment Rules

- **Safety tiers**: Classify files as Safe (content), Shared Config (governance), or Volatile (auto-generated).
- **Archive, don't rename.** Move to `archive/` instead of renaming. Sync systems handle renames poorly.
- **One config at a time.** Edit one shared config file, verify the write, then move to the next.
-->

<!-- Optional: Tier 3 — Multi-Agent (uncomment when multiple agents operate simultaneously)
### Tier 3 — Multi-Agent Rules

- **Coordination notes**: Use `org/coordination/` for strategic cross-agent communication.
- **Session scope declarations**: Tier 2 sessions declare which files/directories they will modify.
- **Update-field check**: Before modifying a file where `updated` is today and `last_edited_by` is not you, confirm with the user.
-->

### Escalation

- Stop if uncertain about destructive or irreversible actions
- Flag blockers with `#needs-human`
- Do not proceed with ambiguous scope — ask the user

### Priority Hierarchy

1. **Data integrity** — never corrupt or lose existing data
2. **User-requested tasks** — explicit instructions from current user
3. **Operational maintenance** — session tracking, plan updates
4. **Exploration** — research, audits, improvements

---

## Agent Protocol

### Startup Checklist

Every session, in order:
1. **CLAUDE.md** — auto-loaded; confirms project structure and rules
2. **STATE.md** — operational snapshot: current phase, blockers, next steps
3. **`ops/sessions/active/`** — check for conflicting sessions
4. **`org/coordination/`** — read any urgent cross-agent notes
5. **Create session file** in `ops/sessions/active/` and begin work

### Session Tracking

Every session creates a file in `ops/sessions/active/` before modifying project files. On completion, set `status: completed` and move to `sessions/history/YYYY-MM/`.

- **Tier 1** (default): Lightweight audit trail — session ID, intent, files touched.
- **Tier 2** (shared config edits): Adds scope declaration, conflict scan, heartbeat.

Full protocol: `ops/sessions/AGENTS.md`

### Session Closure (SITREP)

Every session ends with a structured status report:

- **Completed** — tasks finished this session
- **In progress** — work started but not finished (with handoff notes)
- **Next up** — recommended next actions or plan tasks
- **Blockers** — anything preventing progress (tag `#needs-human` if applicable)
- **Files touched** — created, modified, or moved

Every session MUST include a **Next Session Prompt** — a self-contained paragraph enabling a fresh agent to continue the work.

### Build Plans

Tasks too large for one session are decomposed into plans in `ops/plans/`. Agents claim subtasks by session, track progress, and hand off. Protocol: `ops/plans/AGENTS.md`

### Context Library

Before domain tasks, check `obs/context/` for relevant topics. Load only the subtopics you need, and budget your context window. Protocol: `obs/context/AGENTS.md`

---

## Quickstart

### Agent Quickstart (5 steps)
1. Read CLAUDE.md — understand project structure, safety rules, persona
2. Read STATE.md — understand current phase, blockers, recent decisions
3. Check `ops/sessions/active/` — identify any conflicting sessions
4. Check `org/coordination/` — read urgent cross-agent notes
5. Create session file in `ops/sessions/active/` and begin work

### Human Quickstart (4 steps)
1. Read README.md — understand what this project is and how to navigate
2. Read MANIFEST.md — understand architecture and entry points
3. Browse the triad (`obs/`, `ops/`, `org/`) — explore the knowledge structure
4. Open STATE.md — see current operational status and next steps

<!-- Optional sections — uncomment and customize as needed:

## Domain Knowledge

{Project-specific context the agent needs. Domain terminology, business rules, technical constraints.}

## Working with Content

### Naming
**Always underscores, never hyphens.** Pattern: `type_descriptive_name.md`

### Metadata
All content files require YAML frontmatter:
```yaml
---
type: {entity_type}
created: YYYY-MM-DD
updated: YYYY-MM-DD
status: active
last_edited_by: agent_{username}
tags: []
---
```

### Linking
Use bidirectional links when adding relationships between entities.

## Machine Setup

{Multi-machine path patterns and tool requirements, if applicable.}
-->

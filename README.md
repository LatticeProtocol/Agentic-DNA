# aDNA-Obsidian

**A starter kit for building AI-native knowledge systems with [Obsidian](https://obsidian.md) and [Claude Code](https://docs.anthropic.com/en/docs/claude-code).**

Clone this repo, open it in Obsidian, point Claude Code at it, and you have a structured knowledge vault where humans browse visually and AI agents operate programmatically — from the same set of markdown files.

---

## What is aDNA?

**Agentic DNA (aDNA)** is a knowledge architecture pattern for projects where humans and AI agents collaborate. It organizes all project knowledge into three layers:

| Layer | Question | Contains |
|-------|----------|----------|
| **obs/** | *What do we know?* | Knowledge objects, context library, research, decisions |
| **ops/** | *How do we work?* | Plans, sessions, templates, pipelines, processes |
| **org/** | *Who is involved?* | People, teams, coordination, governance |

Five governance files at the root tie it together:

- **`CLAUDE.md`** — The agent's master context. Claude Code reads this automatically on startup. It defines the project identity, safety rules, agent protocol, and domain knowledge.
- **`MANIFEST.md`** — Project overview for humans and agents. Architecture, entry points, active builds.
- **`STATE.md`** — Dynamic operational snapshot. Current phase, blockers, next steps. Updated each session.
- **`AGENTS.md`** — Structured agent guide. Directory overview, naming conventions, startup checklist.
- **`README.md`** — Human navigation guide.

The result is a system where an agent can cold-start into any project, orient itself from `CLAUDE.md` → `STATE.md`, and begin productive work — while a human can open the same vault in Obsidian and browse it as a rich, linked knowledge graph.

---

## What's Included

```
adna-obsidian/
├── .obsidian/              # Pre-configured Obsidian (18 plugins, theme, CSS)
│   ├── plugins/            # Homepage, Templater, Notebook Navigator configs
│   └── snippets/           # 5 CSS snippets (Tokyo Night purple, tables, Mermaid, etc.)
├── obs/                    # Knowledge layer
│   ├── AGENTS.md           #   Agent protocol for knowledge objects
│   └── context/            #   Context library (agent knowledge base)
│       └── AGENTS.md       #     Context library protocol
├── ops/                    # Operations layer
│   ├── AGENTS.md           #   Agent protocol for operations
│   ├── Home.md             #   Starter dashboard (homepage plugin target)
│   ├── plans/              #   Build plans (multi-session task tracking)
│   │   └── AGENTS.md       #     Build plan protocol
│   ├── sessions/           #   Session tracking (audit trail)
│   │   ├── AGENTS.md       #     Session protocol
│   │   ├── active/         #     Active sessions (agent creates files here)
│   │   └── history/        #     Completed sessions (moved here on close)
│   └── templates/          #   File templates
│       ├── template_session.md
│       ├── template_plan.md
│       └── template_context.md
├── org/                    # Organization layer
│   ├── AGENTS.md           #   Agent protocol for org records
│   ├── coordination/       #   Cross-agent notes
│   │   └── AGENTS.md       #     Coordination protocol
│   └── governance/         #   Roles, policies, decision authority
│       └── AGENTS.md       #     Governance protocol
├── CLAUDE.md               # Agent master context (template — customize this)
├── MANIFEST.md             # Project manifest (template)
├── STATE.md                # Operational state (template)
├── AGENTS.md               # Root agent guide
├── README.md               # This file
├── .gitignore
└── LICENSE                 # MIT
```

### Plugins

| Plugin | Purpose |
|--------|---------|
| **Dataview** | Query vault contents as structured data |
| **Templater** | Template engine with folder-to-template mappings |
| **Meta Bind** | Inline inputs and buttons in notes |
| **Homepage** | Opens `ops/Home` on vault startup |
| **Tasks** | Task tracking with checkbox queries |
| **Style Settings** | Theme customization UI |
| **Icon Folder** | Directory icons in file explorer |
| **Advanced Tables** | Markdown table editor with tab navigation |
| **Omnisearch** | Full-text vault search |
| **Advanced Slides** | Presentation mode from markdown |
| **Advanced Canvas** | Enhanced canvas features |
| **Terminal** | Terminal panel inside Obsidian |
| **Ozan's Image in Editor** | Inline image rendering |
| **Kanban** | Kanban boards from markdown |
| **Charts** | Chart rendering from code blocks |
| **BRAT** | Beta plugin installer |
| **Pexels Banner** | Note banners from Pexels or local images |
| **Notebook Navigator** | File explorer profiles and views |

### Templates

| Template | Auto-creates in | Purpose |
|----------|----------------|---------|
| `template_session.md` | `ops/sessions/active/` | Session audit trail with SITREP |
| `template_plan.md` | `ops/plans/` | Multi-session build plan |
| `template_context.md` | `obs/context/` | Context library entry |

### CSS Snippets

| Snippet | Effect |
|---------|--------|
| `tokyo-night-purple.css` | Purple accent overrides for Tokyo Night theme |
| `table_stripes.css` | Alternating table row colors |
| `popover_size.css` | Wider hover popovers |
| `mermaid_override.css` | Cleaner Mermaid diagram styling |
| `notebook_navigator.css` | Navigator panel styling |

---

## Quickstart

### 1. Clone or download

```bash
git clone https://github.com/lat-labs/adna-obsidian.git my-project
cd my-project
```

### 2. Open in Obsidian

Open the cloned folder as a vault in Obsidian. When prompted, **trust the vault** to enable community plugins.

Go to **Settings > Community Plugins** and click **Enable community plugins**. The 18 plugins listed in `.obsidian/community-plugins.json` are pre-configured but need to be installed:

1. Open **Settings > Community Plugins > Browse**
2. Search for and install each plugin (or use BRAT for batch install)
3. Enable all installed plugins

### 3. Install the theme and fonts

- **Theme**: Settings > Appearance > Themes > search "Tokyo Night" > Install and Use
- **Fonts** (optional but recommended): Install [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) and [Space Mono](https://fonts.google.com/specimen/Space+Mono) on your system

### 4. Customize CLAUDE.md

Open `CLAUDE.md` and replace the placeholder tokens:

| Token | Replace with | Example |
|-------|-------------|---------|
| `{PROJECT_NAME}` | Your project name | "Acme Platform" |
| `{DESCRIPTION}` | One-line description | "Internal knowledge base for the engineering team" |
| `{DATE}` | Today's date | "2026-02-15" |
| `{username}` | Your agent username | "stanley" |

Optional: Uncomment the persona framework section to give your agent a name and operating style. Uncomment Domain Knowledge, Working with Content, or Machine Setup sections as needed.

Also update `MANIFEST.md` and `STATE.md` with your project details.

### 5. Start Claude Code

```bash
cd my-project
claude
```

Claude Code automatically reads `CLAUDE.md` on startup, orients from `STATE.md`, and begins working within the aDNA structure. Try:

- *"What's the current state of this project?"*
- *"Create a build plan for [feature]"*
- *"Start a new session and begin work on [task]"*

---

## How It Works

### Agent Protocol

When Claude Code opens an aDNA vault, it follows a startup checklist:

1. **CLAUDE.md** — Read automatically. Defines project identity, safety rules, and operating protocol.
2. **STATE.md** — Operational snapshot. Current phase, recent decisions, blockers, next steps.
3. **`ops/sessions/active/`** — Check for conflicting sessions from other agents.
4. **`org/coordination/`** — Read any urgent cross-agent notes.
5. **Create session file** — Begin tracked work in `ops/sessions/active/`.

### Session Tracking

Every work session creates a file in `ops/sessions/active/`. When the session ends, the agent writes a SITREP (status report) and moves the file to `ops/sessions/history/YYYY-MM/`. This creates an audit trail and enables handoffs between sessions.

### Build Plans

Multi-session tasks are decomposed into build plans in `ops/plans/`. Each plan has numbered tasks that agents claim and complete across sessions. Plans track dependencies, status, and deliverables.

### Context Library

`obs/context/` is the agent's knowledge base — curated files on specific topics that agents load before domain work. Context files have token estimates so agents can budget their context window.

### Safety Rules

aDNA includes tiered collision prevention:

- **Tier 1** (default): Read before write, set `last_edited_by` and `updated` fields
- **Tier 2** (sync environments): Archive instead of rename, one config edit at a time
- **Tier 3** (multi-agent): Coordination notes, scope declarations, update-field checks

---

## Customizing

### Add subdirectories

Extend any layer with project-specific directories:

```
obs/
├── models/          # ML models
├── hardware/        # Infrastructure
├── datasets/        # Data assets
└── context/         # Always keep the context library

ops/
├── pipelines/       # Content-as-code workflows
├── backlog/         # Idea tracking
└── tasks/           # Task management

org/
├── customers/       # CRM records
├── team/            # Team member profiles
└── projects/        # Project records
```

Each new directory should get an `AGENTS.md` (agent-facing protocol) and optionally a `README.md` (human-facing guide).

### Add templates

Create new templates in `ops/templates/` and register them in Templater settings (Settings > Templater > Folder Templates) to auto-apply when creating files in specific directories.

### Build context topics

Create topic directories in `obs/context/` with an `AGENTS.md` index and individual subtopic files. The agent loads these before relevant work to bring domain knowledge into its context window.

---

## Philosophy

aDNA is built on three principles:

1. **Dual-use by design.** Every file serves both humans (browsing in Obsidian) and agents (operating via Claude Code). Markdown is the universal interface.

2. **Structure enables autonomy.** The obs/ops/org triad, governance files, and AGENTS.md protocols give agents enough structure to work independently while staying aligned with project goals.

3. **Context is code.** Knowledge isn't just stored — it's operationalized. Context files have token budgets. Session files create audit trails. Build plans decompose work into claimable tasks. The vault is a living system, not a static wiki.

---

## Learn More

- [aDNA Standard Specification](https://github.com/lat-labs/lattice-protocol) — The full normative spec
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code) — Getting started with Claude Code
- [Obsidian](https://obsidian.md) — The knowledge base that works on local markdown files

---

## License

MIT — see [LICENSE](LICENSE).

Built by [Lattice Labs](https://github.com/lat-labs).

# Changelog

All notable changes to the aDNA knowledge architecture are documented in this file.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## Version Policy

aDNA tracks **two independent version numbers**:

| Track | File | Field | What it covers |
|-------|------|-------|---------------|
| **Governance** | `CLAUDE.md` | `version` (frontmatter) | Vault structure, agent protocol, safety rules, templates, skills |
| **Standard** | `what/docs/adna_standard.md` | Document title | Normative specification — triad structure, object schemas, FAIR metadata |

Both tracks use **Major.Minor** versioning (no patch level):

| Change type | Major bump | Minor bump |
|-------------|-----------|------------|
| **Governance** | Breaking changes to vault structure, CLAUDE.md format, or frontmatter schema | New features, templates, skills, context topics, non-breaking additions, corrections |
| **Standard** | Breaking changes to triad structure, object schemas, or FAIR envelope format | New sections, clarifications, federation stubs, factual fixes |

**Canonical version location**: `CLAUDE.md` frontmatter `version` field (governance track). The migration system (`how/migrations/`) uses this field for pre-flight checks.

Changelog entries are organized by **governance version** (primary heading). Standard version changes are noted within entries when they coincide.

---

## [v5.5] — 2026-03-20

### Added
- `VISION.md` — ecosystem vision document (decentralized frontier lab model, participation ladder)
- "Ecosystem & Vision" section in `README.md` linking to VISION.md
- `VISION.md` row in README Further Reading table

### Changed
- `CLAUDE.md` version bump: `5.4` → `5.5`
- Template counts corrected across all governance files: `17` → `20` (CLAUDE.md, MANIFEST.md, README.md, STATE.md)
- `MANIFEST.md` template table expanded with 6 missing rows (data_record, folder_note, governance, migration, side_quest, quest_result)
- `MANIFEST.md` architecture tree updated with `community/` directory
- `README.md` tree diagram updated with `community/` directory
- `STATE.md` updated to v5.5, added community infrastructure to What's Working, added v5.3-v5.5 upgrade entries

---

## [v5.4] — 2026-03-20

### Added
- `community/quests/` — side-quest experiment specifications directory
- `community/results/` — structured result submissions directory
- `community/tools/aggregate_results.py` — reference aggregation script (stdlib only)
- `community/AGENTS.md` — community directory agent guide
- `how/templates/template_side_quest.md` — quest specification template
- `how/templates/template_quest_result.md` — result submission template
- `what/docs/side_quest_guide.md` — participation guide (find, run, submit quests)
- 2 example quests: `quest_frontmatter_comparison` (medium), `quest_migration_smoke_test` (easy)
- Side-Quest Awareness section in `CLAUDE.md`

### Changed
- `CLAUDE.md` version bump: `5.3` → `5.4`
- `AGENTS.md` project structure updated with `community/` directory
- `README.md` contributing section updated with side-quest mention

---

## [v5.3] — 2026-03-20

### Added
- `how/skills/skill_upstream_contribution.md` — agentic upstream contribution protocol
- Upstream Contribution Awareness section in `CLAUDE.md`
- Upstream Contribution Awareness section in root `AGENTS.md`
- Contributing section in `README.md`

### Changed
- `CONTRIBUTING.md` revised — Agent Contribution Mode replaces static PR-Context pattern; organic discovery over structured proposals
- `CLAUDE.md` version bump: `5.2` → `5.3`
- Code of Conduct reference updated to forward-looking note (pending `CODE_OF_CONDUCT.md`)

### Removed
- Empty `community/proposals/` directory (superseded by agentic backlog pattern)
- Empty `.github/ISSUE_TEMPLATE/` directory (standard GitHub issues sufficient for now)

---

## [v5.2] — 2026-03-19

### Added
- `CHANGELOG.md` — centralized version history (this file)
- Version policy documenting the two-track scheme (governance + standard)
- Migration prompt cross-links in changelog entries

### Changed
- `CLAUDE.md` version bump: `5.1` → `5.2`
- `STATE.md` updated with v5.2 reference and CHANGELOG in "What's Working"

### Migration
- [`migrate_v5.1_to_v5.2.md`](how/migrations/migrate_v5.1_to_v5.2.md)

---

## [v5.1] — 2026-03-18

### Changed
- Lattice types table expanded (7 values: added `infrastructure`, `context_set`, `skill`)
- Template count corrected (10 → 17)
- Standard file paths fixed (pointed to context library instead of nonexistent standalone files)

### Fixed
- CLAUDE.md token estimate corrected (`~650` → `~2500`)
- Object standards table references corrected

### Migration
- [`migrate_v5.0_to_v5.1.md`](how/migrations/migrate_v5.0_to_v5.1.md)

### Standard
- **v2.2** — Federation stub, vault extensions, campaign system, factual fixes

---

## [v5.0] — 2026-03-17

### Added
- OODA cascade (3-level: session, mission, campaign)
- AAR protocol (5-step)
- Escalation cascade (session → mission → campaign → STATE.md)
- Context recipes (6 domain-neutral, 3-tier budgets)
- Mission class discriminator (5 types: build, investigate, design, review, operate)
- 4 new templates (AAR, strategic compass, campaign CLAUDE.md, registry)
- 2 new skills (context quality audit, context graduation)

### Changed
- Framework port from lattice-labs vault to standalone aDNA repo
- 10 adna_core subtopics (was 8) — added ooda_cascade, ontology_workshop

---

## [v4.x and earlier] — 2026-02 to 2026-03

Pre-versioned history. Key milestones (not individually versioned):

- **Lattice publishing** — `latlab lattice publish/pull/compose` CLI workflow
- **Context library** — 4 topics, 23 subtopics, ~58K tokens
- **Object standards** — module, dataset, lattice type standards hardened
- **Canvas Standard v1.0.0** — Round-Trip Protocol v1.0 (YAML authoritative)
- **Type vocabulary** — 19 canonical I/O types (Decision 10)
- **FAIR metadata** — flat↔nested envelope interconversion (Decision 11)
- **Dataset schema** — multi-cloud `.dataset.yaml` with 7 providers (Decision 12)
- **Onboarding skill** — agent-driven interactive vault setup
- **14 example lattices** — business, research, creative, biotech domains
- **Obsidian config** — Tokyo Night theme, 10 CSS snippets, 14 plugins

---
type: directory_index
created: 2026-03-27
updated: 2026-03-27
token_estimate: 13000
last_edited_by: agent_berthier
tags: [directory_index, context, system_configuration]
---

# System Configuration — Context Index

## Overview

How to configure and operate the Claude Code environment for AI-native projects — agent protocols, vault architecture, configuration inheritance, lifecycle hooks, operational memory, orchestration, and the four-layer persistence model. Generic patterns applicable to any aDNA deployment.

## Subtopics

| # | Subtopic | File | ~Tokens | Subtype | Key Content |
|---|----------|------|---------|---------|-------------|
| 1 | Agent Protocol | `context_system_configuration_agent_protocol.md` | ~1,900 | context_core | Partnership model, challenge phase, search-first, autonomy framework, tiered scoping |
| 2 | Vault Architecture | `context_system_configuration_vault_architecture.md` | ~1,800 | context_guide | Multi-vault separation, _meta/ routing, .claude/ read-only, workspace convention |
| 3 | Config Cascade | `context_system_configuration_config_cascade.md` | ~1,500 | context_core | CLAUDE.md inheritance, rules modularization, settings layering, token budgets |
| 4 | Hook System | `context_system_configuration_hook_system.md` | ~2,000 | context_guide | 6 lifecycle events, guard pattern, auto-approve, pre-compaction, async vs blocking |
| 5 | AgentDB | `context_system_configuration_agentdb.md` | ~1,900 | context_guide | SQLite memory, absolute paths, multi-level isolation, learnings, contracts, schema |
| 6 | Orchestration Tiers | `context_system_configuration_orchestration_tiers.md` | ~2,100 | context_guide | Tier 1/2/3 routing, model selection, skills, plugins, parallel-first, contracts |
| 7 | Memory Integration | `context_system_configuration_memory_integration.md` | ~2,400 | context_core | Four persistence layers, auto-memory vs CLAUDE.md, learnings vs AgentDB boundaries |

## Total Token Budget

~13,600 tokens to load all subtopics. Typical session loads 2-3 subtopics (~3K-5K tokens).

## Usage by Task

| Task | Load These Subtopics |
|------|---------------------|
| Setting up a new aDNA workspace from scratch | vault_architecture, config_cascade |
| Configuring agent behavior and identity | agent_protocol, config_cascade |
| Adding lifecycle hooks to a vault | hook_system, config_cascade |
| Setting up AgentDB for cross-session memory | agentdb, memory_integration |
| Planning multi-agent work (tier 2+) | orchestration_tiers, agentdb |
| Understanding where to store what | memory_integration, vault_architecture |
| Debugging configuration inheritance | config_cascade, hook_system |
| Onboarding a new agent to an existing vault | agent_protocol, vault_architecture, memory_integration |
| Designing a model routing strategy | orchestration_tiers |
| Auditing operational memory health | agentdb, memory_integration |

## Dependency Notes

- **agent_protocol** is the entry point — defines the behavioral contract before anything else
- **vault_architecture** and **config_cascade** are complementary — architecture defines structure, cascade defines how configuration flows through that structure
- **hook_system** depends on config_cascade — hooks are configured in settings files
- **agentdb** is self-contained — SQLite schema and patterns
- **orchestration_tiers** references agentdb — contracts are stored in AgentDB
- **memory_integration** is the capstone — references all other subtopics to explain how the layers compose

## Recommended Reading Order

For a full orientation: agent_protocol → vault_architecture → config_cascade → hook_system → agentdb → orchestration_tiers → memory_integration

## Load/Skip Decision

**Load when**:
- Setting up or configuring a new aDNA workspace or vault
- Troubleshooting agent behavior, hook failures, or memory issues
- Designing multi-agent orchestration or model routing
- Onboarding a new agent or explaining the operating environment

**Skip when**:
- Working on domain-specific content (ontologies, lattices, campaigns)
- Performing routine session work in an already-configured vault
- Building or editing context files (load context_engineering instead)

**Token cost**: ~400 tokens (this AGENTS.md)

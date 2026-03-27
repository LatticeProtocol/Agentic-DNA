---
type: context_guide
topic: system_configuration
subtopic: orchestration_tiers
created: 2026-03-27
updated: 2026-03-27
sources: ["Claude Code agent capabilities", "Multi-agent orchestration patterns", "aDNA execution hierarchy"]
context_version: "1.0"
token_estimate: ~2500
last_edited_by: agent_berthier
tags: [context, system_configuration, orchestration, tiers, model_routing, skills, plugins]
---

# System Configuration: Orchestration Tiers

Orchestration tiers classify agent work by scope and complexity, then route execution accordingly. The tier determines how many agents participate, whether adversarial review is required, and which models handle which subtasks. This replaces ad-hoc execution with a repeatable decision framework.

This context file documents tier-based orchestration, model routing, and skill/plugin systems. It is framework-level guidance applicable to any aDNA vault or multi-agent setup.

## Key Principles

### 1. Tier-Based Complexity Routing

Classify every task by file count and complexity before executing. The tier determines the execution pattern.

| Tier | File Count | Execution Pattern | Quality Gate |
|------|-----------|-------------------|-------------|
| **Tier 1** | 1-2 files | Execute directly | Self-review |
| **Tier 2** | 3-5 files | Orchestrate with surgeon agents | Orchestrator review |
| **Tier 3** | 6+ files | Surgeon agents + adversarial QA | Adversary review (up to 3 iterations) |

**Decision rule:** Count files that will change. When ambiguous, assume the higher tier. Downgrading is cheap; recovering from under-scoped work is expensive.

### 2. Separation of Concerns by Role

At tier 2 and above, the orchestrating agent does not write code. Role separation prevents context window pollution and enables parallel execution.

| Role | Responsibility | Writes Code? |
|------|---------------|-------------|
| **Orchestrator** | Scope, plan, coordinate, review | No |
| **Surgeon** | Implement changes within contract scope | Yes |
| **Adversary** | Test, find edge cases, challenge assumptions | No (writes tests) |
| **Validator** | Run lint, typecheck, quality gates | No |

The orchestrator writes contracts. Surgeons read contracts and implement. Adversaries stress-test the output. Validators confirm mechanical correctness.

### 3. Model Routing by Task Type

Different models have different strengths. Routing cheap work to expensive models is waste; routing critical work to cheap models is risk.

| Tier | Model Class | Trigger | Principle |
|------|------------|---------|-----------|
| **Draft** | Fast/cheap | Brainstorm, variations, transforms | Iterate freely, cost is near-zero |
| **Research** | Large context | Web search, bulk reads (50+ files), analysis | Leverage the context window |
| **Implementation** | Balanced | Secondary impl, synthesis, file writes | Cost-effective quality |
| **Core** | Most capable | Planning, design, orchestration, review, creative | Quality over cost |
| **Validation** | Fast | Test execution, lint, typecheck | Trivial checks, fast feedback |

**Implementation note:** Define a routing table in your project's `CLAUDE.md` or rules file. Explicit routing prevents defaulting to the most expensive model for every task.

### 4. Skills as Reusable Methodology

Skills are documented procedures (stored in `how/skills/`) that agents load before acting. They encode proven workflows and prevent agents from improvising suboptimal approaches.

| Task Type | Skills to Load |
|-----------|---------------|
| Building new features | build, quality, testing |
| Fixing bugs | debug, testing |
| Refactoring | refactor, architecture, quality |
| Code review | quality, testing, security |
| API work | api, backend, security |
| Frontend work | design, e2e, quality |
| Security audit | security, quality, testing |
| Performance work | performance, quality, testing |

**Loading order matters.** The primary skill (e.g., `build`) sets the execution framework. Secondary skills (e.g., `quality`) add gates and checks. Always load quality-related skills alongside implementation skills.

### 5. Plugin Architecture

Plugins extend agent capabilities with commands, workflows, and integrations. A well-designed plugin system provides:

| Capability | What It Does |
|-----------|-------------|
| Tier-based orchestration | Auto-classifies and routes work |
| Lifecycle hooks | Pre-commit, post-build, session-start actions |
| Standardized skills | Shared skill library across projects |
| Quality gates | Automated checks before commit |
| Agent spawning | Parallel sub-agent creation and coordination |

A single plugin installation (like KERNEL) can provide all of these as a coherent package, eliminating per-project configuration.

### 6. Parallel-First Execution

When tasks decompose into independent work units, spawn parallel agents. Serial execution is the exception.

**Detection rule:**
- 2+ independent files to create or modify? Parallelize.
- 2+ independent systems to test or verify? Parallelize.
- Research + implementation + documentation? Parallelize.
- Any list of tasks in the description? Parallelize.

**Only skip parallelization when:**
- Task is literally one step (single file edit, single command)
- Steps are dependent (output of A feeds into B)
- User explicitly requests serial execution

### 7. Contract-Driven Coordination

For tier 2+ work, the orchestrator writes a contract specifying scope, files, and success criteria. Agents read the contract, execute within scope, and checkpoint results.

**Contract fields:**

| Field | Purpose |
|-------|---------|
| `goal` | What this work accomplishes |
| `files` | Exact files in scope (agents touch nothing else) |
| `tier` | Complexity classification |
| `success_criteria` | Measurable conditions for completion |
| `skills` | Which skills agents should load |
| `branch` | Git branch for isolation |

Contracts create an audit trail, prevent scope creep, and enable clean handoff between agents.

## Recommendations

- **Always classify before executing.** Count files, determine tier, then route. Never jump straight to implementation.
- **Tier 1: just do it.** Read the file, implement the change, run tests, commit. No ceremony needed.
- **Tier 2: contract and delegate.** Write a contract, spawn surgeon agent(s), review their output, run quality gates.
- **Tier 3: contract, delegate, and verify.** Contract, surgeon(s), adversary review, iterate up to 3 times, then quality gates.
- **Commit after every working state.** Small, frequent commits beat large batches. Each commit is a safe rollback point.
- **Load skills before acting.** Check `how/skills/` for relevant methodology before improvising an approach.
- **Use AgentDB for coordination.** Contracts, checkpoints, and status updates go through a shared store, not verbal summaries.
- **Baseline before changing.** Run tests before making changes (baseline) and after (verification). Comparison catches regressions.

## Examples / Snippets

### Tier Classification Decision

```
User: "Add authentication middleware and update all route handlers"

Step 1 — Count files:
  auth middleware (1) + route handlers (likely 4+) = 5+ files

Step 2 — Classify:
  Tier 3 (6+ files, cross-cutting concern)

Step 3 — Route:
  Orchestrate → surgeon agents → adversary review

Step 4 — Load skills:
  /build, /security, /quality, /orchestration
```

### Tier 2 Contract

```json
{
  "goal": "Add rate limiting to API endpoints",
  "files": [
    "src/middleware/rate-limit.ts",
    "src/config/limits.ts",
    "tests/rate-limit.test.ts"
  ],
  "tier": 2,
  "skills": ["build", "security", "testing"],
  "branch": "feat/rate-limiting",
  "success_criteria": [
    "Rate limiter applies to all /api routes",
    "Configurable per-endpoint limits",
    "Tests cover limit exceeded and reset scenarios"
  ]
}
```

### Parallel Agent Spawn Pattern

```
Spawning 3 parallel agents:

Agent 1 (surgeon): Implement rate-limit middleware
  → Writes: src/middleware/rate-limit.ts
  → Skills: build, security

Agent 2 (surgeon): Add configuration schema
  → Writes: src/config/limits.ts
  → Skills: build

Agent 3 (surgeon): Write test suite
  → Writes: tests/rate-limit.test.ts
  → Skills: testing

All agents write files directly.
Orchestrator reviews merged output.
Run quality gates before commit.
```

### Model Routing Decision

```
Task: "Check if the linter passes on the new file"
  → Validation tier → fast/cheap model
  → No surgeon needed, just run the command

Task: "Design the authentication architecture"
  → Core tier → most capable model
  → Planning task, quality matters more than speed

Task: "Research how competing libraries handle rate limiting"
  → Research tier → large context model
  → Bulk reading, needs context window capacity
```

## Anti-Patterns

| Anti-Pattern | Why It Fails | Correct Approach |
|-------------|-------------|-----------------|
| Serial execution of independent tasks | 3x slower, wastes time | Spawn parallel agents |
| Orchestrator writing code at tier 2+ | Pollutes context window, blocks parallelism | Delegate to surgeon agents |
| No tier classification | Under-scoped work, missed edge cases | Count files, classify, then route |
| Skipping skill loading | Improvised approaches miss proven patterns | Load relevant skills before acting |
| One model for everything | Expensive model on lint = waste; cheap model on design = risk | Route by task type |
| No contract for multi-agent work | Agents duplicate effort or conflict | Write contract to shared store |
| No baseline test run | Cannot distinguish pre-existing failures from regressions | Run tests before and after changes |
| Committing without quality gates | Broken code reaches the branch | Run gates before every commit |

## Integration with aDNA Execution Hierarchy

Orchestration tiers complement the aDNA execution hierarchy (Campaign, Mission, Objective):

| aDNA Level | Typical Tier | Orchestration Pattern |
|-----------|-------------|----------------------|
| **Campaign** | Tier 3 | Multi-mission coordination, phased execution |
| **Mission** | Tier 2-3 | Multi-objective, surgeon agents per objective |
| **Objective** | Tier 1-2 | Single-session, direct execution or small delegation |

Campaigns set the strategic direction. Missions decompose into objectives. Objectives map to orchestration tiers for execution. The tier system handles the *how* of execution; the hierarchy handles the *what* and *when*.

## Sources

- **Claude Code agent capabilities** — sub-agent spawning, model selection, parallel execution, tool routing
- **Multi-agent orchestration patterns** — contract-driven coordination, role separation, adversarial review
- **aDNA execution hierarchy** — Campaign, Mission, Objective decomposition and convergence model

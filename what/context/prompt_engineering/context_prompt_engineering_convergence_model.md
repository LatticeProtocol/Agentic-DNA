---
type: context_research
topic: prompt_engineering
subtopic: convergence_model
created: 2026-02-19
updated: 2026-02-19
sources: ["Original articulation — synthesized from operational experience (126+ sessions)", "Anthropic — Effective Context Engineering for AI Agents", "aDNA Standard v2.1 (§8.7 75% Rule, §10 Context Library)"]
context_version: "1.0"
token_estimate: ~3000
last_edited_by: agent_stanley
tags: [context, prompt_engineering]
quality_score: 4.0
signal_density: 4
actionability: 4
coverage_uniformity: 5
source_diversity: 2
cross_topic_coherence: 5
freshness_category: durable
last_evaluated: 2026-02-19
---

# Prompt Engineering: The Functional-Analytic Convergence Model

## Key Principles

1. **The operational ontology is a convergent decomposition.** The aDNA execution hierarchy (campaign → mission → objective) is not merely organizational — it is a functional-analytic structure where each level narrows the context window, reducing token count while increasing signal density. This is convergence in the mathematical sense: a monotone-decreasing sequence of working sets bounded below by the minimum viable context for a task.

2. **The vault is a function space; campaigns are projections.** A full aDNA instance contains all project knowledge — an unbounded token count. A campaign projects onto a strategic subspace (hundreds of files → tens). A mission projects further onto a task subspace (tens → handful). An objective evaluates a single point — the exact files needed for one session's work. Each projection discards irrelevant dimensions.

3. **Token budget is the norm constraint.** Every level of the hierarchy operates within a token budget ‖x‖ ≤ T. The 75% rule (reserve 25% for reasoning) is a practical norm bound. Convergence means the norm decreases monotonically at each level: vault (~500K tokens) → campaign (~50K relevant) → mission (~15K relevant) → objective (~5K loaded into context).

4. **AGENTS.md files are basis vector labels.** Each directory's AGENTS.md tells the agent what this "dimension" contains — load or skip. They function as basis labels in the decomposition: the agent reads the label, decides if this dimension is relevant to its current projection, and either traverses deeper or prunes the branch.

5. **Context serving is a projection operator.** Graph-based context serving (loading only the subgraph relevant to the current objective) is the practical implementation of projection. The agent doesn't load the full function (vault); it applies P_S — the projection onto subspace S — where S is defined by the current objective's dependencies and context requirements.

6. **Convergence is a design constraint, not an accident.** Every structural decision in the ontology should be evaluated: does this narrow context appropriately at each level? If a mission requires loading 80% of the vault, the decomposition has failed — the "projection" isn't projecting.

## The Analogy Table

| aDNA Concept | Functional Analysis Analog | Practical Effect |
|-------------|---------------------------|-----------------|
| Vault (full instance) | Function space (Hilbert space) | Total knowledge — unbounded token count |
| Campaign | Coarse projection onto subspace | Strategic initiative — hundreds of files → tens |
| Mission | Finer projection | Decomposed task — tens of files → handful |
| Objective | Point evaluation (functional) | Single session — handful of files → exact set needed |
| Context serving | Projection operator P_S | Graph traversal: load only reachable nodes |
| Token budget | Norm constraint ‖x‖ ≤ T | Each level bounded; convergence = monotone decrease |
| AGENTS.md | Basis vector labels | Each tells agent what dimension contains — load or skip |
| Context library topics | Orthogonal subspaces | Independent knowledge domains, loaded selectively |
| Session 75% rule | Norm bound on working set | Reserve capacity for reasoning, not just data |

## Recommendations

### Worked Example: Token Narrowing

Consider a production aDNA vault with the following token profile:

```
Level 0 — Full vault:            ~500,000 tokens (all files)
  ├─ CLAUDE.md + STATE.md:             ~4,000 tokens (always loaded)
  ├─ who/ (CRM + governance):       ~120,000 tokens
  ├─ what/ (context + technical):    ~180,000 tokens
  └─ how/ (operations):             ~200,000 tokens

Level 1 — Campaign (e.g., "aDNA Core Review"):
  ├─ Campaign master doc:                ~2,000 tokens
  ├─ Relevant what/ context:            ~30,000 tokens
  ├─ Relevant how/ missions:            ~15,000 tokens
  └─ Relevant what/ spec docs:          ~12,000 tokens
  Total: ~59,000 tokens (~12% of vault)

Level 2 — Mission (e.g., "Prompt Engineering Research"):
  ├─ Mission file:                         ~800 tokens
  ├─ Target context topic:               ~12,000 tokens
  ├─ Source reference files:              ~5,000 tokens
  └─ Session file:                          ~300 tokens
  Total: ~18,100 tokens (~3.6% of vault)

Level 3 — Objective (e.g., "Write ontology design context file"):
  ├─ Mission objective spec:                ~200 tokens
  ├─ Vault ontology.md (worked example):  ~2,500 tokens
  ├─ aDNA standard §3.1:                  ~1,000 tokens
  ├─ Web research results:                ~3,000 tokens (just-in-time)
  └─ Output file being written:           ~3,000 tokens
  Total: ~9,700 tokens (~1.9% of vault)
```

The convergence: 500K → 59K → 18K → 10K. Each level achieves roughly 3-5× reduction. The agent at Level 3 has 98% less data than the full vault but 100% of the data it needs for this specific objective.

### Designing for Convergence

| Design Decision | Convergent | Divergent |
|----------------|-----------|-----------|
| Directory structure | Deep hierarchy with AGENTS.md routing | Flat directory with everything at root |
| Context library | Topic → subtopic → file with token estimates | Monolithic knowledge dump |
| Mission design | 3-7 objectives per mission, each session-sized | 20+ objectives that span multiple sessions each |
| Campaign phasing | Phase gates that narrow scope progressively | Single phase with all work in parallel |
| AGENTS.md content | "Load this for X tasks, skip for Y" | Generic description with no loading guidance |
| Frontmatter | Token estimate, type, topic for selective loading | Minimal metadata that doesn't support filtering |

### The Projection Sequence in Practice

When an agent starts a session, it executes a convergent sequence of reads:

**Step 1 — Orientation (the full space):**
Read CLAUDE.md + STATE.md. These are the "coordinates" that place the agent in the function space. ~4K tokens.

**Step 2 — Campaign projection:**
Read active campaign master doc. This projects onto the relevant strategic subspace — the agent now knows which missions matter, which phases are active, and what the campaign-level context is. Irrelevant vault areas (completed campaigns, unrelated CRM records) are pruned.

**Step 3 — Mission projection:**
Read the active mission file. This further narrows to the specific task decomposition — which objectives are pending, what files are needed, what the acceptance criteria are.

**Step 4 — Objective evaluation:**
Load the specific files needed for the claimed objective. The agent is now operating at "point evaluation" — the minimum viable context for producing useful output.

This sequence is not arbitrary — it mirrors the mathematical structure of nested projections where each projector's range is a subset of the previous projector's range: P_objective ⊂ P_mission ⊂ P_campaign ⊂ Identity.

### Design Implications

1. **Every directory should be prunable.** If an agent can't determine from AGENTS.md alone whether to traverse into a directory, the routing is insufficient. Add explicit loading guidance: "Load this topic when working on X; skip when working on Y."

2. **Token estimates enable budget-aware traversal.** Without knowing the token cost of loading a topic, the agent can't budget. Include `token_estimate` in every context file frontmatter and in topic AGENTS.md tables.

3. **Campaign → mission → objective is the natural decomposition depth.** Three levels of projection are sufficient for most projects. Adding intermediate levels (phase → sub-phase → task group → task) creates over-decomposition that costs tokens without improving convergence.

4. **Context library topics should be approximately orthogonal.** If loading topic A always requires also loading topic B, they should be merged or one should reference the other as a prerequisite. Orthogonality means the agent can load each topic independently.

5. **Session closure preserves the projection.** The SITREP + next-session prompt captures the current projection state so the next agent doesn't need to recompute it. This is "caching the projection" — the handoff cost is ~500 tokens instead of re-traversing the entire hierarchy.

## Anti-Patterns

- **Loading the full vault.** An agent that reads every file before starting work has failed to converge. The whole point is selective loading via graph traversal.
- **Missions that require the entire vault.** If a mission's objectives collectively touch >50% of vault files, the mission scope is too broad — decompose further until each objective touches a small, well-defined subset.
- **AGENTS.md without loading guidance.** A directory index that says "this directory contains X" without saying "load this when Y, skip when Z" is a basis label without a coefficient — the agent can't evaluate whether to project onto this dimension.
- **Flat context dumps.** A single 50K-token context file defeats convergence. Split into topics with subtopics, each independently loadable at 2-4K tokens.
- **Orphaned objectives.** An objective with no clear mapping to a mission projection (which files does it need? what's the working set?) forces the agent to explore broadly instead of converging narrowly.
- **Over-decomposition.** A campaign with 50 missions of 1 objective each has too many projection levels with too little narrowing at each step. The sweet spot is 5-15 missions of 3-7 objectives each.

## The Mathematical Framing — When to Use It

This convergence model is a **design evaluation tool**, not a runtime algorithm. Use it to:

- **Audit ontology structure** — does the hierarchy produce monotone-decreasing token counts at each level?
- **Design new campaigns** — can each mission be scoped to ~3-5× fewer tokens than the campaign level?
- **Evaluate AGENTS.md quality** — does each file help the agent decide load-or-skip (projection), or just describe contents (no projection)?
- **Diagnose agent performance** — if an agent uses too many tokens on a task, trace the convergence path and find where narrowing failed

The math must *clarify*, not obfuscate. If "projection onto a subspace" doesn't help someone design a better directory structure, use "selective loading based on directory AGENTS.md" instead. The analogy exists to provide rigorous backing for practical decisions, not to replace them.

## Sources

- Original articulation — synthesized from operational experience with a production aDNA vault (126+ agent sessions, 6 campaigns, 40+ missions). The convergence pattern was observed empirically before being formalized mathematically.
- [Effective Context Engineering for AI Agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) — Anthropic (2025). "Find the smallest set of high-signal tokens that maximize the likelihood of some desired outcome." The convergence model is the ontological expression of this principle.
- [aDNA Universal Standard v2.1](https://github.com/lat-labs/lattice-adna) — §8.7 (75% Rule as norm bound), §10 (Context Library as topic-based subspace decomposition), §3.1 (question test as classification primitive).

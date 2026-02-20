---
type: directory_index
created: 2026-02-19
updated: 2026-02-20
last_edited_by: agent_stanley
tags: [directory_index, lattice, examples]
---

# what/lattices/examples/ — Reference Lattice Implementations

## Purpose

Example `.lattice.yaml` files demonstrating different lattice types, execution modes, and composition patterns. Use as starting templates when creating new lattices.

## Examples

### General-Purpose Examples

| File | Lattice Type | Execution Mode | Demonstrates |
|------|-------------|---------------|-------------|
| `hello_world.lattice.yaml` | pipeline | workflow | Minimal valid lattice — simplest pipeline for onboarding |
| `sales_pipeline.lattice.yaml` | pipeline | workflow | B2B sales funnel — lead capture through close. Business use case |
| `product_launch.lattice.yaml` | pipeline | hybrid | Cross-functional launch — market research (LLM) through go-to-market |
| `learning_path.lattice.yaml` | workflow | workflow | Personal learning cycle with iterative assessment loop |
| `creative_brief.lattice.yaml` | pipeline | hybrid | Client project workflow — brief through revision cycle with LLM feedback |
| `deep_research.lattice.yaml` | pipeline | hybrid | Multi-agent research pipeline with validation loops and phase gates |
| `knowledge_base.lattice.yaml` | context_graph | reasoning | Knowledge retrieval + LLM reasoning — only `context_graph` type example |
| `research_orchestrator.lattice.yaml` | agent | hybrid | Orchestrator pattern — LLM-driven coordination with human checkpoints |

### Biotech / Federation Examples

| File | Lattice Type | Execution Mode | Demonstrates |
|------|-------------|---------------|-------------|
| `protein_binder_design.lattice.yaml` | pipeline | workflow | Deterministic computational biology pipeline — linear DAG, federation metadata |
| `docking_assessment.lattice.yaml` | pipeline | workflow | Sub-lattice extracted from protein_binder_design — demonstrates all 5 federation properties |
| `binder_generation.lattice.yaml` | pipeline | workflow | Generative design sub-lattice — interface descriptor + federation extraction |
| `composed_therapeutics.lattice.yaml` | pipeline | workflow | Single external reference composition — uses docking_assessment via `lattice://` URI |
| `full_therapeutics.lattice.yaml` | pipeline | workflow | Multi-lattice composition — composes both binder_generation and docking_assessment |

## How to Use

1. **Pick the closest example** to your target lattice type and execution mode
2. **Copy** the file with a new name: `your_lattice_name.lattice.yaml`
3. **Modify** nodes, edges, metadata, and FAIR block to match your design
4. **Validate** with `tools/lattice_validate.py` to check schema compliance

## Load/Skip Decision

**Load this directory when**:
- Creating a new `.lattice.yaml` file and need a structural template
- Learning the lattice YAML format by example
- Comparing execution modes (workflow vs. reasoning vs. hybrid)

**Skip when**:
- Already familiar with the `.lattice.yaml` format and not creating new lattices
- Working on non-lattice tasks (sessions, context, governance)

**Token cost**: ~250 tokens (this AGENTS.md). Individual YAML files are ~500-1,000 tokens each.

## Cross-References

- [what/lattices/AGENTS](../AGENTS.md) — Lattice YAML ecosystem overview
- [what/lattices/tools/AGENTS](../tools/AGENTS.md) — Validation and conversion tools
- `../lattice_yaml_schema.json` — JSON Schema for validation
- `../canvas_yaml_interop.md` — Canvas ↔ YAML bidirectional mapping

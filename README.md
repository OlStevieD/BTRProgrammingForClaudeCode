# BTR Framework

**Boundaries, Terms, Relationships** — a skill-first framework for turning ambiguous ideas into executable AI-assisted development work.

BTR has two layers:

1. **The Method** — the tool-agnostic thinking model: start with an End Goal, work backward through Boundaries, Terms, and Relationships, identify the Entry Point, then execute forward.
2. **The Framework** — the reusable project structure, skills, templates, review lenses, and optional runtime adapters that apply the method in real projects.

This repository began as **BTR Programming for Claude Code**. It now treats Claude Code agents as one adapter around a more portable BTR core.

**End Goal → BTR Discovery → Entry Point → Readiness Assessment → Execution**

---

## What This Is

A reusable framework for AI-assisted development that:

1. **Starts with BTR Discovery** — clarify scope before building.
2. **Creates durable context** — write a `docs/BTR.md` artifact that survives sessions, models, and tools.
3. **Uses skills as the primary runtime surface** — the method lives in reusable procedures, not one tool's agent format.
4. **Keeps agents as optional adapters** — Claude Code agents and other runtime-specific prompts can still be generated from the same BTR source of truth.
5. **Maintains quality with review lenses** — security, performance, edge cases, maintainability, consistency, tests, documentation, dependencies, and synthesis.

---

## Quick Start

### Skill-first use

Use the BTR skill with any capable AI assistant or agent runtime:

```text
Use the BTR method to scope this project before implementation.
End Goal: <describe what you want to build>
```

Work through discovery until the Entry Point is clear, then create `docs/BTR.md` using `templates/BTR-template.md`.

### Clone as a project template

```bash
git clone https://github.com/OlStevieD/BTRProgrammingForClaudeCode.git my-project
cd my-project

# Remove the template's git history and start fresh
rm -rf .git
git init
```

Then run BTR discovery with your AI tool of choice.

### Claude Code adapter use

Claude Code support still exists, but it is now framed as an adapter:

```bash
mkdir -p .claude/agents
cp adapters/claude-code/agents/*.md .claude/agents/
claude .
```

If generated agents conflict with `docs/BTR.md`, the BTR artifact wins.

---

## The Workflow

```text
End Goal
  │
  ▼
BTR Discovery
  • Define the End Goal
  • Set Boundaries
  • Establish Terms
  • Map Relationships
  • Identify the Entry Point
  │
  ▼
Readiness Assessment
  • Is the Entry Point actionable?
  • Are major terms and dependencies clear?
  • Are open questions answered or intentionally parked?
  │
  ▼
BTR Artifact
  • Create/update docs/BTR.md
  • Treat it as source of truth
  │
  ▼
Execution
  • Build from the Entry Point
  • Stay inside Boundaries
  • Update BTR if scope changes
  │
  ▼
Review
  • Apply BTR review lenses
  • Optionally use runtime-specific agents
```

---

## What's Included

```text
BTRProgrammingForClaudeCode/
├── README.md
├── CLAUDE.md                         # Legacy Claude Code project instructions
├── docs/
│   ├── BTR-Method.md                 # Tool-agnostic BTR thinking model
│   ├── BTR-Framework.md              # Skill-first operational framework
│   ├── BTR-Artifact-Spec.md          # What a complete BTR artifact contains
│   ├── BTR-Glossary.md               # Term definitions
│   └── Agent-Framework.md            # Legacy / adapter-specific agent model
├── skills/
│   ├── btr/
│   │   ├── SKILL.md                  # Core BTR discovery skill
│   │   ├── references/               # Method/framework/spec/glossary copies
│   │   └── templates/
│   │       └── BTR-template.md
│   └── btr-review/
│       ├── SKILL.md                  # BTR-aware review workflow
│       └── references/               # Review lenses copied from agent templates
├── adapters/
│   └── claude-code/
│       ├── README.md
│       └── agents/                   # Claude Code-specific agent adapter
├── templates/
│   ├── BTR-template.md               # Backward-compatible artifact template
│   └── agents/                       # Backward-compatible Claude Code templates
└── audits/                           # Review/agent outputs
```

---

## Method vs Framework

### Method

The **method** is the conceptual procedure.

It answers:

> How does BTR think?

Read: [`docs/BTR-Method.md`](docs/BTR-Method.md)

It covers:

- End Goal
- Entry Point
- Boundaries
- Terms
- Relationships
- unknown-unknowns → known-unknowns → known-knowns
- readiness-gated execution
- failure modes

The method is stable, philosophical, and tool-agnostic.

### Framework

The **framework** is the operational package around the method.

It answers:

> How do we apply BTR in AI-assisted development workflows?

Read: [`docs/BTR-Framework.md`](docs/BTR-Framework.md)

It covers:

- skill-first architecture
- repo layout
- artifact conventions
- review lenses
- runtime adapters
- migration from generated agents
- extension rules

The framework is the usable toolkit layer.

---

## Skills

### `skills/btr/`

The core BTR discovery skill.

Use it to:

- clarify ambiguous goals
- establish Boundaries, Terms, and Relationships
- identify the Entry Point
- decide whether the project is ready for execution
- create or update `docs/BTR.md`

### `skills/btr-review/`

The BTR-aware review skill.

Use it after implementation begins to check work against:

- the BTR artifact
- project boundaries
- defined terms
- dependency relationships
- security, performance, edge-case, maintainability, consistency, test, documentation, dependency, and synthesis lenses

---

## Adapters

Adapters translate the canonical BTR method and skills into runtime-specific surfaces.

Currently included:

- `adapters/claude-code/` — preserves the original Claude Code agent workflow.

Future adapters could include:

- Hermes install/export layout
- Codex prompt packs
- OpenCode prompts
- bootstrap scripts for project-local BTR artifacts

Adapters should not redefine the BTR method. They should implement it for a specific runtime.

---

## After BTR Discovery

Once discovery completes, a project should have:

```text
your-project/
├── docs/
│   └── BTR.md                # Source of truth: scope, stack, terms, relationships, Entry Point
├── src/                      # Structure defined by the BTR artifact
├── tests/                    # Verification strategy defined by scope
├── audits/                   # Optional review outputs
└── .claude/agents/           # Optional, only when using the Claude Code adapter
```

`docs/BTR.md` is the durable context. Generated agents, prompts, and review outputs are secondary.

---

## Using Claude Code Agents

The original agent workflow is still supported.

```bash
mkdir -p .claude/agents
cp adapters/claude-code/agents/*.md .claude/agents/
```

Then in Claude Code:

```text
/agents
/agents security
/agents review
Run all agents on src/
Run security and edge-cases on the changed files
Read audits and implement critical fixes
```

But the governing rule is now:

> Agents are adapter outputs. `docs/BTR.md` is the source of truth.

---

## Why This Exists

AI-generated code often suffers from:

- local solutions without global coherence
- inconsistent patterns across files
- missed edge cases
- security oversights
- premature execution from vague prompts
- context loss when sessions or models change

BTR addresses this by:

- **scoping first** — know what you are building before you build
- **curating context** — Boundaries define what matters, Terms define meaning, Relationships define dependencies
- **writing durable artifacts** — context survives token limits and model switches
- **starting from the Entry Point** — execution begins at the root dependency
- **reviewing against scope** — quality checks stay tied to the agreed artifact

---

## Customization

### Add stack-specific review checks

Edit or extend the review lenses in:

```text
skills/btr-review/references/
```

If you are using Claude Code agents, also update or regenerate:

```text
adapters/claude-code/agents/
```

### Skip discovery when scope is already known

If you already know your scope:

1. Create `docs/BTR.md` manually using `templates/BTR-template.md`.
2. Run a readiness check against `docs/BTR.md`.
3. Begin execution only if the Entry Point is actionable.

### Add another runtime

Create a new adapter directory:

```text
adapters/<runtime>/
```

Keep reusable method/workflow content in `skills/`; keep runtime-specific prompts, agents, scripts, or instructions in the adapter.

---

## License

MIT — use freely, attribution appreciated.

---

## Contributing

Improvements welcome. The framework evolves through use.

When contributing, preserve the split:

- Method changes belong in `docs/BTR-Method.md`.
- Framework/workflow changes belong in `docs/BTR-Framework.md`.
- Reusable AI procedures belong in `skills/`.
- Runtime-specific behavior belongs in `adapters/`.

---

*BTR Framework: Start with End Goal. Work backward to Entry Point. Execute forward.*

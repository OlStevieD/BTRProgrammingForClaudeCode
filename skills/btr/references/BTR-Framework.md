# BTR Framework
*The skill-first operating system for applying the BTR Method*

BTR has two layers:

1. **The Method** — the tool-agnostic thinking model: start with an End Goal, work backward through Boundaries, Terms, and Relationships, identify the Entry Point, then execute forward.
2. **The Framework** — the reusable project structure, skills, templates, review lenses, and optional runtime adapters that apply the method in AI-assisted development.

This document describes the framework layer. For the conceptual model, read [`BTR-Method.md`](BTR-Method.md).

---

## Design Direction

BTR is now **skill-first**.

The core BTR behavior should live in reusable skills and written artifacts, not in runtime-specific agent files. Claude Code agents, Codex prompts, Hermes skills, and future runtimes are adapters around the same BTR method.

**Old center of gravity:**

```text
Claude Code project template → generated agents → BTR behavior inside agent prompts
```

**New center of gravity:**

```text
BTR Method → BTR skills + artifacts → optional runtime adapters
```

Agents are still useful for parallel or specialized review, but they are no longer the source of truth. They are generated or maintained as adapter outputs.

---

## Canonical Project Layout

```text
btr-framework/
├── README.md
├── docs/
│   ├── BTR-Method.md          # The thinking model
│   ├── BTR-Framework.md       # This operational framework
│   ├── BTR-Artifact-Spec.md   # Required shape of docs/BTR.md
│   ├── BTR-Glossary.md        # Shared definitions
│   └── Agent-Framework.md     # Legacy / adapter-specific agent model
├── skills/
│   ├── btr/
│   │   ├── SKILL.md
│   │   ├── references/
│   │   │   ├── BTR-Method.md
│   │   │   ├── BTR-Framework.md
│   │   │   ├── BTR-Artifact-Spec.md
│   │   │   └── BTR-Glossary.md
│   │   └── templates/
│   │       └── BTR-template.md
│   └── btr-review/
│       ├── SKILL.md
│       └── references/
│           ├── security.md
│           ├── performance.md
│           ├── edge-cases.md
│           ├── maintainability.md
│           ├── consistency.md
│           ├── test-scenarios.md
│           ├── documentation.md
│           ├── dependencies.md
│           ├── config.md
│           └── review.md
├── adapters/
│   └── claude-code/
│       ├── README.md
│       └── agents/
│           └── *.md
├── templates/
│   ├── BTR-template.md        # Backward-compatible root template
│   └── agents/                # Backward-compatible Claude Code templates
└── audits/
```

The root `templates/agents/` directory remains for backward compatibility. New integrations should prefer `skills/` as the canonical surface and `adapters/` for runtime-specific outputs.

---

## Core Artifacts

### `docs/BTR.md`

Every BTR-scoped project should eventually produce a project-local `docs/BTR.md`. This is the durable context artifact that survives sessions, model changes, and runtime changes.

It records:

- End Goal
- Entry Point
- Tech stack, if applicable
- Boundaries
- Terms
- Relationships
- Open questions
- Parked items
- Readiness assessment

The required shape is defined in [`BTR-Artifact-Spec.md`](BTR-Artifact-Spec.md).

### `skills/btr/SKILL.md`

The core BTR skill tells an AI assistant when and how to run BTR discovery. It should remain conversational, readiness-gated, and tool-agnostic.

It owns:

- trigger conditions
- discovery cadence
- pillar prompts
- artifact creation rules
- readiness assessment
- failure modes

### `skills/btr-review/SKILL.md`

The review skill applies BTR-aware review lenses after an artifact exists and execution has begun.

It owns:

- reading the BTR artifact first
- reviewing against Boundaries, Terms, and Relationships
- applying security/performance/edge-case/maintainability/etc. lenses
- writing or summarizing findings
- prioritizing blockers before polish

### `adapters/`

Adapters translate the canonical BTR method and skills into runtime-specific surfaces.

Examples:

- Claude Code `.claude/agents/`
- Hermes local skills
- Codex prompt packs
- project bootstrap scripts

Adapters are allowed to be opinionated about their runtime, but they should not redefine the BTR method.

---

## Skill-First Workflow

```text
End Goal
  ↓
BTR discovery skill
  ↓
Boundaries / Terms / Relationships clarified
  ↓
Entry Point identified
  ↓
docs/BTR.md created or updated
  ↓
Execution begins from Entry Point
  ↓
BTR review skill applies review lenses
  ↓
Optional adapters run specialized agents/prompts
```

Important rule:

> Do not treat generated agents as the durable context. The durable context is the written BTR artifact plus the canonical skills/references.

---

## Relationship Between Skills and Agents

Skills and agents are different layers.

**Skills:**

- reusable procedures
- loaded when a task matches a trigger
- stable across projects and runtimes
- good for methodology, workflows, checklists, and conventions

**Agents:**

- runtime-specific workers or reviewer personas
- useful for parallel specialized review
- often project-local and generated
- good for delegation when a tool supports them

BTR should use skills for the method and framework. Agents should be optional adapter outputs when the runtime benefits from them.

---

## Review Lenses

The original Claude Code agent templates become review lenses in the skill-first model:

- `config` — stack, project constraints, environment assumptions
- `security` — auth, secrets, injection, access control, unsafe defaults
- `performance` — latency, scaling, resource use, hot paths
- `edge-cases` — error states, weird inputs, boundary conditions
- `maintainability` — code organization, readability, future change cost
- `consistency` — naming, patterns, architecture coherence
- `test-scenarios` — coverage gaps and verification paths
- `documentation` — docs, comments, onboarding clarity
- `dependencies` — package choices, version risks, supply-chain concerns
- `review` — synthesis and prioritization

A runtime may implement each lens as an agent, a prompt, a checklist, or a section inside a single review pass.

---

## Migration Guidance

For the current Claude Code template:

1. Preserve existing `templates/agents/` so current users are not broken.
2. Copy those templates into `adapters/claude-code/agents/` to make their adapter role explicit.
3. Copy those templates into `skills/btr-review/references/` as reusable review lenses.
4. Add `skills/btr/` as the canonical discovery skill.
5. Split the old conceptual `BTR-Framework.md` into:
   - `BTR-Method.md` for tool-agnostic thinking
   - `BTR-Framework.md` for skill-first operational structure
6. Update README language from “Claude Code template” to “skill-first BTR framework with a Claude Code adapter.”

---

## Extension Rules

When adding a new runtime or workflow:

1. Do not fork the method unless the method itself changes.
2. Put runtime-specific files under `adapters/<runtime>/`.
3. Keep reusable procedures under `skills/`.
4. Keep durable project context in `docs/BTR.md`.
5. If a new reviewer category is broadly useful, add it as a review lens before generating runtime-specific agents from it.
6. If a workflow depends on a specific runtime feature, document that dependency in the adapter, not in the core method.

---

## Readiness Standard

A project is ready for execution when:

- the End Goal is written down
- the Entry Point is named and actionable
- in-scope and out-of-scope boundaries are clear enough to prevent immediate scope creep
- critical terms have shared definitions
- major relationships/dependencies are mapped
- unresolved questions are either answered or parked intentionally
- the next action can be taken without inventing missing context

If those are not true, continue BTR discovery before building.

---

*BTR Framework by Stephen Danals — skill-first architecture draft.*

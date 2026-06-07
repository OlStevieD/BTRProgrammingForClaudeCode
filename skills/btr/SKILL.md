---
name: btr
description: Use when a user needs to scope an idea, project, feature, component, or task before execution by clarifying Boundaries, Terms, Relationships, End Goal, Entry Point, and readiness.
version: 1.0.0
author: Stephen Danals
license: MIT
metadata:
  hermes:
    tags: [btr, scoping, planning, context, methodology, ai-development]
    related_skills: [btr-review]
---

# BTR

## Overview

BTR means **Boundaries, Terms, Relationships**. It is a method for moving from ambiguity to executable clarity.

Use BTR to turn an unclear goal into durable context: a written artifact that humans and AI systems can read, transfer, resume, and execute from.

The core arc is:

```text
End Goal → BTR Discovery → Entry Point → Readiness Assessment → Execution
```

BTR is not tied to one runtime. It can be used with Hermes, Claude Code, Codex, other agent systems, or a human planning session.

## When to Use

Use this skill when:

- The user has a vague or broad idea and needs help narrowing it.
- The user is starting a new programming project.
- The user wants to scope a feature before implementation.
- The user asks for BTR by name.
- The user asks “where do we start?” or “what should we build first?”
- The task has enough ambiguity that immediate execution would require guessing.
- A project needs durable context before handoff to another AI, agent, or session.

Do not use BTR for trivial one-step tasks where the End Goal, boundary, and first action are already obvious.

## Operating Mode

Run BTR as a conversation, not a decision dump.

1. Ask for or restate the **End Goal**.
2. Ask one focused question at a time.
3. After each answer, summarize what changed in:
   - Boundaries
   - Terms
   - Relationships
   - Entry Point status
4. Surface the next dependency gently.
5. Do not create a final BTR artifact until the scope is sufficiently agreed.
6. Do not begin implementation until readiness passes.

## Discovery Questions

### Boundaries

- What is the smallest useful version?
- What is explicitly out of scope?
- What constraints matter: time, budget, platform, users, tools, data, risk?
- What would be tempting but premature?

### Terms

- Which words could mean different things to different people?
- Are there domain-specific or invented terms?
- What assumptions are hidden inside common words?
- What does “done” mean for this scope?

### Relationships

- What depends on what?
- Who are the users or actors?
- What systems, files, services, or people interact?
- What must exist before another thing can work?
- What is the root dependency?

### Entry Point

- What can be started without unresolved dependencies?
- What unlocks downstream work?
- What is the first domino?
- Can the next action be taken without inventing missing context?

## Written Artifact

When discovery is ready, create or update `docs/BTR.md` using the template in `templates/BTR-template.md` and the artifact requirements in `references/BTR-Artifact-Spec.md`.

The artifact should include:

- End Goal
- Entry Point
- Tech stack, if relevant
- Glossary of Terms
- Mapped Relationships
- Boundaries
- Parked Items
- Open Questions
- Readiness Assessment

The artifact is the durable context. It should outlive the conversation.

## Readiness Assessment

Execution can begin only when:

- End Goal is written down.
- Entry Point is named and actionable.
- In-scope and out-of-scope boundaries are clear enough to prevent immediate scope creep.
- Critical terms have shared definitions.
- Major relationships/dependencies are mapped.
- Open questions are either answered or intentionally parked.
- The next action does not require guessing.

If readiness fails, keep discovering.

## Handoff to Execution

Once ready:

1. Treat `docs/BTR.md` as source of truth.
2. Begin at the Entry Point.
3. Keep changes inside the established Boundaries.
4. Update the BTR artifact when scope changes.
5. Use the `btr-review` skill or equivalent review lenses before considering work complete.

## References

- `references/BTR-Method.md` — the tool-agnostic thinking model.
- `references/BTR-Framework.md` — the skill-first project/workflow system.
- `references/BTR-Artifact-Spec.md` — minimum required artifact shape.
- `references/BTR-Glossary.md` — definitions for BTR terms.
- `templates/BTR-template.md` — artifact template.

## Common Pitfalls

1. **Premature execution** — building before the Entry Point is clear.
2. **Decision dumping** — front-loading a whole architecture instead of discovering one dependency at a time.
3. **Undefined terms** — using words that sound obvious but hide disagreement.
4. **Scope drift** — treating parked items as current requirements.
5. **Artifact neglect** — relying on chat memory instead of writing durable context.
6. **Agent-first thinking** — treating generated agents as the source of truth instead of BTR artifacts and skills.

## Verification Checklist

- [ ] End Goal is captured.
- [ ] Boundaries are separated into in-scope, out-of-scope, and constraints.
- [ ] Important Terms are defined.
- [ ] Relationships/dependencies are mapped.
- [ ] Entry Point is explicit.
- [ ] Open questions are answered or parked.
- [ ] `docs/BTR.md` exists or there is a deliberate reason it has not been created yet.
- [ ] Execution has not started before readiness.

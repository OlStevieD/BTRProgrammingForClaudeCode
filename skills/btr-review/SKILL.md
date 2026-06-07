---
name: btr-review
description: Use when reviewing implementation work against an existing BTR artifact using security, performance, edge-case, maintainability, consistency, test, documentation, dependency, and synthesis lenses.
version: 1.0.0
author: Stephen Danals
license: MIT
metadata:
  hermes:
    tags: [btr, review, code-review, quality, ai-development]
    related_skills: [btr]
---

# BTR Review

## Overview

BTR Review applies quality lenses after BTR discovery has produced durable context. It keeps implementation aligned with the End Goal, Boundaries, Terms, Relationships, and Entry Point recorded in `docs/BTR.md`.

The original Claude Code agent templates are preserved here as review lenses. A runtime may apply them as agents, prompts, checklists, or sections inside one review pass.

## When to Use

Use this skill when:

- `docs/BTR.md` exists and implementation has begun.
- A feature, component, or PR needs review against agreed scope.
- You need to check whether changes respect the BTR artifact.
- You want specialized review lenses without making agents the source of truth.
- You are preparing handoff to a human or another AI system.

Do not use this as a substitute for BTR discovery. If there is no agreed End Goal, Entry Point, or scope, use the `btr` skill first.

## Review Workflow

1. Read `docs/BTR.md` first.
2. Identify the implementation scope being reviewed.
3. Check alignment with:
   - End Goal
   - Entry Point
   - Boundaries
   - Terms
   - Relationships
   - parked items and open questions
4. Apply the relevant review lenses from `references/`.
5. Prioritize findings:
   - Critical: violates scope, security, correctness, or readiness.
   - Major: likely to cause defects, maintenance pain, or user-visible issues.
   - Minor: polish, documentation, naming, consistency.
6. Recommend concrete fixes or next BTR questions.
7. If the work changes scope, update or reopen the BTR artifact instead of silently expanding implementation.

## Review Lenses

- `references/config.md` — stack, configuration, environment assumptions.
- `references/security.md` — auth, secrets, injection, unsafe defaults, access control.
- `references/performance.md` — hot paths, latency, resource use, scaling concerns.
- `references/edge-cases.md` — bad inputs, failure states, weird paths, boundary conditions.
- `references/maintainability.md` — organization, readability, future change cost.
- `references/consistency.md` — naming, patterns, architectural coherence.
- `references/test-scenarios.md` — coverage gaps and verification paths.
- `references/documentation.md` — docs, comments, onboarding clarity.
- `references/dependencies.md` — package choices, version risk, supply-chain concerns.
- `references/review.md` — synthesis and prioritization.

## Output Format

Prefer concise structured findings:

```text
BTR alignment: pass / partial / fail
Scope reviewed: <files, feature, or PR>

Critical:
- ...

Major:
- ...

Minor:
- ...

BTR artifact updates needed:
- ...

Recommended next action:
- ...
```

If there are no material findings, say what was checked and why it passes.

## Common Pitfalls

1. **Reviewing without BTR context** — always read the artifact first.
2. **Treating lenses as separate truths** — the artifact remains source of truth.
3. **Over-reviewing tiny changes** — apply only relevant lenses when scope is small.
4. **Ignoring scope changes** — if implementation expands the project, reopen BTR discovery.
5. **Only listing problems** — include concrete fixes or next questions.

## Verification Checklist

- [ ] `docs/BTR.md` was read or its absence was explicitly called out.
- [ ] Findings are tied to BTR scope, terms, or relationships where possible.
- [ ] Relevant lenses were applied.
- [ ] Critical issues are separated from polish.
- [ ] Scope changes are routed back to BTR discovery.
- [ ] The next action is clear.

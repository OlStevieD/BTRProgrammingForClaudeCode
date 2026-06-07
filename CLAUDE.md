# CLAUDE.md

This project uses the **BTR Framework** (Boundaries, Terms, Relationships) for scoping and development.

BTR is now **skill-first**:

- `docs/BTR.md` is the project source of truth once discovery completes.
- `skills/btr/` is the canonical discovery workflow.
- `skills/btr-review/` is the canonical review workflow.
- `.claude/agents/` are optional Claude Code adapter outputs, not the source of truth.

---

## Project Status

**Phase:** Discovery

**BTR Artifact:** `docs/BTR.md` (created during discovery)

**Skills:** `skills/btr/`, `skills/btr-review/`

**Optional Claude Code Adapter:** `.claude/agents/` (generated or copied only when useful)

---

## First Run Instructions

Welcome! This project template uses BTR to scope before building.

### If `docs/BTR.md` does NOT exist → Start BTR Discovery

You are now a BTR discovery partner. Help narrow scope from a vague goal to actionable work.

Run the conversation using the BTR skill behavior in `skills/btr/SKILL.md`.

**The Arc:**

```text
End Goal → BTR Discovery → Entry Point → Readiness Assessment → Execution
```

**Begin by asking:**

> What do you want to build? Describe your End Goal.

**Then ask focused questions, preferably one at a time, to establish:**

**Boundaries:**

- What's the smallest useful version?
- What's definitely NOT included?
- What are the constraints: time, resources, must-haves, platforms, risk?

**Terms:**

- Are there domain-specific words that need defining?
- Any concepts that could mean different things?
- What does “done” mean for this scope?

**Tech Stack, if this is a programming project:**

- What language(s)?
- What framework(s)?
- What libraries or services?
- Where will it be deployed?
- What's the testing approach?

**Relationships:**

- What depends on what?
- What external services are involved?
- What's the data flow?
- Who are the users or actors?

**Entry Point:**

- Trace dependencies backward — what's the root?
- What must exist before anything else?
- What's the literal first thing to build?

**Summarize after each exchange:**

- Boundaries set
- Terms defined
- Tech stack decisions, if relevant
- Relationships mapped
- Entry Point status
- Items parked

**Discovery ends when:**

- Entry Point is identified and actionable
- Tech stack is decided, if relevant
- Readiness Assessment passes
- Open questions are answered or intentionally parked

**Then do these steps:**

1. Create `docs/BTR.md` using `templates/BTR-template.md` and the requirements in `docs/BTR-Artifact-Spec.md`.

   The artifact must contain:

   - End Goal
   - Entry Point and why it is the Entry Point
   - Tech Stack, if relevant
   - Glossary of Terms
   - Mapped Relationships
   - Boundaries: in scope, out of scope, constraints
   - Parked Items
   - Open Questions
   - Readiness Assessment

2. Update this `CLAUDE.md`:

   - Change Phase to `Ready`
   - Add project-specific notes below
   - Record whether the Claude Code adapter is being used

3. Optional: set up Claude Code agents only if this project will use Claude Code's `/agents` workflow.

   Preferred adapter source:

   ```bash
   mkdir -p .claude/agents
   cp adapters/claude-code/agents/*.md .claude/agents/
   ```

   If agents are customized, keep them aligned with `docs/BTR.md`.

4. Announce ready for execution from Entry Point.

---

### If `docs/BTR.md` EXISTS → Execution Mode

**Read `docs/BTR.md` before doing any implementation work.**

Build from Entry Point toward End Goal.

**Primary workflow:**

1. Read `docs/BTR.md` for source-of-truth context.
2. Work on the current task toward the End Goal.
3. Stay inside the established Boundaries.
4. Use the BTR review workflow in `skills/btr-review/SKILL.md` on new or changed work.
5. Address Critical findings before continuing.
6. Save review outputs to `audits/` when useful.

**Optional Claude Code commands, if `.claude/agents/` exists:**

- `/agents` — list all agents
- `/agents [name]` — run a specific agent
- `Run all agents on [path]` — full audit

**If scope changes:**

1. Stop expanding implementation.
2. Update `docs/BTR.md` or reopen BTR discovery.
3. Regenerate or update affected adapter outputs, including Claude Code agents if used.

Rule:

> If an agent, prompt, or local instruction conflicts with `docs/BTR.md`, the BTR artifact wins.

---

## Project-Specific Notes

*(Added after BTR Discovery completes)*

---

## File Structure

```text
project/
├── CLAUDE.md                       (this file)
├── docs/
│   ├── BTR.md                      (project BTR artifact - created in discovery)
│   ├── BTR-Method.md               (tool-agnostic thinking model)
│   ├── BTR-Framework.md            (skill-first operational framework)
│   ├── BTR-Artifact-Spec.md        (artifact requirements)
│   └── BTR-Glossary.md             (shared terms)
├── skills/
│   ├── btr/                        (canonical discovery skill)
│   └── btr-review/                 (canonical review skill)
├── adapters/
│   └── claude-code/                (optional Claude Code adapter)
├── templates/
│   └── agents/                     (backward-compatible agent templates)
├── .claude/
│   └── agents/                     (optional project-local Claude agents)
├── audits/                         (review/agent outputs)
└── src/                            (your code)
```

---

## Quick Reference

| Situation | Action |
|-----------|--------|
| First time, no BTR.md | Start BTR Discovery using `skills/btr/SKILL.md` |
| BTR.md exists | Execution mode, build from Entry Point |
| Need review | Use `skills/btr-review/SKILL.md` |
| Using Claude Code agents | Copy from `adapters/claude-code/agents/` |
| Scope changed | Update BTR.md first, then update adapters |
| Stuck on where to start | Check Entry Point in BTR.md |

---

*BTR Framework: Start with End Goal. Work backward to Entry Point. Execute forward.*

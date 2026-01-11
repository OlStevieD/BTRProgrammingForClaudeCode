# CLAUDE.md

This project uses the **BTR Framework** (Boundaries, Terms, Relationships) for scoping and development.

---

## Project Status

**Phase:** Discovery

**BTR Artifact:** `docs/BTR.md` (created during discovery)

**Agents:** `.claude/agents/` (generated after BTR complete)

---

## First Run Instructions

Welcome! This project template uses BTR to scope before building.

### If `docs/BTR.md` does NOT exist → Start BTR Discovery

You are now a BTR discovery partner. Help narrow scope from a vague goal to actionable work.

**The Arc:**
```
End Goal → (BTR Discovery) → Entry Point → (Readiness Assessment) → Execution
```

**Begin by asking:**
1. "What do you want to build? Describe your End Goal."

**Then ask questions (1-2 at a time) to establish:**

**Boundaries:**
- What's the smallest useful version?
- What's definitely NOT included?
- What are the constraints (time, resources, must-haves)?

**Terms:**
- Are there domain-specific words that need defining?
- Any concepts that could mean different things?

**Tech Stack:**
- What language(s)?
- What framework(s)?
- What libraries or services?
- Where will it be deployed?
- What's the testing approach?

**Relationships:**
- What depends on what?
- What external services are involved?
- What's the data flow?

**Entry Point:**
- Trace dependencies backward - what's the root?
- What must exist before anything else?
- What's the literal first thing to build?

**Summarize after each exchange:**
- Boundaries set
- Terms defined
- Tech stack decisions
- Relationships mapped
- Entry Point status
- Items parked

**Discovery ends when:**
- Entry Point is identified and actionable
- Tech stack is decided
- Readiness Assessment passes (confidence to proceed)

**Then do these steps:**

1. Create `docs/BTR.md` with the complete artifact containing:
   - End Goal
   - Entry Point (and why)
   - Tech Stack (languages, frameworks, libraries, infrastructure)
   - Glossary of Terms
   - Mapped Relationships
   - Boundaries (in scope, out of scope, constraints)
   - Parked Items
   - Readiness Assessment

2. Generate agents in `.claude/agents/` with YAML frontmatter:
   ```yaml
   ---
   name: [Agent Name]
   description: [One-line description]
   ---
   ```
   
   Create these agents customized to the tech stack:
   - `config.md` - Project config from BTR decisions
   - `security.md` - With stack-specific vulnerability checks
   - `performance.md` - With stack-specific efficiency patterns
   - `edge-cases.md` - With stack-specific gotchas
   - `maintainability.md` - Coupling, clarity, surface area
   - `consistency.md` - With established patterns pre-filled
   - `test-scenarios.md` - With testing framework awareness
   - `documentation.md` - Docs and comments
   - `dependencies.md` - Package audits
   - `review.md` - Synthesizes all findings

3. Update this CLAUDE.md:
   - Change Phase to "Ready"
   - Add project-specific notes below

4. Announce ready for execution from Entry Point

---

### If `docs/BTR.md` EXISTS → Execution Mode

**Read `docs/BTR.md` for project context.**

Build from Entry Point toward End Goal.

**Available commands:**
- `/agents` - List all agents
- `/agents [name]` - Run specific agent
- `Run all agents on [path]` - Full audit

**Workflow:**
1. Work on current task toward End Goal
2. Run relevant agents on new/changed code
3. Address Critical findings before continuing
4. Audits saved to `audits/` folder

**If scope changes:** Update `docs/BTR.md` and regenerate affected agents.

---

## Project-Specific Notes

*(Added after BTR Discovery completes)*

---

## File Structure

```
project/
├── CLAUDE.md              (this file)
├── docs/
│   ├── BTR.md             (your BTR artifact - created in discovery)
│   ├── BTR-Framework.md   (methodology reference)
│   └── ...
├── templates/
│   └── agents/            (agent templates - reference)
├── .claude/
│   └── agents/            (YOUR agents - generated from BTR)
├── audits/                (agent outputs)
└── src/                   (your code)
```

---

## Quick Reference

| Situation | Action |
|-----------|--------|
| First time, no BTR.md | BTR Discovery starts automatically |
| BTR.md exists | Execution mode, build from Entry Point |
| Need to run agents | `/agents` or `/agents [name]` |
| Scope changed | Update BTR.md, regenerate agents |
| Stuck on where to start | Check Entry Point in BTR.md |

---

*BTR Framework: Start with End Goal. Work backward to Entry Point. Execute forward.*

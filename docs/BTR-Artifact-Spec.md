# BTR Artifact Specification

The minimum requirements for a complete BTR artifact.

---

## What is a BTR Artifact?

A BTR Artifact is the written document produced by BTR discovery. It captures everything established during the discovery process in a format readable by both humans and AI.

**The artifact IS the product.** Without it:
- Context doesn't persist beyond the session
- Context can't transfer between AI models
- Context can't be shared with others
- You're relying on memory, which resets

---

## Minimum Required Sections

A complete BTR Artifact must contain all of the following:

### 1. End Goal
**What you're trying to achieve.**

Format: User story or outcome statement.

```
As a [user type], I want to [action] so that [outcome].
```
or
```
The end state is: [description of what exists when done].
```

**Why required:** Everything works backward from this. Without a clear End Goal, there's no anchor for discovery.

---

### 2. Entry Point
**Where execution begins.**

The root dependency—the thing that must exist before anything else can. The first actionable step.

```
Entry Point: [What it is]
Why: [Why this is the foundation—what it unlocks]
```

**Why required:** Without an Entry Point, you have a goal but no place to start building. Discovery isn't complete until you can name this.

---

### 3. Glossary of Terms
**All terms defined with shared meaning.**

| Term | Definition |
|------|------------|
| [Term] | [What it means in this context] |

Include:
- Domain-specific terms
- Terms you invented for this project
- Common words used in specific ways
- Any word that could be misunderstood

**Why required:** Ambiguous terms cause misalignment. If the human and AI don't share meaning, outputs will be wrong.

---

### 4. Mapped Relationships
**Dependencies documented.**

What must exist before something else can work. The sequence of dependencies from Entry Point to End Goal.

```
[Entry Point]
    → enables [Step 1]
        → enables [Step 2]
            → enables [End Goal]
```

Include:
- System dependencies (what talks to what)
- Logical dependencies (what must be decided before what)
- User/role relationships (who does what)
- Sequence (what order things happen)

**Why required:** Relationships are the structure. Without them, you have isolated pieces but no understanding of how they connect or what order to build them.

---

### 5. Boundaries
**What's in scope, what's out, and constraints.**

#### In Scope
- [What's included in this effort]

#### Out of Scope
- [What's explicitly excluded—for now or forever]

#### Constraints
- [Limits, rules, non-negotiables]
- [Technical constraints]
- [Time/resource constraints]

**Why required:** Boundaries prevent scope creep and set expectations. They define the edges of the problem space.

---

### 6. Parked Items
**Known-unknowns deferred for later.**

Questions or decisions acknowledged but not resolved in this pass. Not ignored—captured for future work.

| Item | Why Parked | Revisit When |
|------|------------|--------------|
| [Question/decision] | [Reason for deferring] | [Trigger for revisiting] |

**Why required:** BTR won't resolve everything. Parked items ensure nothing is forgotten—they're tracked, not lost.

---

### 7. Readiness Assessment
**Confidence check before execution.**

This is the "90% clamp"—a deliberate checkpoint that asks: *Given what we know, do we believe we have enough to execute?*

```
Readiness: [Ready / Not Ready / Ready with Caveats]

Confidence: [High / Medium / Low]

Rationale: [Why we believe we can proceed—or what's blocking us]

Known Risks: [What could still go wrong]
```

**Assessment criteria:**
- Entry Point is clear and actionable
- All critical terms are defined
- Key relationships are mapped
- Boundaries are set
- Remaining unknowns are parked, not blocking

**Why required:** This prevents premature execution. It forces a conscious decision: "Are we ready?" It's not a guarantee—it's a checkpoint.

---

## For Programming Projects: Tech Stack Section

When using BTR for programming projects, add:

### 8. Tech Stack
**Technologies chosen for this project.**

```
Languages: [e.g., TypeScript]
Framework: [e.g., Next.js 14]
UI: [e.g., React, Tailwind]
Backend: [e.g., Firebase]
Testing: [e.g., Vitest]
Infrastructure: [e.g., Vercel]
Key Libraries: [e.g., Zod, React Query]
```

**Why required for programming:** Agents are customized based on tech stack. Security, performance, and edge case checks are stack-specific.

---

## Completeness Check

Before marking a BTR Artifact complete, verify:

- [ ] End Goal is stated clearly
- [ ] Entry Point is identified and actionable
- [ ] All ambiguous terms are in the Glossary
- [ ] Key relationships are mapped
- [ ] Boundaries define in/out of scope
- [ ] Unresolved items are parked (not forgotten)
- [ ] Readiness Assessment is completed
- [ ] Tech Stack defined (for programming projects)
- [ ] Document is readable by both human and AI

If any box is unchecked, discovery isn't complete.

---

*Part of: BTR Framework*

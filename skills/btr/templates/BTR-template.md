# BTR Artifact Template

Use this template when creating your BTR artifact at `docs/BTR.md`.

---

```markdown
# BTR Artifact: [Project Name]

*Created: [Date]*
*Status: Discovery | Ready | Execution*

---

## End Goal

[User story or outcome statement]

As a [user type], I want to [action] so that [outcome].

**Success looks like:** [Concrete description of done]

---

## Entry Point

**[The foundation - where execution begins]**

Why: [Why this is the root dependency - what it unlocks]

**First action:** [The literal first thing to build/do]

---

## Tech Stack

### Languages
- [e.g., TypeScript]

### Framework
- [e.g., Next.js 14 (App Router)]

### UI
- [e.g., React, Tailwind CSS]

### Backend/Data
- [e.g., Firebase - Auth, Firestore, Functions]

### Testing
- [e.g., Vitest, Playwright]

### Infrastructure
- [e.g., Vercel, GitHub Actions]

### Key Libraries
- [e.g., React Query, Zod, date-fns]

---

## Glossary of Terms

| Term | Definition |
|------|------------|
| [Term] | [What it means in this project] |
| [Term] | [What it means in this project] |

---

## Mapped Relationships

```
[Entry Point]
    → enables [Step 1]
        → enables [Step 2]
            → enables [End Goal]
```

### Dependencies
- [Thing A] depends on [Thing B]
- [Thing C] requires [Thing A] and [Thing D]

### System Integrations
- [External Service] ↔ [How it connects]

### User Flows
- [User type] → [Action sequence]

---

## Boundaries

### In Scope
- [What's included in this effort]
- [Feature or capability]

### Out of Scope
- [What's explicitly excluded]
- [What might be assumed but isn't happening]

### Constraints
- [Technical constraints]
- [Time/resource constraints]
- [Business rules]
- [Non-negotiables]

---

## Project Structure

```
project/
├── [folder]/
│   └── [what goes here]
├── [folder]/
│   └── [what goes here]
└── ...
```

### Patterns to Establish
- **File naming:** [convention]
- **Component structure:** [pattern]
- **Error handling:** [approach]
- **State management:** [approach]
- **API patterns:** [approach]

---

## Parked Items

| Item | Why Parked | Revisit When |
|------|------------|--------------|
| [Question/decision] | [Reason for deferring] | [Trigger] |

---

## Readiness Assessment

**Readiness:** [Ready / Not Ready / Ready with Caveats]

**Confidence:** [High / Medium / Low]

**Rationale:** [Why we believe we can proceed - or what's blocking]

**Known Risks:**
- [What could still go wrong]
- [Assumptions being made]

---

## Agent Focus Areas

Priority areas for code review agents:

1. [e.g., Authentication flow - security critical]
2. [e.g., Database queries - performance sensitive]
3. [e.g., API integrations - error handling important]

---

## Next Steps

After Readiness passes:

1. [ ] Generate agents from this artifact
2. [ ] Create project structure
3. [ ] Build Entry Point: [specific first task]
4. [ ] [Next milestone]

---

*BTR Framework: Boundaries, Terms, Relationships*
```

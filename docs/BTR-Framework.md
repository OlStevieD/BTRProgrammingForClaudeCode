# BTR Framework
*Boundaries, Terms, Relationships*

A methodology for scoping AI interactions and moving from ambiguity to clarity.

---

## The Core Problem

**People struggle with AI because of unknown-unknowns.**

- "Build me a fitness tracking app" → Scope could be billions of tokens. Where do you even start?
- "Help me choose a platform to build a fitness tracking app on" → Now we're somewhere workable.

The difference isn't just specificity—it's *knowability*. The second prompt has definable boundaries, clear terms, and understood relationships.

**BTR is also about controlling context.**

Without BTR, you dump everything into the AI. Noise. The AI doesn't know what's relevant—neither do you.

With BTR:
- **Boundaries** define what context matters
- **Terms** ensure context is understood the same way
- **Relationships** define how context connects

You're curating context. Signal, not noise. Only what's needed for the goal.

**BTR creates portable, permanent context.**

When you hit the token limit or switch AI models, normally you lose everything. The AI has amnesia. But documented BTR:
- Survives sessions and token limits
- Transfers between different AI models
- Lets you pick up where you left off
- Can be shared with other people or teams

BTR = Context that outlives the conversation.

---

## Core Requirement: Written Artifacts

**BTR relies on writing files that both human and AI can understand.**

This isn't optional. Without written documentation:
- Context can't persist beyond a session
- Context can't transfer between AI models
- Context can't be shared with others
- You're relying on memory (yours or the AI's), which resets

The format doesn't matter—markdown, plain text, whatever. What matters:
1. It's written down
2. A human can read and understand it
3. An AI can read and understand it

The BTR artifact *is* the product of discovery. It's what survives.

---

## The End Goal: Start with What You Want

**Everyone knows what they want.** Even if it's rough. Even if it's wrong.

Start with:
- A user story: *"As a [user], I want to [action] so that [outcome]"*
- Or just an end goal: *"I want X to exist"*

This is your anchor. Discovery works backward from here.

---

## The Entry Point: Where You End Up

**The Entry Point is where execution begins.**

When you work backward from your End Goal through BTR discovery, you're tracing the relationship chain—finding what depends on what. Eventually, that chain terminates. You hit something that doesn't depend on anything else within your scope.

That's the Entry Point. The foundation. The root dependency. It's not where you start discovery—it's where you end up after narrowing.

```
End Goal          ← Start discovery here
    ↑ depends on
Intermediate Step
    ↑ depends on
Intermediate Step
    ↑ depends on
Entry Point       ← End up here, start building here
```

**Entry Point characteristics:**
- Has no unresolved dependencies within scope
- Is actionable—you can start work on it immediately
- Unlocks downstream work once complete
- Is the first domino in the sequence

**Without a defined Entry Point:**
- You have a goal and scattered pieces, but nowhere to start
- Execution stalls because everything seems to depend on something else
- Paralysis by "where do I even begin?"

**BTR discovery is complete when you can name your Entry Point.**

---

## The Knowledge Hierarchy

```
Unknown-Unknowns  →  Known-Unknowns  →  Known-Knowns
     (Chaos)            (Questions)        (Answers)
```

**BTR is the mechanism for moving left to right.**

Working backward from your goal forces BTR questions to surface:
- What boundaries need to exist for this goal to be achievable?
- What terms am I using that need definition?
- What relationships must exist between things?

Each question answered narrows the gap.

---

## The Three Pillars

### Boundaries
*Where scope stops regarding an action or branched idea.*

Boundaries shrink the problem space. They turn infinite possibility into finite territory.

### Terms
*A word or phrase used to describe a thing or express a concept—can be domain-specific, made up by the user in context (e.g., "BTR"), or general lexicon. The key: shared meaning understood by both AI and human in context.*

Terms eliminate ambiguity. They surface assumptions and force clarity on what words actually mean in this context.

### Relationships
*Dependencies. What must exist for something else to work. Sequence and pattern.*

Everything executes linearly—you can't do X without Y. But human minds are scattered; we don't naturally see the sequence. Relationships force linearization. They're first-principles thinking: breaking down what depends on what.

---

## The Process

### 1. State Your Goal (Imperfect is Fine)
Write it down. User story format or plain language.
> "I want to build a fitness tracking app that helps people log workouts and see progress."

### 2. Work Backward – Ask BTR Questions
**Boundaries:** What's the smallest version of this? What's definitely NOT included (yet)?
**Terms:** What words am I using that could mean different things? What needs defining?
**Relationships:** What depends on what? Who are the users? What systems talk to each other?

### 3. Each Answer Narrows Scope
Your unknown-unknowns become known-unknowns (questions).
Your known-unknowns become known-knowns (answers).

The gap shrinks.

### 4. Repeat at Each Level
- Broad: "Build fitness tracking app"
- Narrower: "Choose a platform for fitness tracking app"
- Narrower: "Compare Firebase vs Supabase for the app's data model"
- Actionable: "Design Firestore schema for workout logs"

### 5. Document as You Go
Markdown files capture resolved BTR—your growing body of known-knowns. This becomes persistent context for future prompts.

---

## Why People Fail with AI

| Failure Mode | BTR Diagnosis |
|--------------|---------------|
| Prompt too vague | Boundaries undefined |
| AI "hallucinates" or assumes wrong things | Terms not established |
| Output doesn't fit the system | Relationships not communicated |
| Overwhelmed, don't know where to start | Didn't anchor to a goal and work backward |

---

## When BTR Fails

BTR doesn't fail—*execution before readiness* fails.

| Failure Mode | What Happened |
|--------------|---------------|
| **Unclear goal** | User doesn't understand what they actually want. Can't work backward from nothing. |
| **Insufficient time vs. complexity** | Rushed discovery. Didn't iterate enough given problem size. |
| **Premature execution** | Too many unknown-unknowns remained. Pillars misaligned at runtime. |

**Pillar misalignment** is the core failure: if Boundaries, Terms, and Relationships aren't aligned when you execute, you get friction, confusion, scope creep, wrong outputs.

---

## Cascading Complexity

BTR can be applied at any level of granularity:

```
Project Level    →  BTR the whole idea
    ↓
Feature Level    →  BTR a specific feature
    ↓
Component Level  →  BTR a single component
    ↓
Task Level       →  BTR a specific task
```

How deep you go is up to you. More complexity = more BTR passes. The framework scales with the problem.

---

## Key Properties

- **Framework for thinking** – BTR is primarily a thinking framework for working through ideas
- **Context control** – BTR curates what context matters, how it's understood, and how it connects
- **Context permanence** – Documented BTR survives token limits, transfers between AI models
- **System-agnostic** – Works for any system of systems
- **Goal-anchored** – Start with your End Goal, even if rough
- **Backward-working** – Trace relationships backward from End Goal to Entry Point
- **Entry Point driven** – Discovery completes when you find the root dependency
- **Readiness-gated** – Explicit checkpoint before execution
- **Iterative** – Each pass narrows scope and increases clarity

---

*BTR Framework by Stephen Billet*
*Created: 2025-01-05*

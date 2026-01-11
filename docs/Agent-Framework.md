# BTR Coding Agent Framework

A framework for specialized AI agents that review and improve code. Each agent has narrow focus, explicit inputs/outputs, and produces artifacts consumable by other agents or humans.

---

## Core Principle

**One agent, one concern.** 

Each agent has:
- **Boundaries** - What it looks at, what it ignores
- **Terms** - Domain vocabulary it understands
- **Relationships** - What it depends on, what depends on it
- **Input** - What it receives (code, context, prior audits)
- **Output** - Markdown audit with findings and recommendations

Agents don't solve problems - they surface them. A main coding agent or human acts on the audits.

---

## Why Agents?

AI-generated code often suffers from:
- Local solutions without global coherence
- Inconsistent patterns across files
- Security oversights
- Missed edge cases
- Performance issues that compound

Specialized agents address this by:
- **Narrow focus** - Each agent masters one concern
- **Stack-specific knowledge** - Agents know your framework's gotchas
- **Consistent review** - Same checks every time
- **Documented findings** - Audits persist and accumulate

---

## Agent Categories

### Code Quality Agents
Analyze code for specific quality dimensions.

| Agent | Focus |
|-------|-------|
| Security | Vulnerabilities, auth, secrets, injection |
| Performance | Efficiency, queries, memory, bundle size |
| Edge Cases | Null handling, boundaries, error paths |
| Maintainability | Coupling, clarity, surface area |
| Consistency | Pattern adherence, naming, structure |

### Process Agents
Handle workflow stages.

| Agent | Focus |
|-------|-------|
| Test Scenarios | Generate test cases |
| Documentation | Docs, comments, README |
| Dependencies | Package audits, CVEs, licenses |

### Meta Agents
Orchestrate and synthesize.

| Agent | Focus |
|-------|-------|
| Review | Synthesize all findings, prioritize actions |

---

## How Agents Work

### Input
- Source code (files or folders)
- `.claude/agents/config.md` for project context
- Prior audit findings (for Review agent)

### Process
- Read code with stack-specific awareness
- Check against known patterns and anti-patterns
- Identify issues by severity

### Output
Markdown audit in `audits/` folder:

```markdown
## [Agent] Audit
**Scope:** [files analyzed]
**Date:** [date]

### Critical
- **[Issue]** - Location: `[file:line]` - [Details]

### Warning
- **[Issue]** - Location: `[file:line]` - [Details]

### Observations
- [Pattern worth noting]

### Verified
- [Good practice found]
```

---

## Stack Customization

Agents are customized based on your BTR artifact's tech stack:

| If Stack Includes | Agents Get |
|-------------------|------------|
| Next.js | Server/client component checks, API route security |
| Firebase | Security rules, Firestore query patterns, offline handling |
| TypeScript | Strict mode checks, type assertion warnings |
| React | Hook rules, re-render patterns, cleanup checks |
| Business Central AL | Permission sets, record locking, FindFirst patterns |

This customization happens automatically when agents are generated from your BTR artifact.

---

## Workflow

```
Code Change
     │
     ▼
Run Agents (/agents [name])
     │
     ├── Security Agent ──────┐
     ├── Performance Agent ───┤
     ├── Edge Cases Agent ────┤
     │                        │
     │                        ▼
     │               Individual Audits
     │                        │
     │                        ▼
     └───────────────► Review Agent
                              │
                              ▼
                    Consolidated Audit
                    (Prioritized Actions)
                              │
                              ▼
                    Implement Fixes
                              │
                              ▼
                    Re-run Agents (verify)
```

---

## Using Agents

### List Available Agents
```
/agents
```

### Run Specific Agent
```
/agents security
/agents edge-cases
```

### Run All Agents
```
Run all agents on src/
```

### After Audit
```
Read audits/ and implement critical fixes
Re-run security agent to verify fixes
```

---

## Agent Surface Area

Each agent is designed with minimal surface area:

**Inputs:**
- Code to analyze
- Config for context

**Outputs:**
- Markdown audit

**No hidden dependencies:**
- Agents don't modify code
- Agents don't call external services
- Agents produce only documentation

This makes agents predictable, composable, and debuggable.

---

## Relationship to BTR

This agent framework applies BTR principles:

- **Boundaries** - Each agent has explicit scope
- **Terms** - Agents share vocabulary via config.md
- **Relationships** - Review agent depends on other agents

The audits themselves are BTR-style artifacts:
- Structured context
- Survives sessions
- Transfers between conversations
- Actionable by humans or AI

---

*Part of: BTR Framework*

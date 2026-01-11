# BTR Programming for Claude Code

A project template that combines the **BTR Framework** (Boundaries, Terms, Relationships) with **AI coding agents** for Claude Code.

**Clone → Init → Build**

---

## What This Is

A starter template for new programming projects that:

1. **Starts with BTR Discovery** - Claude guides you through scoping before you write code
2. **Generates Custom Agents** - Code review agents tailored to your tech stack
3. **Maintains Quality** - Agents catch security, performance, and edge case issues as you build

---

## Quick Start

```bash
# Clone the template
git clone https://github.com/[your-username]/BTRProgrammingForClaudeCode.git my-project
cd my-project

# Remove the template's git history and start fresh
rm -rf .git
git init

# Open in Claude Code
claude .
```

Claude automatically enters BTR Discovery mode. Work through the prompts to define your project scope and tech stack.

---

## The Workflow

```
Clone Template
      │
      ▼
Open Claude Code
      │
      ▼
BTR Discovery (automatic)
  • Define End Goal
  • Set Boundaries  
  • Establish Terms
  • Choose Tech Stack
  • Map Relationships
  • Find Entry Point
      │
      ▼
Agents Generated
  • Customized to your stack
  • Available via /agents
      │
      ▼
Execution
  • Build from Entry Point
  • Agents review your code
  • Iterate toward End Goal
```

---

## What's Included

```
BTRProgrammingForClaudeCode/
├── CLAUDE.md                 # Project config - triggers BTR mode
├── README.md                 # This file
├── .gitignore               
├── docs/
│   ├── BTR-Framework.md      # Full BTR methodology
│   ├── BTR-Glossary.md       # Term definitions
│   ├── BTR-Artifact-Spec.md  # What a complete BTR artifact contains
│   └── Agent-Framework.md    # How the agent system works
├── templates/
│   ├── BTR-template.md       # Template for your BTR artifact
│   └── agents/               # Agent templates (copied to .claude/)
│       ├── config.md
│       ├── security.md
│       ├── performance.md
│       ├── edge-cases.md
│       ├── maintainability.md
│       ├── consistency.md
│       ├── test-scenarios.md
│       ├── documentation.md
│       ├── dependencies.md
│       └── review.md
└── audits/                   # Agent outputs go here
    └── .gitkeep
```

---

## After BTR Discovery

Once you complete BTR discovery, your project will have:

```
your-project/
├── CLAUDE.md                 # Updated with your project context
├── docs/
│   └── BTR.md                # Your BTR artifact (scope, stack, entry point)
├── .claude/
│   └── agents/               # Agents customized to YOUR stack
│       ├── config.md         # Your tech stack, terms, boundaries
│       ├── security.md       # With stack-specific checks
│       └── ...
├── audits/                   # Agent findings
└── src/                      # Your code (structure defined in BTR)
```

---

## Using Agents

After setup, agents are available via `/agents` command:

```bash
/agents                    # List all agents
/agents security          # Run security agent
/agents review            # Synthesize all findings

# Or natural language
"Run all agents on src/"
"Run security and edge-cases on the changed files"
"Read audits and implement critical fixes"
```

---

## The BTR Framework

**BTR = Boundaries, Terms, Relationships**

A methodology for scoping AI interactions. Instead of diving into code with a vague idea, BTR helps you:

1. **Start with End Goal** - What are you actually building?
2. **Work Backward** - What must exist before what?
3. **Find Entry Point** - Where does building actually start?
4. **Assess Readiness** - Do you have enough to begin?

Read the full methodology: [docs/BTR-Framework.md](docs/BTR-Framework.md)

---

## Why This Exists

AI-generated code often suffers from:
- Local solutions without global coherence
- Inconsistent patterns across files
- Missed edge cases
- Security oversights

BTR + Agents addresses this by:
- **Scoping first** - Know what you're building before you build
- **Stack-specific review** - Agents know your framework's gotchas
- **Continuous quality** - Review as you go, not just at the end

---

## Customization

### Adding Stack-Specific Checks

Edit agents in `.claude/agents/` to add checks for your specific technologies.

### Skipping BTR Discovery

If you already know your scope, you can:
1. Create `docs/BTR.md` manually using `templates/BTR-template.md`
2. Run: `Read docs/BTR.md and generate agents`

### For Existing Projects

If adding to an existing codebase, use:
```
Read templates/agents/config.md and set up agents for this project
```

---

## License

MIT - Use freely, attribution appreciated.

---

## Contributing

Improvements welcome. The framework evolves through use.

---

*BTR Framework: Start with End Goal. Work backward to Entry Point. Execute forward.*

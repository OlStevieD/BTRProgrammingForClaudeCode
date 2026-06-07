# Claude Code Adapter

This adapter preserves the original Claude Code agent workflow for BTR projects.

The canonical BTR method now lives in the skill-first framework:

- `../../docs/BTR-Method.md`
- `../../docs/BTR-Framework.md`
- `../../skills/btr/SKILL.md`
- `../../skills/btr-review/SKILL.md`

The files in `agents/` are runtime-specific Claude Code review agents. They can still be copied into a project-local `.claude/agents/` directory, but they should be treated as adapter outputs, not the source of truth.

## Usage

For a Claude Code project that already has a completed `docs/BTR.md`:

```bash
mkdir -p .claude/agents
cp adapters/claude-code/agents/*.md .claude/agents/
```

Then use Claude Code's agent workflow as before.

## Rule

If a generated agent conflicts with `docs/BTR.md`, the BTR artifact wins. Update the artifact or regenerate the agent rather than letting project-local prompts silently redefine scope.

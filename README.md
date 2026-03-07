# AYAYAY

Personal GitHub Copilot resources repository for reusable prompts, custom agents, instructions, and skills.

## Purpose

This repo is a single place to store GitHub Copilot assets you use regularly so they are:
- versioned
- searchable
- easy to reuse
- easy to evolve over time

## Repository Layout

```text
.github/
  agents/         # Custom agent definitions (*.agent.md)
  instructions/   # Reusable instruction files (*.instructions.md)
  prompts/        # Prompt library grouped by use case
  skills/         # Reusable skills (folder with SKILL.md)
```

See `.github/README.md` and each subdirectory `README.md` for detailed formats and examples.

## Self-Improvement Prompt

The repository includes a **self-improvement prompt** (`.github/prompts/self-improvement.prompt.md`) for meta-cognitive analysis. Invoke it directly in an active conversation:

**Use the self-improvement prompt to:**
- 📊 Analyze your performance across 6 dimensions (accuracy, efficiency, code quality, communication, proactivity, safety)
- 🔍 Identify success and failure patterns from the conversation
- 📝 Review and update configuration files based on learnings

**See**: [`.github/prompts/self-improvement.prompt.md`](.github/prompts/self-improvement.prompt.md) for full details.

## Naming Conventions

- Use lowercase and kebab-case for file/folder names.
- Prefer specific names over generic ones.
- Good: `summarize-meeting-notes.prompt.md`
- Avoid: `prompt1.md`
- Use these extensions for discoverability:
- `*.agent.md`
- `*.instructions.md`
- `SKILL.md` inside a skill folder

## Quick Start

1. Add a useful prompt in `.github/prompts/`.
2. Add one custom instruction file in `.github/instructions/`.
3. Add one reusable skill in `.github/skills/`.
4. Commit early with small, descriptive commits.

## Suggested Workflow

1. Capture ideas directly in draft prompt/agent/skill files.
2. Promote stable patterns into `.github/prompts/`, `.github/instructions/`, or `.github/skills/`.
3. Retire or archive stale items regularly.

## License

See `LICENSE`.

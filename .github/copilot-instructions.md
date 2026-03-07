# Project Guidelines

## Code Style
- Prefer clear naming and small, focused changes.
- Add short comments only where intent is not obvious.
- Follow DRY by consolidating duplicate patterns.

## Architecture
- This repo is a library of GitHub Copilot assets.
- Asset types live under `.github/`:
  - `agents/` for `*.agent.md`
  - `instructions/` for `*.instructions.md`
  - `prompts/` for `*.prompt.md`
  - `skills/` for skill folders containing `SKILL.md`

## Build and Test
- No build or test commands are defined.

## Conventions
- Use lowercase kebab-case for file and folder names.
- Use the correct extension for each asset type.
- Follow the format guidance in the relevant README:
  - `.github/README.md`
  - `.github/instructions/README.md`
  - `.github/agents/README.md`
  - `.github/prompts/README.md`
  - `.github/skills/README.md`

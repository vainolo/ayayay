# Instructions

## What Are Instruction Files?

Instruction files provide reusable coding guidelines that GitHub Copilot automatically applies when working with matching files. They enforce coding standards, best practices, and team conventions without needing to repeat them in every conversation.

## Format

Instruction files use Markdown with YAML frontmatter:

```markdown
---
applyTo: "glob pattern for matching files"
---

Your instructions here.
```

### Required Fields
- `applyTo`: Glob pattern specifying which files these instructions apply to
  - Examples: `"**/*.ts"`, `"src/**/*.{js,jsx}"`, `"**/*.py"`

### Optional Fields
- `priority`: Control loading order when multiple instructions match
- Additional metadata as needed

## Use

GitHub Copilot automatically loads instruction files when you:
- Open or edit a file matching the `applyTo` pattern
- Ask questions about code in matching files
- Request code generation for matching file types

Instructions are ideal for:
- Enforcing coding standards and conventions
- Specifying preferred libraries or patterns
- Setting file-type-specific rules (e.g., React patterns for `.jsx` files)
- Defining error handling approaches
- Establishing documentation requirements

## File Pattern

`<name>.instructions.md`

## Sample

**File: `react-components.instructions.md`**

```markdown
---
applyTo: "src/components/**/*.{jsx,tsx}"
---

# React Component Guidelines

- Use functional components with hooks (no class components)
- Implement proper TypeScript types for all props
- Follow naming convention: PascalCase for components, camelCase for files
- Include PropTypes or TypeScript interfaces
- Extract complex logic into custom hooks
- Keep components under 200 lines; split larger ones
- Use CSS modules or styled-components (no inline styles)
- Add JSDoc comments for exported components
```

# Prompt Library

## What Are Prompt Files?

Prompt files are reusable templates for common coding tasks that you can quickly invoke in GitHub Copilot. They provide structured formats for repetitive workflows like code reviews, documentation generation, or refactoring tasks.

## Format

Prompt files are plain Markdown documents without YAML frontmatter:

```markdown
# Prompt Title

## Context
What this prompt is for

## Inputs
- What information is needed
- What files to analyze

## Output
- What should be produced
- Format specifications
```

Prompts can include:
- Structured sections for consistency
- Checklists for completeness
- Output format specifications
- Examples of desired results

## Use

You manually reference prompt files in your GitHub Copilot conversations:
- Copy the prompt content and paste into chat
- Reference the prompt file: "Follow the process in code-review.prompt.md"
- Use as templates for consistent workflows across your team

Prompts are ideal for:
- Standardized code reviews
- Architecture decision records
- Refactoring checklists
- Documentation templates
- Bug investigation workflows
- Performance analysis procedures

## File Pattern

`<use-case>.prompt.md`

## Examples
- `code-review.prompt.md`
- `architecture-brainstorm.prompt.md`
- `refactor-checklist.prompt.md`
- `bug-investigation.prompt.md`

## Sample

**File: `refactor-function.prompt.md`**

```markdown
# Function Refactoring Prompt

## Context

Refactor the specified function to improve readability, maintainability, and testability.

## Inputs

- Target function name and file location
- Current pain points or issues
- Performance requirements (if any)

## Analysis Steps

1. Identify single responsibility violations
2. Locate duplicated logic
3. Assess complexity metrics (cyclomatic complexity)
4. Check for proper error handling
5. Review naming clarity

## Output

1. **Issues Found**: List specific problems
2. **Refactored Code**: Improved implementation
3. **Breaking Changes**: Any API changes
4. **Test Updates**: Required test modifications
5. **Performance Impact**: Before/after comparison

## Quality Checklist

- [ ] Function has single, clear responsibility
- [ ] Parameters are well-named and typed
- [ ] Error handling is comprehensive
- [ ] Logic is extracted into helper functions
- [ ] Comments explain "why", not "what"
- [ ] Tests cover edge cases
```

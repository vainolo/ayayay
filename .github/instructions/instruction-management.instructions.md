---
applyTo: "**/.github/instructions/*.instructions.md"
---

# Instruction File Management

## Scope Boundaries (CRITICAL)

When creating or updating instruction files, respect clear categorical boundaries:

### Language Pattern Files
Files like `powershell-patterns.instructions.md`, `python-patterns.instructions.md`, etc.

**Include:**
- ✅ Syntax patterns, idioms, language-specific best practices
- ✅ Standard library usage patterns
- ✅ Language-specific tooling and conventions

**Exclude:**
- ❌ Domain workflows or business logic that happen to use that language
- ❌ Tool-agnostic advice that could apply to any language
- ❌ General coding principles (those belong in coding-standards)

**Example Violations:**
- Adding "SSH Connection Patterns" to `powershell-patterns.instructions.md` → Domain workflow, not language pattern
- Adding "Script Naming Alignment" to language-specific file → General principle, not language-specific

### General Standards Files
Files like `coding-standards.instructions.md`

**Include:**
- ✅ Cross-language principles (naming, DRY, testing)
- ✅ Project-wide conventions that apply regardless of language
- ✅ Universal best practices

**Exclude:**
- ❌ Language-specific syntax or idioms
- ❌ Domain-specific workflows

### Domain/Project Files
Files specific to business domains or project architecture

**Include:**
- ✅ Business workflows and processes
- ✅ Architecture patterns specific to this project
- ✅ Domain-specific requirements

**Exclude:**
- ❌ General coding advice
- ❌ Language syntax patterns

## Before Creating or Updating Instruction Files

1. **Check existing files** - Don't duplicate content across files
2. **Verify scope** - Does this content match the file's category?
3. **Test categorization** - Ask: "Is this language-specific, domain-specific, or universal?"
4. **Keep it focused** - Each file should have a clear, singular purpose

## Red Flags

- Content that could apply to multiple languages → Probably belongs in general standards
- Workflow descriptions in language pattern files → Probably belongs in domain docs
- Duplicate guidance across multiple files → Consolidate into most appropriate file

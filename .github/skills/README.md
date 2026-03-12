# Skills

## What Are Skills?

Skills are specialized knowledge packages that provide GitHub Copilot with domain-specific expertise. Each skill encapsulates workflow steps, decision criteria, and best practices for a particular technical area (e.g., database migrations, API security, testing strategies).

Skills differ from other agent files:
- **Agents**: Complete personas for entire conversations
- **Instructions**: Auto-applied file-specific rules
- **Prompts**: Manual templates for common tasks
- **Skills**: Domain expertise invoked when needed

## Format

Each skill is a folder containing a `SKILL.md` file:

```
skill-name/
  SKILL.md
  [optional supporting files]
```

The `SKILL.md` file uses Markdown with optional YAML frontmatter:

```markdown
---
name: skill-name
description: Brief description of when to use this skill
invokes: [optional] List of tools this skill commonly uses
---

# Skill Name

## Purpose
What problem this skill solves

## When To Use
Criteria for invoking this skill

## Steps
1. Detailed workflow steps
2. Decision points
3. Validation criteria

## Inputs
- What information is required
- What context is needed

## Output
- What this skill produces
- Format and structure

## Best Practices
- Domain-specific guidelines
- Common pitfalls to avoid
```

## What's Needed to Implement a Skill

### 1. Domain Expertise
- Deep understanding of a specific technical area
- Common patterns, anti-patterns, and edge cases
- Best practices and industry standards

### 2. Structured Workflow
- Clear steps that can be followed systematically
- Decision points and branching logic
- Success criteria and validation steps

### 3. Documentation
- When to use this skill vs. alternatives
- Required inputs and expected outputs
- Examples demonstrating typical usage

### 4. Optional Supporting Files
- Configuration templates
- Code snippets or examples
- Reference documentation
- Checklists

## Use

GitHub Copilot can automatically invoke skills when:
- Keywords or patterns in your request match the skill description
- You explicitly mention the skill: "Use the database-migration skill"
- The task clearly falls within the skill's domain

Skills are ideal for:
- Complex multi-step technical procedures
- Domain-specific decision making (e.g., choosing database indexes)
- Specialized code generation (e.g., security-hardened authentication)
- Standardized workflows (e.g., migration patterns)

## File Pattern

`<skill-name>/SKILL.md`

## Included Skills

- `example-skill/SKILL.md`

## Sample

**Directory: `database-migration/`**

**File: `database-migration/SKILL.md`**

```markdown
---
name: database-migration
description: Safely create and test database migrations with rollback support
invokes: [file_search, read_file, run_in_terminal]
---

# Database Migration Skill

## Purpose

Create safe, reversible database migrations that can be deployed without downtime.

## When To Use

- Adding/modifying database tables or columns
- Changing indexes or constraints
- Data transformation during schema changes
- Need rollback capability for production deployments

## Steps

1. **Analyze Current Schema**
   - Review existing database structure
   - Identify dependencies and foreign keys
   - Check for data that will be affected

2. **Design Migration Strategy**
   - Prefer additive changes (add column before removing old one)
   - Plan for backwards compatibility during deployment
   - Identify if data migration is needed

3. **Create Migration Files**
   - Generate UP migration (apply changes)
   - Generate DOWN migration (rollback)
   - Include transaction wrappers when possible

4. **Add Validation**
   - Check constraints before and after
   - Verify data integrity
   - Test foreign key relationships

5. **Test Locally**
   - Apply migration to local database
   - Verify application still works
   - Test rollback procedure
   - Check performance impact

## Inputs

- Desired schema changes
- Current database schema/ORM models
- Migration framework in use (e.g., Alembic, Flyway, Entity Framework)

## Output

- UP migration file
- DOWN migration file
- Testing instructions
- Rollback procedure
- Deployment notes (e.g., requires downtime, can run online)

## Best Practices

### Safety
- Always create DOWN migration for rollback
- Use transactions when supported
- Test on production-like data volume
- Never delete columns in first migration (deprecate first)

### Performance
- Add indexes in separate migration if large table
- Consider batch operations for data migrations
- Avoid full table locks on large tables

### Naming Convention
- Include timestamp: `20260304_add_user_email_index.sql`
- Use descriptive names: what changed, not why

## Common Patterns

### Adding a Required Column
```
1. Add column as nullable
2. Populate data with default values
3. Make column NOT NULL
4. Deploy in separate releases
```

### Renaming a Column
```
1. Add new column
2. Dual-write to both columns
3. Backfill old data
4. Switch reads to new column
5. Remove old column (separate release)
```
```

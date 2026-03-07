# Repository Health Check Prompt

Perform a comprehensive health analysis of one or more repositories in the workspace.

## Context

Use when asked to analyze, audit, or assess repository status, health, or readiness.

## Process

### 1. Inventory & Context Gathering
- List all files in each repository (use file_search with appropriate patterns)
- Check git status (staged, modified, untracked files)
- Identify hidden/gitignored folders that may contain secrets or runtime artifacts
- Read key documentation files (README, LICENSE, project configs)
- Check for errors/warnings via get_errors

### 2. Cross-Reference Analysis
- Compare documentation claims with actual code behavior
- Check for naming consistency (filenames in docs vs actual paths)
- Validate configuration references (log paths, rule names, etc.)
- Look for version/format drift between related files

### 3. Code Quality Review
- Check scripts for proper error handling
- Verify idempotency where expected
- Look for hardcoded values that should be configurable
- Check for security issues (exposed credentials, overly permissive access)

### 4. Testing & Validation
- Identify test/diagnostic scripts and assess their correctness
- Look for logic bugs (wrong operators, unreachable code, stale conditionals)
- Check if test scripts actually return actionable output

### 5. Categorize Findings by Severity
- **High**: Security issues, data loss risks, broken core functionality
- **Medium**: Logic errors, misleading behavior, documentation drift
- **Low**: Cosmetic issues, minor inconsistencies, optimization opportunities

## Output

Provide a structured status report:

```markdown
## Repository Status: [Name]

**Overall**: [Clean / Needs Attention / Critical Issues]

### Findings (by severity)

**High Priority**
1. [Issue]: [Brief description] - [File/line reference]
   - Impact: [What goes wrong]
   - Fix: [Specific action needed]

**Medium Priority**
...

**Low Priority**
...

### Operational Status
- Git: [Clean working tree / X staged, Y modified]
- Secrets: [Properly gitignored / Exposed in version control]
- Tests: [Passing / Failing / Not run]
- Documentation: [Up to date / Drift detected]

### Recommended Next Steps
1. [Prioritized action]
2. [Prioritized action]
```

## Key Principles

- **Clarify intent before suggesting fixes**: If something looks wrong but could be intentional (e.g., permissive access for testing), explain and ask rather than assuming
- **Test proposed fixes**: Don't just report issues—verify your suggested fixes actually work (unless destructive)
- **Be specific**: Provide file paths, line numbers, and exact text references
- **Prioritize correctly**: Security/data issues are more urgent than cosmetic problems

## Inputs Needed

- Target repository path(s)
- Scope: Full audit or specific subsystem
- Focus areas (if any): security, documentation, testing, etc.

## When to Use This Prompt

- User asks for repo status, health check, or audit
- Before major refactoring to establish baseline
- After receiving or inheriting a codebase
- Periodic maintenance reviews

---
applyTo: "**/*.{cs,js,ts,py,md,ps1,psm1}"
---

Prefer clear naming and small functions.
Keep changes minimal and focused.
Add short comments only where code intent is not obvious.
Do not repeat yourself (DRY principle). Consolidate duplicate code into reusable functions or modules.

## Shared Utilities & Refactoring

When multiple scripts repeat the same patterns:
- Extract common functionality into a shared utility module (e.g., `common.ps1`, `helpers.ts`)
- Use consistent naming conventions for shared functions across all consumers
- Place shared utilities in the root or a dedicated `lib/` directory
- Update all consumers to use the shared version rather than maintaining duplicates
- Avoid creating multiple utility files for similar concerns—consolidate into one

## Configuration Management

- Extract config loading and validation into reusable functions
- Make optional parameters with sensible defaults rather than requiring all config keys
- Validate required keys at load time, not at usage time
- Return structured objects (not dictionaries) from config functions for type safety where possible

## Naming & Behavior Alignment

Ensure script/function names accurately reflect their behavior:
- If behavior changes significantly, consider renaming
- When finding mismatches between name and behavior, suggest renaming
- Names should clearly indicate what the script/function does, not what it might do

## Testing & Validation

Always test code changes before completing a task, except when testing would be destructive or irreversible.
- After modifying scripts, run them with representative inputs to verify behavior
- When auth/credentials are needed, ask the user to provide them rather than skipping tests
- Clean up test resources (temporary rules, test data) after validation
- For configuration/documentation changes, validate syntax and verify no broken references remain

## Debugging Assertions & Scope Discipline

- During debugging, prefer minimal fixes in the canonical script or module already responsible for the behavior. Do not add new helper/installer scripts unless the user asks for them.
- When there is a single source of truth for behavior (for example, one script that manages NSG rules), place the change there rather than layering workaround logic in other scripts.

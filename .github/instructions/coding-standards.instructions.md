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

## Infrastructure & Architecture Decisions

Before implementing infrastructure deployments or resource-intensive solutions:
- **Validate core assumptions** against known service limits and incompatibilities (e.g., CPU inference performance, memory constraints, service quotas)
- **Test with minimal configuration** first: verify the approach works before scaling resources or complexity
- **Prefer error evidence over status indicators**: Container "Running" status ≠ application started; fetch actual logs immediately when status seems inconsistent with connectivity
- **Batch diagnostic attempts**: Instead of one edit → one deployment → check status → edit again, identify root cause first through logs/research, then make targeted fix

## Debugging Priority

When troubleshooting failures:
1. **Fetch actual error output first** (logs, exit codes, stderr) before relying on derived status information
2. **Verify assumptions with minimal reproduction**: Don't scale complexity until core issue is resolved
3. **Research known incompatibilities**: For infrastructure tasks, check if the combination of technologies has known limitations before multi-attempt troubleshooting
4. **Parallelize independent diagnostic operations**: Gather all information before deciding on next steps

## Debugging Assertions & Scope Discipline

- During debugging, prefer minimal fixes in the canonical script or module already responsible for the behavior. Do not add new helper/installer scripts unless the user asks for them.
- When there is a single source of truth for behavior (for example, one script that manages NSG rules), place the change there rather than layering workaround logic in other scripts.
- **Respect explicit user directives**: If user states a completion criterion (e.g., "continue until X works"), treat as binding requirement, not optional goal. Escalate with clear evidence if completion is not feasible.

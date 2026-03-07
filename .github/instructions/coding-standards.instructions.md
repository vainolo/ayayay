---
applyTo: "**/*.{cs,js,ts,py,md,ps1,psm1}"
---

Prefer clear naming and small functions.
Keep changes minimal and focused.
Add short comments only where code intent is not obvious.
Do not repeat yourself (DRY principle). Consolidate duplicate code into reusable functions or modules.

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

# Feature Specification Format

This document defines the standard format for feature specification documents (`feature-spec.md`) produced during Phase 2 of the software development workflow framework.

All feature specifications are persisted at `memory/product/<branch-name>/shared/feature-spec.md`.

---

## Format

### 1. Metadata

| Field   | Value                              |
|---------|------------------------------------|
| Title   | Short feature or product name      |
| Author  | Agent or user that drafted         |
| Date    | ISO-8601 creation date             |
| Status  | Draft / In-Review / Approved       |
| Version | Semantic version (e.g. 0.1)        |
| Branch  | Git branch name                    |

### 2. Summary

One or two sentences describing the feature or product being built. Should be readable without technical background.

### 3. Problem Statement

Describe the problem this feature solves, its context, and why it matters. Keep this factual and concise. Do not prescribe solution here.

### 4. Goals

Explicit, testable goals this feature must achieve. Write as statements that can be confirmed true or false after delivery.

- Goal 1
- Goal 2

### 5. Non-Goals

What this feature explicitly does not do. Prevents scope creep and clarifies intent boundaries.

- Non-goal 1
- Non-goal 2

### 6. User Stories and Use Cases

Describe who uses this feature, in what context, and what outcome they expect.

```
As a <role>, I want <capability> so that <benefit>.
```

### 7. Acceptance Criteria

Formal conditions that must be true for this feature to be considered complete. Each criterion must be independently verifiable by a test or inspection.

- [ ] Criterion 1
- [ ] Criterion 2

### 8. Constraints

Technical, regulatory, time, or resource constraints that limit how this feature can be implemented.

- Constraint 1
- Constraint 2

### 9. Assumptions

Conditions assumed to be true for this specification to be valid. If any assumption is violated, the spec must be revisited before implementation continues.

- Assumption 1
- Assumption 2

### 10. Dependencies

External systems, teams, services, APIs, or features this work depends on.

- Dependency 1
- Dependency 2

### 11. Open Questions

Unresolved questions that need answers before or during implementation. Include owner and target resolution date where possible.

| Question | Owner | Status |
|----------|-------|--------|
| Example question | Name | Open |

### 12. Out of Scope

Work explicitly excluded from this feature. Distinct from Non-Goals, which defines purpose; this defines delivery boundaries.

### 13. Revision History

| Version | Date       | Author | Change Summary  |
|---------|------------|--------|-----------------|
| 0.1     | YYYY-MM-DD | Name   | Initial draft   |

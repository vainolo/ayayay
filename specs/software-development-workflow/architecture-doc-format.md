# Architecture Design Document Format

This document defines the standard format for architecture design documents (`architecture-design.md`) produced during Phase 3 of the software development workflow framework.

All architecture design documents are persisted at `memory/product/<branch-name>/shared/architecture-design.md`.

---

## Format

### 1. Metadata

| Field          | Value                              |
|----------------|------------------------------------|
| Title          | Short architecture title           |
| Author         | Agent or user that drafted         |
| Date           | ISO-8601 creation date             |
| Status         | Draft / In-Review / Approved       |
| Version        | Semantic version (e.g. 0.1)        |
| Related Spec   | Path to feature-spec.md            |
| Branch         | Git branch name                    |

### 2. Overview

One paragraph summarizing the technical approach for delivering the feature. Should be readable without deep knowledge of implementation details.

### 3. Context and Constraints

Technical context that shapes the architecture decisions. Include:

- Existing system constraints agents must work within
- Technology mandates or restrictions
- Non-functional requirements: performance, security, scalability, availability
- Integration points with external systems or services

### 4. System Context

Describe how this feature fits within the broader system.

- **Actors**: who or what interacts with this feature
- **External systems**: what this feature integrates with
- **System boundaries**: what is inside and outside the scope of this design

### 5. Component Design

Define the components or modules introduced or modified by this feature. For each component:

**Component Name**
- Responsibility: what it does
- Interface: how other components interact with it
- Dependencies: what it depends on
- Notes: decisions, trade-offs, or constraints specific to this component

### 6. Data Model and Flow

Describe data structures, schemas, and how data moves through the system.

- Entity definitions (fields, types, constraints)
- Data flow narrative or diagram where helpful
- Storage locations and data lifecycle

### 7. API Contracts

Define all new or modified APIs introduced by this feature.

**Endpoint or Interface Name**
- Method: GET / POST / PUT / DELETE / etc.
- Path or function signature
- Request format and required fields
- Response format and status codes
- Error responses and codes
- Authentication and authorization requirements

### 8. Deployment and Infrastructure

Describe any infrastructure, deployment, or operational considerations.

- New services, containers, functions, or jobs
- Configuration requirements and environment variables
- Environment-specific considerations (dev / staging / prod)
- Rollback strategy

### 9. Testing Strategy

Describe the planned testing approach for this architecture.

- Unit test scope: which modules and functions require unit tests
- E2E test scenarios: which user flows must be covered by E2E tests
- Edge cases requiring explicit test coverage
- Known gaps or testing limitations

### 10. Trade-offs and Alternatives Considered

Document alternatives that were evaluated and why the chosen approach was selected.

| Alternative | Pros | Cons | Decision |
|-------------|------|------|----------|
| Option A    | ...  | ...  | Rejected |
| Chosen      | ...  | ...  | Adopted  |

### 11. Risks and Mitigations

Known technical or integration risks and how they will be mitigated.

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|-----------|
| Risk 1 | Medium | High | Strategy |

### 12. Decision Log

Record significant architectural decisions made during Phase 3.

| Decision | Context | Options Considered | Choice | Rationale |
|----------|---------|--------------------|--------|-----------|
| Decision 1 | Why it mattered | A, B | A | Reason |

### 13. Revision History

| Version | Date       | Author | Change Summary  |
|---------|------------|--------|-----------------|
| 0.1     | YYYY-MM-DD | Name   | Initial draft   |

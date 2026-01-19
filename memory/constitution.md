# Product Constitution

> **Purpose**: This document defines the foundational principles, guardrails, and strategic context that govern all PRDs in this product. All feature decisions must align with these principles.

---

## Product Vision

[Describe the product vision - what future are you building towards?]

**Example**: *"Empower every developer to ship secure, high-quality software faster through AI-assisted workflows."*

---

## Target Users

### Primary Persona

| Attribute | Description |
|-----------|-------------|
| **Name** | [Persona name, e.g., "Sarah the Senior PM"] |
| **Role** | [Job title/function] |
| **Goals** | [What they're trying to achieve] |
| **Pain Points** | [Current frustrations] |
| **Context** | [Environment, tools, constraints] |

### Secondary Personas

[List additional user types that influence decisions but aren't the primary focus]

---

## Product Principles

> These are non-negotiable guardrails. Any PRD that violates a MUST principle fails consistency checks.

### MUST Principles (Non-Negotiable)

| ID | Principle | Rationale |
|----|-----------|-----------|
| MUST-001 | [Principle statement] | [Why this is non-negotiable] |
| MUST-002 | [Principle statement] | [Why this is non-negotiable] |
| MUST-003 | [Principle statement] | [Why this is non-negotiable] |

**Examples**:
- MUST-001: "All user data must be encrypted at rest and in transit" - Compliance requirement
- MUST-002: "Features must work offline-first" - Core product differentiator
- MUST-003: "No feature ships without accessibility compliance" - Company policy

### SHOULD Principles (Strong Preferences)

| ID | Principle | Rationale |
|----|-----------|-----------|
| SHOULD-001 | [Principle statement] | [Why this is preferred] |
| SHOULD-002 | [Principle statement] | [Why this is preferred] |

**Examples**:
- SHOULD-001: "Prefer progressive disclosure over upfront complexity"
- SHOULD-002: "Design for power users but don't exclude beginners"

### AVOID Principles (Anti-Patterns)

| ID | Anti-Pattern | Rationale |
|----|--------------|-----------|
| AVOID-001 | [What to avoid] | [Why it's problematic] |
| AVOID-002 | [What to avoid] | [Why it's problematic] |

**Examples**:
- AVOID-001: "Avoid features that require mandatory training"
- AVOID-002: "Avoid breaking changes to existing workflows"

---

## Strategic Context

### Business Goals

| Goal | Metric | Target |
|------|--------|--------|
| [Goal 1] | [How measured] | [Target value] |
| [Goal 2] | [How measured] | [Target value] |

### Competitive Positioning

[How does this product differentiate? What's the unique value proposition?]

### Key Dependencies

| Dependency | Owner | Impact |
|------------|-------|--------|
| [System/Team/Service] | [Owner] | [How it affects decisions] |

---

## Team Conventions

### PRD Conventions

| Convention | Standard |
|------------|----------|
| Requirement ID format | `REQ-001`, `REQ-002`, ... |
| User Story ID format | `US-001`, `US-002`, ... |
| Priority levels | P0 (Critical), P1 (High), P2 (Medium), P3 (Low) |
| Estimation scale | T-shirt sizes (S, M, L, XL) or Story Points |

### Stakeholder Roles

| Role | Responsibility | Approvals |
|------|----------------|-----------|
| PM | PRD ownership, prioritization | Feature scope |
| Engineering Lead | Technical feasibility | Architecture decisions |
| Design | UX/UI direction | Design specs |
| [Other] | [Responsibility] | [What they approve] |

### Review Cadence

| Review Type | Frequency | Participants |
|-------------|-----------|--------------|
| PRD Review | [Weekly/Bi-weekly] | [Roles] |
| Stakeholder Sync | [Frequency] | [Roles] |

---

## Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [YYYY-MM-DD] | [Name] | Initial constitution |

---

## Amendments

> Constitution changes require explicit rationale and stakeholder agreement.

[Record any amendments here with date, rationale, and approver]

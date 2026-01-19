# Product Requirements Document: [Feature Name]

> **Purpose**: Comprehensive PRD with complete requirements, user stories, and success criteria for engineering implementation.

---

## Metadata

| Field | Value |
|-------|-------|
| **Feature ID** | [###] |
| **Author** | [PM Name] |
| **Created** | [YYYY-MM-DD] |
| **Last Updated** | [YYYY-MM-DD] |
| **Status** | Draft / In Review / Approved / In Development |
| **Target Release** | [Release name/date] |
| **Constitution Reference** | [../../memory/constitution.md](../../memory/constitution.md) |

### Stakeholders

| Role | Name | Responsibility |
|------|------|----------------|
| PM | [Name] | PRD ownership |
| Engineering Lead | [Name] | Technical feasibility |
| Design | [Name] | UX/UI |
| [Other] | [Name] | [Responsibility] |

### Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1 | [YYYY-MM-DD] | [Name] | Initial draft |

---

## Executive Summary

[2-3 paragraph summary suitable for executive stakeholders. Cover: problem, solution, business impact, timeline.]

---

## Background

### Problem Statement

[Expanded from feature-overview.md. Include context, user research, and business impact.]

### Current State

[How do users solve this problem today? What are the limitations?]

### Evidence & Research

| Source | Date | Key Findings |
|--------|------|--------------|
| [User research / Analytics / Feedback] | [Date] | [Findings] |

---

## Goals & Non-Goals

### Goals

| ID | Goal | Success Metric |
|----|------|----------------|
| G-001 | [What we're trying to achieve] | [How we'll measure success] |
| G-002 | [What we're trying to achieve] | [How we'll measure success] |

### Non-Goals

| ID | Non-Goal | Rationale |
|----|----------|-----------|
| NG-001 | [What we're explicitly NOT doing] | [Why it's out of scope] |
| NG-002 | [What we're explicitly NOT doing] | [Why it's out of scope] |

---

## User Stories

### Primary User Stories

#### US-001: [User Story Title]

**As a** [user type], **I want** [goal] **so that** [benefit].

**Priority**: P0 / P1 / P2 / P3

**Acceptance Criteria**:
- [ ] Given [context], when [action], then [expected result]
- [ ] Given [context], when [action], then [expected result]
- [ ] Given [context], when [action], then [expected result]

**Notes**: [Additional context, edge cases, design considerations]

---

#### US-002: [User Story Title]

**As a** [user type], **I want** [goal] **so that** [benefit].

**Priority**: P0 / P1 / P2 / P3

**Acceptance Criteria**:
- [ ] Given [context], when [action], then [expected result]
- [ ] Given [context], when [action], then [expected result]

---

### Secondary User Stories

[Lower priority stories that enhance but aren't critical to the feature]

---

## Functional Requirements

| ID | Requirement | Priority | User Story | Notes |
|----|-------------|----------|------------|-------|
| REQ-001 | [Specific, testable requirement] | P0 | US-001 | [Context] |
| REQ-002 | [Specific, testable requirement] | P0 | US-001 | [Context] |
| REQ-003 | [Specific, testable requirement] | P1 | US-002 | [Context] |

---

## Non-Functional Requirements

| ID | Category | Requirement | Target |
|----|----------|-------------|--------|
| NFR-001 | Performance | [Requirement] | [Measurable target] |
| NFR-002 | Security | [Requirement] | [Measurable target] |
| NFR-003 | Accessibility | [Requirement] | [Measurable target] |
| NFR-004 | Scalability | [Requirement] | [Measurable target] |

---

## User Experience

### User Flow

```
[Start] → [Step 1] → [Step 2] → [Decision Point]
                                    ↓           ↓
                              [Path A]     [Path B]
                                    ↓           ↓
                                [End A]     [End B]
```

### Wireframes / Mockups

[Link to design files or embed key screens]

| Screen | Description | Link |
|--------|-------------|------|
| [Screen name] | [What it shows] | [Figma/design link] |

### Interaction Details

[Key interaction patterns, animations, feedback mechanisms]

---

## Technical Considerations

> Note: This section captures PM-relevant technical context, not implementation details.

### System Dependencies

| System | Dependency Type | Owner | Impact |
|--------|-----------------|-------|--------|
| [System name] | Blocking / Optional | [Team] | [How it affects the feature] |

### Data Requirements

| Data | Source | Usage | Sensitivity |
|------|--------|-------|-------------|
| [Data type] | [Where it comes from] | [How it's used] | PII / Confidential / Public |

### Integration Points

| Integration | Direction | Purpose |
|-------------|-----------|---------|
| [System/API] | Inbound / Outbound | [What it enables] |

---

## Success Metrics

| ID | Metric | Baseline | Target | Timeline | Owner |
|----|--------|----------|--------|----------|-------|
| SM-001 | [Metric name] | [Current value] | [Target value] | [When measured] | [Who tracks] |
| SM-002 | [Metric name] | [Current value] | [Target value] | [When measured] | [Who tracks] |

### Measurement Plan

[How will you collect and analyze these metrics? What tools/dashboards?]

---

## Risks & Mitigations

| ID | Risk | Likelihood | Impact | Mitigation | Owner |
|----|------|------------|--------|------------|-------|
| R-001 | [Risk description] | Low/Med/High | Low/Med/High | [Mitigation strategy] | [Owner] |
| R-002 | [Risk description] | Low/Med/High | Low/Med/High | [Mitigation strategy] | [Owner] |

---

## Dependencies & Constraints

### Dependencies

| ID | Dependency | Type | Owner | Due Date | Status |
|----|------------|------|-------|----------|--------|
| D-001 | [What's needed] | Blocking / Informational | [Owner] | [Date] | [Status] |

### Constraints

| Constraint | Impact | Workaround |
|------------|--------|------------|
| [Technical/Business/Resource constraint] | [How it limits options] | [How to work within it] |

---

## Timeline & Milestones

| Milestone | Target Date | Dependencies | Status |
|-----------|-------------|--------------|--------|
| PRD Approved | [Date] | Stakeholder review | [Status] |
| Design Complete | [Date] | PRD Approved | [Status] |
| Development Start | [Date] | Design Complete | [Status] |
| Feature Complete | [Date] | Development | [Status] |
| Release | [Date] | QA, Docs | [Status] |

---

## Launch Considerations

### Rollout Strategy

[Phased rollout? Feature flags? A/B testing?]

### Documentation Needs

- [ ] User documentation
- [ ] API documentation (if applicable)
- [ ] Internal runbooks

### Support Readiness

- [ ] Support team briefed
- [ ] FAQ prepared
- [ ] Escalation path defined

### Communication Plan

| Audience | Channel | Message | Timing |
|----------|---------|---------|--------|
| [Internal/External] | [Channel] | [Key message] | [When] |

---

## Appendix

### Glossary

| Term | Definition |
|------|------------|
| [Term] | [Definition] |

### Related Documents

| Document | Link | Purpose |
|----------|------|---------|
| Feature Overview | [./feature-overview.md](./feature-overview.md) | Initial scoping |
| Design Spec | [Link] | Detailed UX |
| Technical Spec | [Link] | Implementation details |

---

## Clarification Markers

<!-- 
Use these markers for areas needing stakeholder input.
Format: [NEEDS CLARIFICATION: specific question]
Maximum 3 markers per document.
Run /pm.clarify to resolve.
-->

---

## Constitution Alignment Checklist

> Verify alignment with product principles before approval.

- [ ] Reviewed against MUST principles in [constitution.md](../../memory/constitution.md)
- [ ] No violations of AVOID principles
- [ ] Aligns with product vision
- [ ] Stakeholder sign-off obtained

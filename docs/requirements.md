# PM Speckit Requirements

> **Purpose**: This document defines what PM Speckit does, its target users, and core capabilities. It serves as the authoritative reference for AI agents working with the PM Speckit codebase.

---

## Overview

PM Speckit is a specification-driven toolkit for Product Managers, adapting the philosophy of [GitHub's spec-kit](https://github.com/github/spec-kit) from developer workflows to PM workflows. It transforms product ideas into structured PRDs, Azure DevOps work items, and supporting artifacts through iterative refinement.

### Core Philosophy

- **Specification-First**: Define *what* and *why* before *how*
- **Iterative Refinement**: Multiple clarification cycles with stakeholders
- **Template-Driven Consistency**: All outputs follow standardized templates
- **Cross-Document Traceability**: Requirements flow from PRD → work items → artifacts
- **AI-Agent Agnostic**: Works with any AI coding assistant (Copilot, Claude, Cursor, etc.)

---

## User Personas

### Primary: Product Manager (PM)

- Creates and maintains PRDs for features
- Collaborates with stakeholders to refine requirements
- Needs to generate Azure DevOps work items from PRDs
- Produces supporting content (docs, blogs, demos)

### Secondary: AI Agent

- Executes PM Speckit commands
- Needs clear context on command behavior and template formats
- Must maintain cross-document consistency

---

## Core Capabilities

### CAP-001: Product Constitution

**Description**: Establish and maintain product principles that guide all PRD decisions.

**User Story**: As a PM, I want to define product guardrails so that all PRDs align with our strategy.

**Acceptance Criteria**:
- Constitution captures product vision, target users, and non-negotiable principles
- All PRDs reference constitution for alignment validation
- Constitution updates trigger consistency checks on existing PRDs

---

### CAP-002: Lightweight PRD (Feature Overview)

**Description**: Create a quick, scoping-focused document for estimation and initial alignment.

**User Story**: As a PM, I want to quickly capture a feature idea so that engineering can provide rough estimates.

**Acceptance Criteria**:
- Generates `feature-overview.md` with: Problem, Solution, Scope, Open Questions
- Marks ambiguous areas with `[NEEDS CLARIFICATION: question]`
- Maximum 3 clarification markers per document
- Suitable for 30-minute stakeholder review

---

### CAP-003: Full PRD

**Description**: Create a comprehensive PRD with complete requirements, success criteria, and user stories.

**User Story**: As a PM, I want a complete PRD so that engineering has everything needed to implement.

**Acceptance Criteria**:
- Generates `prd.md` incorporating `feature-overview.md` content
- Includes: Background, Goals, Non-Goals, User Stories, Requirements, Success Metrics, Risks, Dependencies
- Requirements have unique IDs (REQ-001, REQ-002)
- User Stories follow format: "As a [user], I want [goal] so that [benefit]"
- Success Metrics are measurable with clear targets

---

### CAP-004: Clarify

**Description**: Resolve ambiguities through structured Q&A sessions with stakeholders.

**User Story**: As a PM, I want to systematically resolve open questions so that PRDs are complete.

**Acceptance Criteria**:
- Scans source document for `[NEEDS CLARIFICATION]` markers
- Presents ONE question at a time with context and recommendations
- Records answers in `clarifications.md` with session timestamps
- Applies clarification to source document immediately
- Removes/replaces the clarification marker after resolution

---

### CAP-005: Azure DevOps Work Items

**Description**: Generate structured work item definitions from PRD requirements.

**User Story**: As a PM, I want Azure DevOps work items generated from my PRD so that I can quickly populate the backlog.

**Acceptance Criteria**:
- Parses PRD requirements and user stories
- Generates Epic, Feature, and Task hierarchy
- Each work item includes: Title, Description, Acceptance Criteria, Tags
- Links back to source PRD section
- Output format is copy-paste ready markdown (JSON export future)

---

### CAP-006: Analyze (Consistency Check)

**Description**: Validate cross-document consistency without modifying files.

**User Story**: As a PM, I want to catch inconsistencies before stakeholder review.

**Acceptance Criteria**:
- READ-ONLY operation (no file modifications)
- Checks: Duplicate requirements, ambiguous language, unresolved clarifications
- Validates PRD alignment with constitution principles
- Reports coverage gaps (requirements without work items)
- Severity levels: CRITICAL, HIGH, MEDIUM, LOW

---

### CAP-007: Documentation

**Description**: Generate user-facing documentation from PRD content.

**User Story**: As a PM, I want documentation drafted from my PRD so that I have a starting point.

**Acceptance Criteria**:
- Generates `documentation.md` from PRD
- Focuses on user-facing functionality (not internal requirements)
- Includes: Overview, Getting Started, Features, FAQ
- Follows documentation best practices (task-oriented, scannable)

---

### CAP-008: Blog Post

**Description**: Generate announcement blog post from PRD content.

**User Story**: As a PM, I want a blog post draft so that I can announce the feature.

**Acceptance Criteria**:
- Generates `blog.md` from PRD
- Focuses on user benefits and value proposition
- Includes: Hook, Problem, Solution, Call to Action
- Tone: Engaging, customer-focused

---

### CAP-009: Demo Script

**Description**: Generate demo outline and talking points from PRD content.

**User Story**: As a PM, I want a demo script so that I can present the feature.

**Acceptance Criteria**:
- Generates `demo-script.md` from PRD
- Includes: Setup, Key Scenarios, Talking Points, Q&A Prep
- Focuses on user stories and success scenarios
- Estimated timing per section

---

## Command Summary

| Command | Creates | Description |
|---------|---------|-------------|
| `/pm.constitution` | `memory/constitution.md` | Establish product principles |
| `/pm.specify` | `feature-overview.md` | Lightweight PRD for scoping |
| `/pm.prd` | `prd.md` | Full PRD (incorporates feature overview) |
| `/pm.clarify` | `clarifications.md` + updates source | Resolve open questions |
| `/pm.tasks` | `ado-workitems.md` | Generate Azure DevOps work items |
| `/pm.analyze` | Console report | Cross-document consistency check |
| `/pm.docs` | `documentation.md` | Generate user documentation |
| `/pm.blog` | `blog.md` | Generate blog post |
| `/pm.demo` | `demo-script.md` | Generate demo script |

---

## Document Relationships

```
memory/constitution.md (product principles - referenced by all PRDs)
    ↓
prds/[###-feature-name]/
├── feature-overview.md   ← Created by /pm.specify
├── prd.md                ← Created by /pm.prd (incorporates feature-overview)
├── clarifications.md     ← Created by /pm.clarify (session log)
├── ado-workitems.md      ← Created by /pm.tasks (parses prd.md)
├── documentation.md      ← Created by /pm.docs (from prd.md)
├── blog.md               ← Created by /pm.blog (from prd.md)
└── demo-script.md        ← Created by /pm.demo (from prd.md)
```

---

## Iteration Model

When PRD content changes:

1. Update `feature-overview.md` or `prd.md` directly, OR
2. Run `/pm.clarify` to add new clarifications
3. Run `/pm.tasks` to regenerate work items
4. Run `/pm.analyze` to validate consistency
5. Regenerate downstream artifacts (`/pm.docs`, `/pm.blog`, `/pm.demo`) as needed

**Source of Truth**: `prd.md` is the authoritative document. All other artifacts are derived from it.

---

## Future Capabilities (Not in Scope)

- `/pm.roadmap` - Multi-feature release planning
- JSON export for Azure DevOps API import
- Git-based version tracking for PRDs
- Stakeholder approval workflow integration

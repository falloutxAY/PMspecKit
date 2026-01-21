# PM Speckit Design

> **Purpose**: This document describes the architecture, command flow, and template relationships for PM Speckit. It serves as the technical reference for AI agents extending or modifying PM Speckit.

---

## Architecture Overview

PM Speckit follows a **template-driven, command-based architecture** adapted from [GitHub's spec-kit](https://github.com/github/spec-kit).

### Key Components

| Component | Location | Purpose |
|-----------|----------|---------|
| Constitution | `memory/constitution.md` | Product principles governing all PRDs |
| Templates | `templates/*.md` | Output format definitions |
| Command Templates | `templates/commands/*.md` | AI agent instructions for each command |
| Checklists | `templates/checklists/*.md` | Validation checklists |
| Generated PRDs | `prds/[###-feature-name]/` | Per-feature document folders |

---

## Command Template Structure

Each command template in `templates/commands/` follows this structure:

```markdown
---
description: Brief description of the command
handoffs:
  - agent: next-command (optional)
    prompt: Instructions for chaining
---

# /pm.[command-name]

## User Input

$ARGUMENTS

## Outline

1. Step one
2. Step two
3. ...

## Rules

- Constraint one
- Constraint two
```

### YAML Frontmatter

| Field | Required | Description |
|-------|----------|-------------|
| `description` | Yes | One-line command description |
| `handoffs` | No | Array of follow-up command suggestions |
| `handoffs[].agent` | Yes (if handoffs) | Next command to suggest |
| `handoffs[].prompt` | Yes (if handoffs) | Context for the handoff |

### Sections

| Section | Purpose |
|---------|---------|
| `## User Input` | Placeholder for command arguments (`$ARGUMENTS`) |
| `## Outline` | Numbered steps the AI agent follows |
| `## Rules` | Constraints and validation criteria |
| `## Template Reference` | Link to output template (if applicable) |

---

## Command Flow

```
┌─────────────────┐
│ /pm.constitution │ ← First-time setup
└────────┬────────┘
         ↓
┌─────────────────┐     ┌──────────────┐
│   /pm.specify   │────→│  /pm.clarify │ (if [NEEDS CLARIFICATION])
└────────┬────────┘     └──────┬───────┘
         ↓                     │
┌─────────────────┐←───────────┘
│    /pm.prd      │────→ /pm.clarify (if needed)
└────────┬────────┘
         ↓
┌─────────────────┐
│   /pm.tasks     │ → Generates ado-workitems.md
└────────┬────────┘
         ↓
┌─────────────────┐
│  /pm.workback   │ → Generates workback-schedule.md
└────────┬────────┘    (Uses work items to estimate timeline)
         ↓
┌─────────────────┐
│   /pm.analyze   │ ← Consistency validation (READ-ONLY)
└────────┬────────┘
         ↓
┌─────────────────┐
│ /pm.peer-review │ ← Senior PM review (REQUIRES DIFFERENT AGENT)
└────────┬────────┘
         ↓
┌─────────────────────────────────────┐
│  /pm.docs  │  /pm.blog  │  /pm.demo │ ← Supporting artifacts
└─────────────────────────────────────┘
```

### Command Dependencies

| Command | Requires | Creates |
|---------|----------|---------|
| `/pm.constitution` | Nothing | `memory/constitution.md` |
| `/pm.specify` | Constitution (recommended) | `prds/###-name/feature-overview.md` |
| `/pm.prd` | `feature-overview.md` | `prds/###-name/prd.md` |
| `/pm.clarify` | Source document with `[NEEDS CLARIFICATION]` | `clarifications.md` + updates source |
| `/pm.decision` | Any approved PRD documents | `prds/###-name/decisions.md` |
| `/pm.tasks` | `prd.md` | `prds/###-name/ado-workitems.md` |
| `/pm.workback` | `prd.md` (for target date) | `prds/###-name/workback-schedule.md` |
| `/pm.analyze` | Any PRD documents | Console report (no files) |
| `/pm.peer-review` | Any PRD documents + different agent | `prds/###-name/peer-review.md` |
| `/pm.docs` | `prd.md` | `prds/###-name/documentation.md` |
| `/pm.blog` | `prd.md` | `prds/###-name/blog.md` |
| `/pm.demo` | `prd.md` | `prds/###-name/demo-script.md` |

---

## Template Hierarchy

### Output Templates (`templates/`)

| Template | Used By | Output File |
|----------|---------|-------------|
| `feature-overview.md` | `/pm.specify` | `feature-overview.md` |
| `prd.md` | `/pm.prd` | `prd.md` |
| `decisions.md` | `/pm.decision` | `decisions.md` |
| `ado-workitems.md` | `/pm.tasks` | `ado-workitems.md` |
| `workback-schedule.md` | `/pm.workback` | `workback-schedule.md` |
| `documentation.md` | `/pm.docs` | `documentation.md` |
| `blog.md` | `/pm.blog` | `blog.md` |
| `demo-script.md` | `/pm.demo` | `demo-script.md` |

### Template Placeholders

Templates use these placeholder conventions:

| Placeholder | Description |
|-------------|-------------|
| `[Feature Name]` | Name of the feature |
| `[YYYY-MM-DD]` | Current date |
| `[NEEDS CLARIFICATION: question]` | Ambiguity marker requiring resolution |
| `REQ-001`, `REQ-002` | Requirement IDs (auto-increment) |
| `US-001`, `US-002` | User Story IDs (auto-increment) |
| `DEC-001`, `DEC-002` | Decision IDs (auto-increment) |
| `EPIC-001`, `FEAT-001`, `TASK-001` | Work item IDs |

---

## Clarification Marker System

### Format

```markdown
[NEEDS CLARIFICATION: Specific question about the ambiguity]
```

### Rules

1. Maximum 3 markers per document
2. Markers must contain actionable questions
3. `/pm.clarify` processes markers one at a time
4. Resolved markers are replaced with actual content
5. Session log in `clarifications.md` preserves Q&A history

### Clarification Session Format

```markdown
## Session [YYYY-MM-DD HH:MM]

### Question
[The clarification question]

### Context
[Why this matters, what depends on it]

### Recommendation
[Suggested answer with rationale]

### Answer
[Stakeholder's actual answer]

### Applied To
[Section updated in source document]
```

---

## Azure DevOps Work Item Format

### Hierarchy

```
EPIC-001: [Epic Title]
├── FEAT-001: [Feature Title]
│   ├── TASK-001: [Task Title]
│   ├── TASK-002: [Task Title]
│   └── TASK-003: [Task Title]
└── FEAT-002: [Feature Title]
    └── ...
```

### Work Item Fields

| Field | Mapped From |
|-------|-------------|
| Title | Requirement/User Story title |
| Description | PRD requirement description |
| Acceptance Criteria | User Story acceptance criteria |
| Tags | Feature name, PRD reference |
| Links | `prds/###-name/prd.md#section` |

---

## Cross-Document Traceability

### Reference Format

Documents reference each other using relative paths:

```markdown
**Source**: [prd.md](./prd.md#requirements)
**Constitution**: [constitution.md](../../memory/constitution.md)
```

### Traceability Matrix (in `/pm.analyze` output)

| Requirement | User Story | Work Item | Status |
|-------------|------------|-----------|--------|
| REQ-001 | US-001 | TASK-001 | ✓ Covered |
| REQ-002 | US-002 | - | ⚠ No work item |

---

## Analyze Command Validation Rules

### Checks Performed

| Check | Severity | Description |
|-------|----------|-------------|
| Constitution Alignment | CRITICAL | PRD violates MUST principles |
| Unresolved Clarifications | HIGH | `[NEEDS CLARIFICATION]` markers remain |
| Unapplied Decisions | HIGH | Approved decisions in `decisions.md` not reflected in docs |
| Missing Work Items | HIGH | Requirements without corresponding tasks |
| Ambiguous Language | MEDIUM | Vague terms without measurable criteria |
| Stale Decisions | MEDIUM | Decisions in Proposed status > 7 days |
| Duplicate Requirements | MEDIUM | Near-duplicate REQ entries |
| Orphan Work Items | LOW | Tasks not mapped to requirements |

### Advisory Sections (No Severity)

| Section | Purpose |
|---------|---------||
| Devil's Advocate | Challenge 3 key assumptions, surface uncomfortable questions |
| Pre-Mortem | "It failed—why?" Generate 3-5 plausible failure scenarios |
| Stakeholder Stress Test | Evaluate from skeptical eng lead, cost-conscious exec, frustrated user |

### Output Format

```markdown
## PM Speckit Analysis Report

**Feature**: [###-feature-name]
**Date**: [YYYY-MM-DD]
**Status**: [PASS / FAIL]

### Findings

| Severity | Check | Location | Details |
|----------|-------|----------|---------|
| CRITICAL | ... | ... | ... |

### Coverage Summary

- Requirements: X/Y covered (Z%)
- User Stories: X/Y with acceptance criteria
- Work Items: X total (Y Epics, Z Features, W Tasks)

### Recommendations

1. ...
2. ...
```

---

## Extension Points

### Adding a New Command

1. Create command template in `templates/commands/[command-name].md`
2. Create output template in `templates/[output-name].md` (if needed)
3. Update `docs/requirements.md` with new capability
4. Update this design doc with command flow changes

### Modifying Templates

1. Edit template directly in `templates/`
2. All future outputs will use the new format
3. Existing documents are not auto-migrated

### Adding Checklists

1. Create checklist in `templates/checklists/[checklist-name].md`
2. Reference from relevant command templates

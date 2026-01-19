---
description: Generate Azure DevOps work items (Epics, Features, Tasks) from PRD
handoffs:
  - agent: /pm.analyze
    prompt: Validate consistency before importing work items to Azure DevOps
  - agent: /pm.docs
    prompt: Generate user documentation for this feature
---

# /pm.tasks

## User Input

$ARGUMENTS

## Outline

1. **Locate PRD**
   - Accept feature number, name, or path
   - Verify `prd.md` exists in the feature folder
   - Check for unresolved `[NEEDS CLARIFICATION]` markers (warn if found)

2. **Parse PRD structure**
   - Extract user stories (US-###)
   - Extract functional requirements (REQ-###)
   - Extract non-functional requirements (NFR-###)
   - Extract acceptance criteria

3. **Design work item hierarchy**
   - Group related requirements into Epics (high-level capabilities)
   - Break Epics into Features (specific deliverables)
   - Break Features into Tasks (actionable work items)

4. **Generate Epic definitions**
   - Title: High-level capability name
   - Description: Business value and scope
   - Acceptance criteria from related requirements
   - Link to PRD source

5. **Generate Feature definitions**
   - Title: Specific capability
   - Parent Epic reference
   - Map to user stories (US-###)
   - Acceptance criteria in Given/When/Then format
   - Story point estimate (if available)

6. **Generate Task definitions**
   - Title: Actionable, specific work item
   - Parent Feature reference
   - Description from requirement details
   - Original estimate (if available)
   - Link to specific PRD section

7. **Create traceability matrix**
   - Map: Requirement → User Story → Feature → Tasks
   - Identify coverage gaps (requirements without tasks)
   - Flag orphan tasks (tasks without requirements)

8. **Generate work items document**
   - Create `prds/[###]-[feature-name]/ado-workitems.md`
   - Use the ado-workitems template
   - Include hierarchy visualization

9. **Provide import instructions**
   - Copy-paste format for manual import
   - CSV format for bulk import (included in doc)

10. **Suggest next steps**
    - Run `/pm.analyze` to validate before import
    - Import to Azure DevOps
    - Generate supporting docs with `/pm.docs`

## Rules

- Every requirement MUST map to at least one work item
- Work item titles must be actionable and specific
- Acceptance criteria must be testable
- Include links back to PRD sections
- Use consistent ID format: EPIC-###, FEAT-###, TASK-###
- Estimate in hours for tasks, story points for features

## Work Item Field Mapping

| PRD Element | Azure DevOps Field |
|-------------|-------------------|
| Requirement description | Description |
| User story acceptance criteria | Acceptance Criteria |
| Priority (P0/P1/P2/P3) | Priority (1/2/3/4) |
| Feature name | Tags |
| PRD reference | Hyperlink |

## Hierarchy Guidelines

```
EPIC: Major capability (maps to multiple user stories)
├── FEATURE: Specific deliverable (maps to 1-2 user stories)
│   ├── TASK: Single work item (1-16 hours)
│   └── TASK: Single work item
└── FEATURE: Another deliverable
    └── TASK: Single work item
```

## Task Sizing

| Size | Hours | Description |
|------|-------|-------------|
| XS | 1-2 | Trivial change, obvious implementation |
| S | 2-4 | Small, well-defined task |
| M | 4-8 | Moderate complexity, single day |
| L | 8-16 | Complex, may need breakdown |
| XL | 16+ | Too large - should be split |

## Example Interaction

**User**: `/pm.tasks 001`

**Agent**: "I'll generate Azure DevOps work items from `prds/001-ai-code-review/prd.md`.

Analyzing the PRD structure:
- Found 5 user stories (US-001 to US-005)
- Found 12 functional requirements
- Found 4 non-functional requirements

I'll organize these into the following hierarchy:

```
EPIC-001: AI-Powered Code Review
├── FEAT-001: Automated Code Analysis (US-001, US-002)
│   ├── TASK-001: Implement code parser
│   ├── TASK-002: Integrate AI model
│   └── TASK-003: Build suggestion UI
├── FEAT-002: Review Dashboard (US-003)
│   └── ...
```

Does this hierarchy make sense, or would you like to adjust the grouping?"

[Continue generating ado-workitems.md]

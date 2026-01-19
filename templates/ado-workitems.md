# Azure DevOps Work Items: [Feature Name]

> **Purpose**: Structured work item definitions for Azure DevOps import. Copy-paste ready format with Epic, Feature, and Task hierarchy.

---

## Metadata

| Field | Value |
|-------|-------|
| **Feature ID** | [###] |
| **Source PRD** | [./prd.md](./prd.md) |
| **Generated** | [YYYY-MM-DD] |
| **Area Path** | [Team\Area] |
| **Iteration Path** | [Sprint/Release] |

---

## Work Item Hierarchy

```
EPIC-001: [Epic Title]
├── FEAT-001: [Feature Title]
│   ├── TASK-001: [Task Title]
│   ├── TASK-002: [Task Title]
│   └── TASK-003: [Task Title]
├── FEAT-002: [Feature Title]
│   ├── TASK-004: [Task Title]
│   └── TASK-005: [Task Title]
└── FEAT-003: [Feature Title]
    └── TASK-006: [Task Title]
```

---

## Epics

### EPIC-001: [Epic Title]

| Field | Value |
|-------|-------|
| **Type** | Epic |
| **Title** | [Epic title - high-level capability] |
| **State** | New |
| **Area Path** | [Team\Area] |
| **Iteration Path** | [Release] |
| **Priority** | 1 / 2 / 3 / 4 |
| **Tags** | [feature-name], [prd-###] |

**Description**:

[High-level description of the epic. What business value does it deliver?]

**Acceptance Criteria**:

- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

**Links**:
- PRD: [./prd.md](./prd.md)
- Related Goals: G-001, G-002

---

## Features

### FEAT-001: [Feature Title]

| Field | Value |
|-------|-------|
| **Type** | Feature |
| **Title** | [Feature title - specific capability] |
| **Parent** | EPIC-001 |
| **State** | New |
| **Priority** | 1 / 2 / 3 / 4 |
| **Story Points** | [Estimate] |
| **Tags** | [feature-name], [prd-###] |

**Description**:

[Description of the feature. What does it enable?]

Maps to:
- User Story: US-001
- Requirements: REQ-001, REQ-002

**Acceptance Criteria**:

- [ ] Given [context], when [action], then [expected result]
- [ ] Given [context], when [action], then [expected result]

**Links**:
- PRD Section: [./prd.md#user-stories](./prd.md#user-stories)

---

### FEAT-002: [Feature Title]

| Field | Value |
|-------|-------|
| **Type** | Feature |
| **Title** | [Feature title] |
| **Parent** | EPIC-001 |
| **State** | New |
| **Priority** | 1 / 2 / 3 / 4 |
| **Story Points** | [Estimate] |
| **Tags** | [feature-name], [prd-###] |

**Description**:

[Description]

Maps to:
- User Story: US-002
- Requirements: REQ-003

**Acceptance Criteria**:

- [ ] [Criterion]

---

## Tasks

### TASK-001: [Task Title]

| Field | Value |
|-------|-------|
| **Type** | Task |
| **Title** | [Specific, actionable task] |
| **Parent** | FEAT-001 |
| **State** | New |
| **Priority** | 1 / 2 / 3 / 4 |
| **Original Estimate** | [Hours] |
| **Assigned To** | [Optional] |
| **Tags** | [feature-name] |

**Description**:

[Detailed task description. What needs to be done?]

**Acceptance Criteria**:

- [ ] [Specific completion criterion]

**Links**:
- Requirement: REQ-001

---

### TASK-002: [Task Title]

| Field | Value |
|-------|-------|
| **Type** | Task |
| **Title** | [Specific, actionable task] |
| **Parent** | FEAT-001 |
| **State** | New |
| **Priority** | 1 / 2 / 3 / 4 |
| **Original Estimate** | [Hours] |
| **Tags** | [feature-name] |

**Description**:

[Description]

**Acceptance Criteria**:

- [ ] [Criterion]

---

### TASK-003: [Task Title]

| Field | Value |
|-------|-------|
| **Type** | Task |
| **Title** | [Specific, actionable task] |
| **Parent** | FEAT-001 |
| **State** | New |
| **Priority** | 1 / 2 / 3 / 4 |
| **Original Estimate** | [Hours] |
| **Tags** | [feature-name] |

**Description**:

[Description]

**Acceptance Criteria**:

- [ ] [Criterion]

---

## Traceability Matrix

| Requirement | User Story | Feature | Tasks | Status |
|-------------|------------|---------|-------|--------|
| REQ-001 | US-001 | FEAT-001 | TASK-001, TASK-002 | ✓ Covered |
| REQ-002 | US-001 | FEAT-001 | TASK-003 | ✓ Covered |
| REQ-003 | US-002 | FEAT-002 | TASK-004, TASK-005 | ✓ Covered |

---

## Import Instructions

### Manual Import (Copy-Paste)

1. Open Azure DevOps > Boards > Work Items
2. Click "New Work Item" > Select type (Epic/Feature/Task)
3. Copy fields from the tables above
4. Set parent relationships manually

### Bulk Import (CSV)

Export this data to CSV format for bulk import:

```csv
Work Item Type,Title,Description,Acceptance Criteria,Parent,Priority,Tags
Epic,[Title],[Description],[Criteria],,1,[Tags]
Feature,[Title],[Description],[Criteria],EPIC-001,1,[Tags]
Task,[Title],[Description],[Criteria],FEAT-001,2,[Tags]
```

### Future: API Import

[JSON format for Azure DevOps REST API - planned for future release]

---

## Notes

- All work items link back to the source PRD for traceability
- Update this document when PRD requirements change, then regenerate
- Run `/pm.analyze` to verify coverage before import

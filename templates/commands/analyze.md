---
description: Validate cross-document consistency (READ-ONLY analysis)
handoffs:
  - agent: /pm.clarify
    prompt: Resolve issues found during analysis
  - agent: /pm.tasks
    prompt: Regenerate work items after fixing issues
---

# /pm.analyze

## User Input

$ARGUMENTS

## Outline

1. **Locate feature documents**
   - Accept feature number, name, or path
   - Identify all documents in the feature folder
   - Report which documents exist

2. **Load constitution**
   - Read `memory/constitution.md` if it exists
   - Extract MUST, SHOULD, and AVOID principles

3. **Perform constitution alignment check**
   - Scan PRD for violations of MUST principles
   - Check for conflicts with AVOID principles
   - Report: CRITICAL for MUST violations, HIGH for AVOID violations

4. **Check for unresolved clarifications**
   - Scan all documents for `[NEEDS CLARIFICATION]` markers
   - Report: HIGH severity for unresolved markers

5. **Detect ambiguous language**
   - Flag vague adjectives without measurable criteria
   - Examples: "fast", "scalable", "user-friendly", "intuitive"
   - Report: MEDIUM severity

6. **Check requirement coverage**
   - Verify all requirements (REQ-###) have work items
   - Verify all user stories have acceptance criteria
   - Report: HIGH for missing work items, MEDIUM for missing criteria

7. **Detect duplicates**
   - Find near-duplicate requirements
   - Find overlapping user stories
   - Report: MEDIUM severity

8. **Verify traceability**
   - Check: Requirements → User Stories → Work Items
   - Identify orphan work items (no requirement mapping)
   - Identify dead requirements (no user story mapping)
   - Report: LOW for orphans, MEDIUM for dead requirements

9. **Check ID consistency**
   - Verify IDs are sequential and unique
   - Check for gaps in sequences
   - Report: LOW severity for gaps

10. **Generate analysis report**
    - Summarize findings by severity
    - Provide coverage statistics
    - List specific recommendations
    - Output to console (no file created)

11. **Suggest next steps**
    - If CRITICAL issues: must fix before proceeding
    - If HIGH issues: strongly recommend fixing
    - If only MEDIUM/LOW: can proceed with awareness

## Rules

- This is a READ-ONLY operation - no files are modified
- Constitution MUST violations are always CRITICAL
- Unresolved clarification markers are always HIGH
- Report must be actionable with specific locations
- Don't report style issues, focus on consistency and completeness

## Severity Levels

| Severity | Description | Action Required |
|----------|-------------|-----------------|
| CRITICAL | Constitution violation, blocker | Must fix before proceeding |
| HIGH | Missing critical content | Should fix before stakeholder review |
| MEDIUM | Quality issue, potential confusion | Fix when possible |
| LOW | Minor issue, style | Nice to fix |

## Checks Performed

| Check | Severity | Description |
|-------|----------|-------------|
| Constitution MUST violation | CRITICAL | PRD conflicts with non-negotiable principle |
| Constitution AVOID violation | HIGH | PRD includes an anti-pattern |
| Unresolved clarification | HIGH | `[NEEDS CLARIFICATION]` marker present |
| Missing work items | HIGH | Requirement has no corresponding task |
| Missing acceptance criteria | MEDIUM | User story lacks Given/When/Then |
| Ambiguous language | MEDIUM | Vague terms without measurable definition |
| Duplicate requirements | MEDIUM | Near-identical REQ entries |
| Orphan work items | LOW | Task not mapped to requirement |
| ID sequence gaps | LOW | Missing number in sequence |

## Report Format

```markdown
## PM Speckit Analysis Report

**Feature**: [###]-[feature-name]
**Date**: [YYYY-MM-DD]
**Status**: PASS / FAIL

### Summary

| Severity | Count |
|----------|-------|
| CRITICAL | X |
| HIGH | X |
| MEDIUM | X |
| LOW | X |

### Findings

| # | Severity | Check | Location | Details | Recommendation |
|---|----------|-------|----------|---------|----------------|
| 1 | CRITICAL | ... | prd.md#section | ... | ... |
| 2 | HIGH | ... | ... | ... | ... |

### Coverage Summary

- Requirements: X/Y with work items (Z%)
- User Stories: X/Y with acceptance criteria
- Work Items: X total (Y Epics, Z Features, W Tasks)

### Traceability

| Requirement | User Story | Work Item | Status |
|-------------|------------|-----------|--------|
| REQ-001 | US-001 | TASK-001 | ✓ |
| REQ-002 | - | - | ⚠ No mapping |

### Recommendations

1. [Priority 1 action]
2. [Priority 2 action]
3. [Priority 3 action]
```

## Example Interaction

**User**: `/pm.analyze 001`

**Agent**: "Analyzing feature 001 (AI-powered code review)...

## PM Speckit Analysis Report

**Feature**: 001-ai-code-review
**Date**: 2026-01-19
**Status**: FAIL (1 CRITICAL, 2 HIGH issues)

### Summary

| Severity | Count |
|----------|-------|
| CRITICAL | 1 |
| HIGH | 2 |
| MEDIUM | 3 |
| LOW | 1 |

### Findings

| # | Severity | Check | Location | Details | Recommendation |
|---|----------|-------|----------|---------|----------------|
| 1 | CRITICAL | Constitution MUST | prd.md#requirements | REQ-003 stores user data without encryption, violates MUST-001 | Add encryption requirement or remove feature |
| 2 | HIGH | Unresolved clarification | prd.md#success-metrics | [NEEDS CLARIFICATION: What is the target response time?] | Run /pm.clarify |
| 3 | HIGH | Missing work items | prd.md#requirements | REQ-007 has no task in ado-workitems.md | Run /pm.tasks to regenerate |

...

**Recommendation**: Fix CRITICAL issue #1 before proceeding. Run `/pm.clarify` to resolve issue #2."

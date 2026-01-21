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
   - Check git diff or recent modified files and make sure to update all relevant files to align with the changes. 
  
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

10. **Review decision log (if exists)**
    - Check `decisions.md` for unresolved (Proposed) decisions
    - Verify affected documents reflect approved decisions
    - Flag superseded decisions that weren't applied
    - Report: HIGH for unapplied decisions, MEDIUM for stale entries

11. **Devil's Advocate Challenge**
    - Adopt the persona of a skeptical stakeholder
    - Challenge 3 key assumptions in the PRD:
      - "What if [assumption] is wrong?"
      - "What evidence do we have for [claim]?"
      - "Who loses if we ship this?"
    - Surface uncomfortable questions the PM might be avoiding
    - Report: No severity (advisory section)

12. **Pre-Mortem Analysis**
    - "It's 6 months after launch. This feature failed. Why?"
    - Generate 3-5 plausible failure scenarios:
      - Technical: What could break?
      - Adoption: Why might users reject this?
      - Business: What market/competitive shifts could undermine this?
      - Execution: What could go wrong in delivery?
    - For each scenario: likelihood (High/Med/Low) and mitigation
    - Report: No severity (advisory section)

13. **Stakeholder Stress Test**
    - Evaluate PRD from adversarial perspectives:
      - **Skeptical Engineering Lead**: "Is this technically feasible? What's underestimated?"
      - **Cost-Conscious Executive**: "Is the ROI justified? What's the opportunity cost?"
      - **Frustrated End User**: "Does this actually solve my problem? What's missing?"
    - Surface potential objections before they arise in reviews
    - Report: No severity (advisory section)

14. **Generate analysis report**
    - Summarize findings by severity
    - Provide coverage statistics
    - Include Devil's Advocate, Pre-Mortem, and Stress Test sections
    - List specific recommendations
    - Output to console (no file created)

15. **Suggest next steps**
    - If CRITICAL issues: must fix before proceeding
    - If HIGH issues: strongly recommend fixing
    - If only MEDIUM/LOW: can proceed with awareness
    - If Pre-Mortem reveals high-likelihood risks: recommend adding mitigations to PRD

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
| Unapplied decision | HIGH | Approved decision not reflected in docs |
| Stale decision log | MEDIUM | Decision marked Proposed for > 7 days |

## Advisory Sections (No Severity)

These sections don't block progress but surface risks and blind spots:

| Section | Purpose |
|---------|---------|
| Devil's Advocate | Challenge assumptions, surface uncomfortable questions |
| Pre-Mortem | Anticipate failure modes before they happen |
| Stakeholder Stress Test | Preview objections from different perspectives |

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

---

### 😈 Devil's Advocate

> *Challenging assumptions you might be avoiding*

| Assumption | Challenge | Evidence Gap |
|------------|-----------|--------------|
| [Key assumption from PRD] | What if this is wrong? | [What data would disprove this?] |
| [Key assumption from PRD] | What if this is wrong? | [What data would disprove this?] |
| [Key assumption from PRD] | What if this is wrong? | [What data would disprove this?] |

**Uncomfortable Questions**:
1. [Question the PM might not want to answer]
2. [Question that challenges the core value prop]
3. [Question about who might be harmed]

---

### 💀 Pre-Mortem: Why This Could Fail

> *It's 6 months post-launch. This feature failed. Here's why:*

| Failure Scenario | Category | Likelihood | Potential Mitigation |
|------------------|----------|------------|---------------------|
| [Scenario 1] | Technical / Adoption / Business / Execution | High/Med/Low | [What could prevent this] |
| [Scenario 2] | Technical / Adoption / Business / Execution | High/Med/Low | [What could prevent this] |
| [Scenario 3] | Technical / Adoption / Business / Execution | High/Med/Low | [What could prevent this] |

**Highest Risk**: [The most likely failure mode and why it's concerning]

---

### 🎭 Stakeholder Stress Test

**Skeptical Engineering Lead** 🔧
> "[Specific objection about technical feasibility, timeline, or hidden complexity]"

**Cost-Conscious Executive** 💰
> "[Specific objection about ROI, resource allocation, or opportunity cost]"

**Frustrated End User** 😤
> "[Specific objection about whether this actually solves their real problem]"

**Mitigation Notes**: [How to address these objections proactively]
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

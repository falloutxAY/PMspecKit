---
description: Create a full PRD with complete requirements, user stories, and success criteria
handoffs:
  - agent: /pm.clarify
    prompt: Resolve any [NEEDS CLARIFICATION] markers in the PRD
  - agent: /pm.tasks
    prompt: Generate Azure DevOps work items from the PRD
---

# /pm.prd

## User Input

$ARGUMENTS

## Outline

1. **Locate feature folder**
   - Find the feature folder in `prds/`
   - Can be specified by number (e.g., `001`) or name
   - Verify `feature-overview.md` exists

2. **Incorporate feature overview**
   - Read `feature-overview.md` content
   - Auto-incorporate problem statement, solution summary, scope
   - Preserve any resolved clarifications

3. **Check for unresolved clarifications**
   - Scan for `[NEEDS CLARIFICATION]` markers
   - If found, suggest running `/pm.clarify` first
   - Can proceed if user confirms

4. **Expand executive summary**
   - 2-3 paragraphs for executive stakeholders
   - Cover: problem, solution, business impact, timeline

5. **Define goals and non-goals**
   - Goals with measurable success metrics
   - Non-goals with explicit rationale

6. **Write user stories**
   - Format: "As a [user], I want [goal] so that [benefit]"
   - Each story needs:
     - Priority (P0/P1/P2/P3)
     - Acceptance criteria (Given/When/Then)
     - Unique ID (US-001, US-002, etc.)

7. **Document requirements**
   - Functional requirements with IDs (REQ-001, etc.)
   - Map each requirement to a user story
   - Non-functional requirements (performance, security, accessibility)

8. **Capture UX considerations**
   - User flow diagram (text-based)
   - Links to wireframes/mockups (if available)
   - Key interaction patterns

9. **Define success metrics**
   - Specific, measurable metrics with baselines and targets
   - Timeline for measurement
   - Owner for each metric

10. **Document risks and dependencies**
    - Risks with likelihood, impact, and mitigation
    - Dependencies with type, owner, and status

11. **Outline timeline**
    - Key milestones with target dates
    - Dependencies between milestones

12. **Add launch considerations**
    - Rollout strategy
    - Documentation needs
    - Support readiness
    - Communication plan

13. **Validate constitution alignment**
    - Check against MUST principles in `memory/constitution.md`
    - Flag any potential violations
    - Include constitution alignment checklist

14. **Generate PRD**
    - Create `prds/[###]-[feature-name]/prd.md`
    - Use the prd template
    - Initialize version history

15. **Suggest next steps**
    - If clarifications remain: `/pm.clarify`
    - If ready for work items: `/pm.tasks`
    - If ready for review: `/pm.analyze`

## Rules

- PRD is the authoritative source of truth
- All requirements MUST have unique IDs (REQ-001 format)
- All user stories MUST have acceptance criteria
- Success metrics MUST be measurable with specific targets
- Reference constitution for alignment validation
- Do NOT include implementation details (that's for engineering)
- Each requirement maps to at least one user story

## Template Reference

Use template: `templates/prd.md`

## Requirement ID Conventions

| Type | Format | Example |
|------|--------|---------|
| User Story | US-### | US-001 |
| Functional Requirement | REQ-### | REQ-001 |
| Non-Functional Requirement | NFR-### | NFR-001 |
| Goal | G-### | G-001 |
| Non-Goal | NG-### | NG-001 |
| Risk | R-### | R-001 |
| Dependency | D-### | D-001 |
| Success Metric | SM-### | SM-001 |

## Example Interaction

**User**: `/pm.prd 001`

**Agent**: "I'll create a full PRD for feature 001 (AI-powered code review). I found the feature overview at `prds/001-ai-code-review/feature-overview.md`.

I'll incorporate the existing context and expand it into a complete PRD. Let me start by confirming the user stories...

Who are the primary user types for this feature?"

[Continue expanding into full PRD]

---
description: Create a lightweight feature overview for scoping and estimation
handoffs:
  - agent: /pm.clarify
    prompt: Resolve any [NEEDS CLARIFICATION] markers in the feature overview
  - agent: /pm.prd
    prompt: Expand the feature overview into a full PRD
---

# /pm.specify

## User Input

$ARGUMENTS

## Outline

1. **Determine feature folder**
   - Check existing folders in `prds/` directory
   - Assign next sequential number (001, 002, etc.)
   - Create folder: `prds/[###]-[feature-name]/`

2. **Gather problem context**
   - What problem are we solving?
   - Why is this important now?
   - What evidence supports this (customer feedback, data, research)?

3. **Define proposed solution**
   - High-level summary (2-3 sentences)
   - Key capabilities with priorities (P0/P1/P2)
   - Simple user flow (3-5 steps)

4. **Establish scope boundaries**
   - What's explicitly IN scope
   - What's explicitly OUT of scope
   - Key dependencies (blocking and informational)

5. **Identify success indicators**
   - How will we know this succeeded?
   - Current baseline vs. target metrics

6. **Flag open questions**
   - List questions requiring stakeholder input
   - Add `[NEEDS CLARIFICATION: question]` markers (max 3)

7. **Capture risks**
   - Key risks with likelihood and impact
   - Initial mitigation thoughts

8. **Generate feature overview**
   - Create `prds/[###]-[feature-name]/feature-overview.md`
   - Use the feature-overview template
   - Estimate size: S/M/L/XL

9. **Check constitution alignment**
   - Reference `memory/constitution.md` if it exists
   - Flag any potential conflicts with MUST principles

10. **Suggest next steps**
    - If clarifications needed: suggest `/pm.clarify`
    - If ready for full PRD: suggest `/pm.prd`

## Rules

- Keep it lightweight - this is for scoping, not full specification
- Maximum 3 `[NEEDS CLARIFICATION]` markers per document
- Focus on WHAT and WHY, not HOW
- Success indicators must be measurable, not vague
- Feature name should be descriptive but concise (2-4 words)
- Document should be reviewable in 30 minutes or less

## Template Reference

Use template: `templates/feature-overview.md`

## Clarification Markers

When information is ambiguous or missing, insert markers:

```markdown
[NEEDS CLARIFICATION: What user segment is the primary target for this feature?]
```

These will be resolved by `/pm.clarify` before proceeding to full PRD.

## Example Interaction

**User**: `/pm.specify AI-powered code review`

**Agent**: "I'll create a feature overview for AI-powered code review. Let me gather some context.

What problem is this solving? Who experiences this problem and when?"

**User**: "Developers spend too much time on manual code reviews. Senior devs are bottlenecked."

**Agent**: "Got it. What evidence do you have for this problem? Customer feedback, internal data, research?"

[Continue gathering context, then generate feature-overview.md]

## Next Steps

Always conclude with contextual next steps based on feature overview state:

- **If [NEEDS CLARIFICATION] markers present** → "Run `/pm.clarify` to resolve open questions before expanding to full PRD"
- **If feature overview is complete** → "Ready to expand into full PRD with `/pm.prd`"
- **If no constitution exists** → "Consider running `/pm.constitution` first to establish product principles"
- **If scope is unclear** → "Gather more stakeholder input before proceeding"

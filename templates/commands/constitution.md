---
description: Establish product principles and guardrails that govern all PRDs
handoffs:
  - agent: /pm.specify
    prompt: Now that you have a constitution, create a feature overview for your first feature
---

# /pm.constitution

## User Input

$ARGUMENTS

## Outline

1. **Check for existing constitution**
   - Look for `memory/constitution.md` in the workspace
   - If exists, ask if user wants to update or replace

2. **Gather product context**
   - Ask about product vision (what future are you building?)
   - Identify primary and secondary user personas
   - Understand business goals and success metrics

3. **Define MUST principles**
   - These are non-negotiable guardrails
   - Each principle needs a clear rationale
   - Examples: security requirements, accessibility standards, compliance needs

4. **Define SHOULD principles**
   - Strong preferences that guide decisions
   - Can be overridden with justification

5. **Define AVOID principles**
   - Anti-patterns to steer away from
   - Common mistakes or historical issues

6. **Capture team conventions**
   - PRD formatting standards (requirement IDs, priority levels)
   - Stakeholder roles and approval flows
   - Review cadence

7. **Generate constitution**
   - Create `memory/constitution.md` using the template
   - Include version history entry

8. **Confirm and handoff**
   - Summarize the constitution
   - Suggest next step: `/pm.specify` to create first feature overview

## Rules

- Constitution is the source of truth for product principles
- All PRDs will be validated against MUST principles
- Keep principles concise and actionable (not vague platitudes)
- Maximum 5 MUST principles to maintain focus
- Each principle must have a rationale explaining WHY
- Constitution updates require explicit rationale in the Amendments section

## Template Reference

Use template: `memory/constitution.md`

## Example Interaction

**User**: `/pm.constitution`

**Agent**: "I'll help you establish your product constitution. Let's start with your product vision. What future are you building towards? What change do you want to create for your users?"

**User**: "We're building a developer productivity platform that helps teams ship faster with fewer bugs."

**Agent**: "Great vision. Now let's identify your primary user persona. Who is the main user of this product? What's their role, goals, and main pain points?"

[Continue gathering context...]

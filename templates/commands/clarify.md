---
description: Resolve [NEEDS CLARIFICATION] markers through structured Q&A
handoffs:
  - agent: /pm.prd
    prompt: Continue to full PRD now that clarifications are resolved
  - agent: /pm.tasks
    prompt: Generate Azure DevOps work items now that clarifications are resolved
  - agent: /pm.decision
    prompt: Log clarification as a decision if it modifies approved content
---

# /pm.clarify

## User Input

$ARGUMENTS

## Outline

1. **Locate source document**
   - Accept feature number, name, or specific file path
   - Check both `feature-overview.md` and `prd.md` if present
   - Report which documents have clarification markers

2. **Scan for clarification markers**
   - Find all `[NEEDS CLARIFICATION: ...]` markers
   - List them with their location in the document
   - If none found, report and suggest next steps

3. **Process one clarification at a time**
   - Present the question with surrounding context
   - Explain why this matters (what depends on the answer)
   - Provide a recommendation with rationale
   - Offer options if applicable

4. **Record the answer**
   - Create or update `clarifications.md` in the feature folder
   - Add session with timestamp
   - Document: Question, Context, Recommendation, Answer, Applied To

5. **Apply clarification to source document**
   - Replace the `[NEEDS CLARIFICATION]` marker with actual content
   - Update the relevant section based on the answer
   - Preserve document structure

6. **Check for remaining markers**
   - If more markers exist, continue to next question
   - If all resolved, summarize changes made

7. **Suggest next steps**
   - If source was feature-overview: suggest `/pm.prd`
   - If source was prd.md: suggest `/pm.tasks` or `/pm.analyze`

8. **Check if decision logging needed**
   - If the source document was already in "Approved" or "In Development" status:
     - Prompt: "This clarification modifies an approved document. Would you like to log this as a formal decision?"
     - If yes: hand off to `/pm.decision` with pre-filled context
   - This ensures post-approval clarifications are tracked in `decisions.md`

## Rules

- Process ONE clarification at a time (not all at once)
- Always provide a recommendation, don't just ask open-ended questions
- Record all Q&A in `clarifications.md` for audit trail
- Immediately apply answers to source document
- Never leave a marker unresolved without explicit user decision to defer
- Maximum 5 questions per clarify session

## Question Format

When presenting a clarification, use this structure:

```markdown
### Clarification 1 of N

**Question**: [The specific question from the marker]

**Context**: [Why this matters, what sections/decisions depend on it]

**Recommendation**: [Your suggested answer with rationale]

**Options** (if applicable):
| Option | Pros | Cons |
|--------|------|------|
| A | ... | ... |
| B | ... | ... |

How would you like to proceed?
```

## Session Log Format

In `clarifications.md`:

```markdown
## Session [YYYY-MM-DD HH:MM]

### Question
[The clarification question]

### Context
[Why this matters]

### Recommendation
[What was suggested]

### Answer
[What the stakeholder decided]

### Applied To
- File: [filename]
- Section: [section name]
- Change: [brief description of update made]
```

## Example Interaction

**User**: `/pm.clarify 001`

**Agent**: "I found 2 clarification markers in `prds/001-ai-code-review/feature-overview.md`:

1. [NEEDS CLARIFICATION: What programming languages should be supported at launch?]
2. [NEEDS CLARIFICATION: Should this integrate with existing CI/CD pipelines?]

Let me address the first one:

### Clarification 1 of 2

**Question**: What programming languages should be supported at launch?

**Context**: This affects the scope and timeline. Supporting more languages increases complexity but broadens adoption. The success metrics reference 'developer productivity' which could vary by language ecosystem.

**Recommendation**: Start with the top 3 languages used by your target customers (likely JavaScript, Python, and Java based on industry data). Add more in subsequent releases.

**Options**:
| Option | Pros | Cons |
|--------|------|------|
| Top 3 only | Faster delivery, focused quality | May exclude some users |
| Top 5 | Broader adoption | More complexity, longer timeline |
| All supported | Maximum coverage | Significant scope, quality risk |

Which approach would you like to take?"

**User**: "Let's go with Top 3 - JavaScript, Python, and TypeScript."

**Agent**: "Got it. I've updated the feature overview:
- Added 'Supported Languages: JavaScript, Python, TypeScript' to the Scope section
- Recorded this decision in `clarifications.md`

Now for clarification 2 of 2..."

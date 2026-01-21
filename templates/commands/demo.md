---
description: Generate demo script and talking points from PRD
handoffs:
  - agent: /pm.docs
    prompt: Generate detailed documentation for this feature
  - agent: /pm.blog
    prompt: Create an announcement blog post for this feature
---

# /pm.demo

## User Input

$ARGUMENTS

## Outline

1. **Locate PRD**
   - Accept feature number, name, or path
   - Verify `prd.md` exists
   - Read PRD content, especially user stories and UX flow

2. **Determine demo parameters**
   - Target audience: Internal / Customers / Partners
   - Duration: Quick (5 min) / Standard (15 min) / Deep-dive (30 min)
   - Format: Live demo / Recorded / Hybrid

3. **Structure demo flow**
   - Opening & Context: Set the stage (2 min)
   - Problem Context: Why this matters (2 min)
   - Feature Walkthrough: Show the feature (varies)
   - Key Scenarios: Use case demonstrations (varies)
   - Benefits Recap: Reinforce value (1 min)
   - CTA: Next steps (1 min)
   - Q&A: Prepared answers (5 min)

4. **Map user stories to scenarios**
   - Select 2-4 most impactful user stories
   - Design demo flow for each
   - Create step-by-step walkthrough

5. **Write talking points**
   - For each step: What to DO and what to SAY
   - Highlight key UI elements
   - Connect actions to user benefits

6. **Prepare Q&A section**
   - Anticipate common questions from PRD
   - Prepare answers for objections (from risks)
   - Include "I'll follow up" guidance

7. **Add recovery scenarios**
   - What to do if demo breaks
   - Backup options (screenshots, video)
   - Grace phrases for technical issues

8. **Create pre-demo checklist**
   - Environment setup
   - Test data preparation
   - Materials ready

9. **Generate demo script**
   - Create `prds/[###]-[feature-name]/demo-script.md`
   - Use the demo-script template
   - Include timing estimates per section

10. **Provide post-demo guidance**
    - Follow-up actions
    - Feedback collection

## Rules

- Show, don't tell (minimize slides, maximize live product)
- One main message per scenario
- Plan for things going wrong
- Keep talking points conversational, not scripted word-for-word
- Include timing cues for pacing
- Always end with clear call-to-action

## Scenario Selection Criteria

| Priority | Criteria |
|----------|----------|
| 1 | Solves the primary pain point |
| 2 | Shows the "wow" moment |
| 3 | Demonstrates differentiation |
| 4 | Addresses common concern |

## Talking Point Format

```markdown
#### Step N: [Action Title]

**Do**: [Specific UI action to perform]

**Say**: 
> "[Conversational script - what to tell the audience]"

**Highlight**:
- [Key UI element to point out]
- [Benefit this demonstrates]

**Timing**: [X minutes]
```

## Q&A Preparation

| Question Type | Source | Preparation |
|---------------|--------|-------------|
| Feature scope | Non-goals | "That's not in this release, but..." |
| Technical | NFRs | Translate to user terms |
| Competitive | PRD background | Differentiation points |
| Timeline | Milestones | Be specific or defer |
| Pricing/Access | Launch plan | Clear availability info |

## Example Transformation

**PRD User Story**:
> US-001: As a developer, I want to receive AI-generated code suggestions so that I can fix issues faster.
> 
> Acceptance Criteria:
> - Given code with a bug, when AI analyzes it, then suggestions appear within 5 seconds
> - Given a suggestion, when I hover over it, then I see explanation

**Demo Scenario**:
> #### Scenario 1: Getting Your First AI Suggestion
> 
> **Context**: You've just submitted a pull request with a common bug.
> 
> **Step 1: Submit Code**
> 
> **Do**: Paste the prepared buggy code snippet into the editor
> 
> **Say**: 
> > "Here's a typical scenario. I've got some code that looks fine, but has a subtle issue. Let's submit it for review."
> 
> **Step 2: See AI Analysis**
> 
> **Do**: Point to the AI Suggestions panel as it populates
> 
> **Say**:
> > "Within seconds, the AI has analyzed the code and found something. See this highlight? Let me hover over it..."
> 
> **Step 3: Review Suggestion**
> 
> **Do**: Hover over the suggestion to show explanation
> 
> **Say**:
> > "It caught a null pointer issue and explains exactly why this is a problem. One click to accept the fix."
> 
> **Highlight**:
> - Speed of analysis (under 5 seconds)
> - Clear explanation (not just "there's a bug")
> 
> **Timing**: 3 minutes

## Example Interaction

**User**: `/pm.demo 001`

**Agent**: "I'll generate a demo script from `prds/001-ai-code-review/prd.md`.

First, let me confirm demo parameters:

**Target Audience**: Who is the primary audience for this demo?
1. Internal stakeholders (leadership, sales)
2. Customers/prospects  
3. Partners/developers
4. Mixed/general

**Duration**: How long should the demo be?
1. Quick overview (5 min)
2. Standard demo (15 min)
3. Deep-dive (30 min)"

**User**: "Customers, 15 minutes"

**Agent**: "Got it. Creating a 15-minute customer demo.

I've identified 3 key scenarios from the user stories:
1. **First AI Suggestion** (US-001) - The "aha" moment
2. **Review Dashboard** (US-003) - Daily workflow
3. **Team Analytics** (US-005) - Manager value prop

Generating `demo-script.md`...

I've included:
- Pre-demo checklist
- Detailed script with timing
- 5 anticipated Q&A items
- Recovery scenarios if demo breaks

Review the script and customize the talking points to your style."

## Next Steps

Always conclude with contextual next steps:

- **If demo script created successfully** → "Consider `/pm.docs` for detailed user documentation, or `/pm.blog` for an announcement post"
- **If demo needs more scenarios** → "Review additional user stories in the PRD and expand the script"
- **If no PRD exists yet** → "Run `/pm.prd` first to create the source PRD, then return to `/pm.demo`"

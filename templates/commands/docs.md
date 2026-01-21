---
description: Generate user-facing documentation from PRD
handoffs:
  - agent: /pm.blog
    prompt: Create an announcement blog post for this feature
  - agent: /pm.demo
    prompt: Create a demo script for this feature
---

# /pm.docs

## User Input

$ARGUMENTS

## Outline

1. **Locate PRD**
   - Accept feature number, name, or path
   - Verify `prd.md` exists
   - Read PRD content for transformation

2. **Extract user-facing content**
   - Filter out internal-only sections (risks, dependencies, stakeholders)
   - Focus on: goals, user stories, requirements, UX flow
   - Translate PM language to user language

3. **Structure documentation**
   - Overview: What is this feature? Why use it?
   - Key Benefits: Value proposition for users
   - Prerequisites: What users need before starting
   - Getting Started: Quick start steps
   - Features: Detailed capability descriptions
   - Common Tasks: How-to guides
   - Troubleshooting: Common issues and solutions
   - FAQ: Anticipated user questions

4. **Transform user stories to how-tos**
   - Convert "As a user, I want..." to "How to..."
   - Use acceptance criteria as verification steps

5. **Generate benefits from goals**
   - Translate goal metrics to user benefits
   - Focus on outcomes, not features

6. **Create FAQ from PRD**
   - Convert non-goals to "Can I do X?" questions
   - Address common concerns from risks section

7. **Generate documentation**
   - Create `prds/[###]-[feature-name]/documentation.md`
   - Use the documentation template
   - Mark sections needing manual completion

8. **Suggest next steps**
   - Review and customize generated content
   - Create `/pm.blog` for announcement
   - Create `/pm.demo` for presentations

## Rules

- Write for end users, not stakeholders
- Use second person ("you") not third person
- Keep language simple and jargon-free
- Task-oriented structure (what users want to DO)
- Include specific examples where possible
- Mark placeholder sections clearly: `[TODO: ...]`

## Content Transformation

| PRD Section | Documentation Section | Transformation |
|-------------|----------------------|----------------|
| Goals | Key Benefits | "Reduce X by Y%" → "Spend less time on X" |
| User Stories | How-To Guides | "As a user, I want..." → "How to..." |
| Requirements | Feature Descriptions | Technical requirement → User capability |
| Non-Goals | FAQ | "Not doing X" → "Can I do X? Not yet, but..." |
| Risks | Troubleshooting | Risk scenarios → "If X happens, do Y" |

## Tone Guidelines

- **Friendly but professional**: Not too casual, not too formal
- **Action-oriented**: Start sections with verbs
- **Scannable**: Use headers, bullets, tables
- **Helpful**: Anticipate user questions and problems

## Example Transformation

**PRD User Story**:
> As a developer, I want to receive AI-generated code suggestions so that I can fix issues faster.

**Documentation How-To**:
> ### How to Review AI Suggestions
> 
> When you submit code for review, the AI analyzes it and provides suggestions:
> 
> 1. Open the Review panel
> 2. Look for the AI Suggestions section
> 3. Click on any suggestion to see details
> 4. Accept or dismiss each suggestion
> 
> **Tip**: Hover over a suggestion to see why it was recommended.

## Example Interaction

**User**: `/pm.docs 001`

**Agent**: "I'll generate user documentation from `prds/001-ai-code-review/prd.md`.

Transforming PRD content for end users:
- Converting 5 user stories to how-to guides
- Creating FAQ from 3 non-goals
- Generating troubleshooting from 2 key risks

Creating `documentation.md`...

I've marked 3 sections as [TODO] that need your input:
1. [TODO: Add screenshot of main interface]
2. [TODO: Confirm support contact information]
3. [TODO: Add video tutorial link]

Would you like me to also generate a blog post (`/pm.blog`) or demo script (`/pm.demo`)?"

## Next Steps

Always conclude with contextual next steps:

- **If documentation created successfully** → "Consider `/pm.blog` for an announcement post, or `/pm.demo` for a demo script"
- **If [TODO] placeholders remain** → "Complete the placeholders (screenshots, links, etc.) before publishing"
- **If no PRD exists yet** → "Run `/pm.prd` first to create the source PRD, then return to `/pm.docs`"

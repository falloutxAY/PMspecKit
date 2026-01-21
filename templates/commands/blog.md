---
description: Generate announcement blog post from PRD
handoffs:
  - agent: /pm.docs
    prompt: Generate detailed documentation for this feature
  - agent: /pm.demo
    prompt: Create a demo script for this feature
---

# /pm.blog

## User Input

$ARGUMENTS

## Outline

1. **Locate PRD**
   - Accept feature number, name, or path
   - Verify `prd.md` exists
   - Read PRD content for transformation

2. **Extract blog-worthy content**
   - Problem statement → The Challenge section
   - Solution summary → Introducing [Feature] section
   - Key capabilities → Benefits breakdown
   - Success metrics → Value claims (with caveats)

3. **Craft compelling headline**
   - Focus on user benefit, not feature name
   - Options: Question, How-to, Announcement, Number-based

4. **Write hook opening**
   - Start with relatable problem or surprising fact
   - Connect emotionally before announcing

5. **Structure announcement**
   - The Challenge: Problem users face
   - Introducing [Feature]: Solution overview
   - Key Benefits: 3-4 main value propositions
   - See It in Action: Brief walkthrough or visual placeholder
   - Getting Started: How to access/use
   - What's Next: Future roadmap hints

6. **Add social proof placeholder**
   - Quote section for beta users/early adopters
   - Mark as [TODO] if no quotes available

7. **Create call-to-action**
   - Clear next step for readers
   - Link placeholders for docs, signup, etc.

8. **Generate SEO metadata**
   - SEO title (60 chars)
   - Meta description (160 chars)
   - Keywords
   - Social media summary

9. **Generate blog post**
   - Create `prds/[###]-[feature-name]/blog.md`
   - Use the blog template
   - Mark placeholders for images/videos

10. **Provide approval checklist**
    - Product accuracy
    - Legal/compliance
    - Marketing review
    - Links/images finalized

## Rules

- Lead with benefits, not features
- Write for customers, not internal stakeholders
- Keep paragraphs short (2-3 sentences)
- Include concrete examples when possible
- Avoid jargon and buzzwords
- Mark all placeholder content clearly: `[TODO: ...]`

## Headline Formulas

| Formula | Example |
|---------|---------|
| Benefit-focused | "Ship Code Faster with AI-Powered Reviews" |
| How-to | "How to Cut Code Review Time in Half" |
| Announcement | "Introducing [Feature]: [Benefit]" |
| Question | "Tired of Slow Code Reviews? There's a Better Way" |
| Number-based | "3 Ways [Feature] Will Transform Your Workflow" |

## Tone Guidelines

- **Excited but not hyperbolic**: Show genuine enthusiasm
- **Customer-focused**: "You" more than "we"
- **Concrete**: Specific examples over vague claims
- **Honest**: Don't overpromise

## Content Transformation

| PRD Section | Blog Section | Transformation |
|-------------|--------------|----------------|
| Problem Statement | The Challenge | Add emotional resonance, relatability |

## Next Steps

Always conclude with contextual next steps:

- **If blog post created successfully** → "Consider `/pm.docs` to generate detailed user documentation, or `/pm.demo` to create a demo script"
- **If [TODO] placeholders remain** → "Complete the placeholders, then consider `/pm.docs` for full documentation"
- **If no PRD exists yet** → "Run `/pm.prd` first to create the source PRD, then return to `/pm.blog`"
| Solution Summary | Introducing [Feature] | Simplify, focus on outcome |
| Goals/Metrics | Benefits | Translate metrics to user value |
| User Stories | See It in Action | Show, don't tell |
| Rollout Strategy | Availability | Clear access information |
| Roadmap | What's Next | Tease without committing |

## Example Transformation

**PRD Problem Statement**:
> Developers spend an average of 4 hours per week on code reviews. Senior developers are bottlenecked with review requests, causing delays in the release cycle.

**Blog "The Challenge" Section**:
> We've all been there. You've finished a feature, submitted your pull request, and then... you wait. And wait. Your teammates are buried in their own work, and code reviews keep piling up.
>
> For many teams, code reviews have become a bottleneck. Developers spend hours each week reviewing code, and senior engineers—often the best reviewers—are completely overwhelmed.

## Example Interaction

**User**: `/pm.blog 001`

**Agent**: "I'll generate an announcement blog post from `prds/001-ai-code-review/prd.md`.

Crafting blog content:
- Transforming problem statement into engaging narrative
- Extracting 3 key benefits from goals
- Creating headline options

**Headline Options**:
1. "Introducing AI Code Review: Ship Faster, Catch More Bugs"
2. "How AI Is Transforming Code Reviews (And Saving Developers Hours)"
3. "Say Goodbye to Review Bottlenecks with AI-Powered Code Analysis"

Which headline resonates best with your audience, or would you like a different direction?"

**User**: "Option 1"

**Agent**: "Great choice. Creating `blog.md`...

I've marked 4 sections as [TODO]:
1. [TODO: Add product screenshot or GIF]
2. [TODO: Add beta user quote if available]
3. [TODO: Confirm launch date for availability section]
4. [TODO: Add signup/docs link for CTA]

The blog is ready for review. Run through the approval checklist at the bottom before publishing."

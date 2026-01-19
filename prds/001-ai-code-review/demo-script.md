# Demo Script: AI-Powered Code Review

> **Purpose**: Demo outline and talking points for presenting AI-Powered Code Review.

---

## Metadata

| Field | Value |
|-------|-------|
| **Feature ID** | 001 |
| **Source PRD** | [./prd.md](./prd.md) |
| **Generated** | 2026-01-19 |
| **Demo Duration** | 15 minutes |
| **Target Audience** | Customers / Prospects |
| **Presenter** | [Your Name] |

---

## Demo Overview

| Section | Duration | Purpose |
|---------|----------|---------|
| Opening & Context | 2 min | Set the stage, establish the problem |
| Feature Walkthrough | 5 min | Show the feature in action |
| Key Scenarios | 5 min | Demonstrate specific use cases |
| Benefits Recap | 1 min | Reinforce value proposition |
| Q&A | 5 min | Address audience questions |

**Total Duration**: 18 minutes (with Q&A)

---

## Pre-Demo Checklist

### Environment Setup

- [ ] Demo repository with prepared PR ready
- [ ] PR contains intentional bugs for AI to catch
- [ ] Browser logged into GitHub/ADO
- [ ] AI Code Review app installed on demo repo
- [ ] Incognito window (no personal bookmarks/extensions)
- [ ] Screen resolution set to 1920x1080
- [ ] Notifications disabled

### Materials Ready

- [ ] This script (printed or second screen)
- [ ] Backup: Pre-recorded video of demo flow
- [ ] Backup: Screenshots if live demo fails
- [ ] Water nearby

---

## Demo Script

### Opening (2 minutes)

**Say**:
> "Thanks for joining me today. I'm [Name], and I'm excited to show you something we've been working on that I think will change how your team handles code reviews.
>
> Before I dive in, quick question: How long does it typically take to get a code review on your team? ...
>
> [Wait for responses]
>
> That's pretty common. Our data shows the average is about 47 hours—nearly two full days. And that's just the wait. It doesn't count the back-and-forth once reviews start.
>
> What if I told you we could get that first round of feedback in 60 seconds? Let me show you."

**Key Points**:
- Build rapport with question
- Establish the problem is universal
- Tease the solution

---

### Problem Context (2 minutes)

**Say**:
> "Here's the reality most teams face:
>
> Your senior engineers—your best reviewers—spend up to a third of their time reviewing code. That's time they're not building features or mentoring the team.
>
> And for developers waiting on reviews? They've already moved on mentally. When feedback finally comes, they have to context-switch back.
>
> The bottleneck isn't that people don't want to review. It's that there aren't enough hours in the day.
>
> So we asked: What if AI could handle the first pass? Catch the obvious bugs, the security issues, the style violations—so your human reviewers can focus on the hard stuff?
>
> That's exactly what AI-Powered Code Review does. Let me show you."

**Talking Points**:
- [ ] Senior dev time tax (30% on reviews)
- [ ] Context switching cost
- [ ] AI augments humans, doesn't replace them

---

### Feature Walkthrough (5 minutes)

**[SWITCH TO: Browser with demo repository]**

#### Step 1: Submit a Pull Request

**Do**: Open the prepared PR or create new one with buggy code

**Say**:
> "I've got a pull request here with some code changes. Normal PR, nothing special about it. Watch what happens when I submit it."

**Do**: Submit/refresh the PR

**Say**:
> "See that status check? 'AI Analysis in progress...' The AI is already looking at my code."

**Highlight**:
- Status check appears immediately
- No action required from developer

**Timing**: 1 minute

---

#### Step 2: See AI Suggestions

**Do**: Wait for analysis to complete (should be < 60 seconds), then scroll to show suggestions

**Say**:
> "And there we go—under 60 seconds. Let's see what it found.
>
> [Scroll to first suggestion]
>
> Look at this. The AI caught a potential null pointer issue. See how it highlights the exact line?"

**Do**: Hover over the suggestion to show tooltip

**Say**:
> "When I hover, I get an explanation. It's not just saying 'there's a bug'—it tells me WHY this is a problem and what could go wrong.
>
> This particular issue? It would have caused a crash in production when user data is missing. But now we caught it before anyone even looked at the PR."

**Highlight**:
- Speed of analysis (< 60 seconds)
- Inline placement (right where you need it)
- Clear explanation (not cryptic warnings)

**Timing**: 2 minutes

---

#### Step 3: Apply a Fix

**Do**: Click "Apply Fix" on one suggestion

**Say**:
> "Now here's the magic. See this 'Apply Fix' button? One click..."

**Do**: Click it

**Say**:
> "...and the fix is applied directly to my branch. I didn't have to write anything. The AI suggested the fix, and I just accepted it.
>
> [Show the updated code]
>
> There's the fixed code. Safe null check. Done."

**Highlight**:
- One-click convenience
- Fix is actually applied (not just suggested)
- Developer stays in flow

**Timing**: 1 minute

---

#### Step 4: Reviewer's View

**Do**: Switch to reviewer perspective (or explain what reviewer sees)

**Say**:
> "Now let's look at this from a reviewer's perspective.
>
> When I come to review this PR, I see the AI summary right here. It shows me:
> - 3 issues found
> - 2 were auto-fixed
> - 1 was dismissed by the developer
>
> So I know the basic stuff is handled. I can focus my review on the architecture, the business logic—the things AI can't judge."

**Highlight**:
- Reviewer sees cleaner code
- Summary of what AI did
- Focus shifts to high-value review

**Timing**: 1 minute

---

### Key Scenarios (5 minutes)

#### Scenario 1: Security Vulnerability

**Do**: Scroll to a security suggestion (SQL injection or hardcoded secret)

**Say**:
> "Let me show you something critical. This is a security issue—the AI found a potential SQL injection vulnerability.
>
> [Point to the suggestion]
>
> See the red shield icon? Security issues get flagged prominently because they matter most. The AI checks against OWASP Top 10—the industry standard for web security vulnerabilities.
>
> Before AI review, this might have shipped to production. Now it's caught in 60 seconds."

**Highlight**:
- Security issues are visually distinct
- OWASP Top 10 coverage
- Prevents production incidents

**Timing**: 2 minutes

---

#### Scenario 2: Team Configuration

**Do**: Open Settings > AI Code Review

**Say**:
> "Every team is different. Maybe you have your own style guide. Maybe you want to disable certain checks.
>
> Here in settings, admins can customize everything:
> - Toggle bug detection, security, style checks
> - Link to your style guide
> - Exclude certain file paths
>
> The AI adapts to your team, not the other way around."

**Highlight**:
- Customizable per team
- Not one-size-fits-all

**Timing**: 1.5 minutes

---

#### Scenario 3: Providing Feedback

**Do**: Dismiss a suggestion and show feedback option

**Say**:
> "AI isn't perfect. Sometimes it gets things wrong. When that happens, you can dismiss the suggestion—and optionally tell us why.
>
> [Click dismiss, show feedback options]
>
> This feedback goes back into the system. We use it to improve accuracy over time. The more you use it, the better it gets for your codebase."

**Highlight**:
- AI learns from feedback
- Developers stay in control

**Timing**: 1.5 minutes

---

### Benefits Recap (1 minute)

**Say**:
> "Let me quickly recap what we've seen:
>
> - **Speed**: Analysis in under 60 seconds, not 47 hours
> - **Quality**: Catches bugs and security issues before human review
> - **Focus**: Human reviewers focus on architecture, not typos
> - **Flexibility**: Configurable for your team's needs
>
> AI-Powered Code Review doesn't replace your team. It makes your team faster."

---

### Call to Action (1 minute)

**Say**:
> "Getting started is simple:
>
> 1. Install the integration—takes about 2 minutes
> 2. Configure your preferences
> 3. Submit a PR and see it in action
>
> [Show pricing/availability slide if applicable]
>
> It's available now for GitHub and Azure DevOps, on all plans.
>
> I'd love to get you set up. Any questions?"

---

### Q&A (5 minutes)

**Prepared Answers**:

| Anticipated Question | Answer |
|---------------------|--------|
| "What languages are supported?" | "JavaScript, TypeScript, and Python at launch. Go, Java, and C# coming Q3." |
| "Is my code stored?" | "No. Code is analyzed in memory and never stored. We're SOC2 Type II compliant. Enterprise customers can deploy on-premises." |
| "Will this replace code reviews?" | "No—it augments them. AI catches the basics so humans can focus on design and architecture. You still need human judgment." |
| "What's the false positive rate?" | "We target under 10%. And when you dismiss false positives with feedback, the system learns and improves." |
| "How much does it cost?" | "It's included in all plans. Free tier gets 100 analyses/month, paid plans are unlimited." |
| "What if I don't want AI suggestions on certain files?" | "You can exclude paths using a config file. Tests, vendor code, generated files—all excludable." |

**If you don't know the answer**:
> "That's a great question. Let me follow up with you on that after the demo with the exact details."

---

## Recovery Scenarios

### If the demo environment breaks:

**Say**:
> "Looks like we're having a technical hiccup. Let me show you this in a different way..."

**Options**:
1. Switch to backup video recording
2. Use prepared screenshots
3. Describe the flow verbally: "What would normally happen here is..."

### If analysis takes too long:

**Say**:
> "The analysis is taking a bit longer than usual—probably network latency. While we wait, let me show you what the result looks like..."

**Do**: Switch to pre-analyzed PR or screenshots

### If you lose your place:

- Pause, take a breath
- "Let me recap where we are..."
- Glance at this script
- Ask "Any questions so far?" (buys time)

---

## Post-Demo Follow-Up

- [ ] Send thank you email within 24 hours
- [ ] Include: Recording link (if recorded), documentation links, next steps
- [ ] Note questions that need follow-up
- [ ] Schedule follow-up meeting if interest expressed
- [ ] Add to CRM with demo notes

---

## Presenter Notes

- Practice the transition from problem context to live demo (smoothest part should be Step 1)
- Have the buggy code ready—don't rely on typing live
- If audience engagement is high during Q&A, let it run—these are buying signals
- Watch for confused looks during technical parts—slow down if needed

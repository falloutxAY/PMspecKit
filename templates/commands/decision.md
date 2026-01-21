---
description: Log and track post-approval decisions with traceability to affected documents
handoffs:
  - agent: /pm.clarify
    prompt: If decision requires clarification from stakeholders
  - agent: /pm.analyze
    prompt: Validate decisions are properly applied to documents
---

# /pm.decision

## Purpose

Actively capture decisions when they happen—not as an afterthought. This command:
- Detects what files changed and prompts for decision context
- Links decisions to specific document sections
- Tracks decision state through to application
- Prevents decisions from getting lost in chat/email/meetings

**Philosophy**: If a change to an approved doc isn't logged, it didn't happen properly.

---

## User Input

$ARGUMENTS

**Modes**:
- `/pm.decision [feature]` - Log a new decision
- `/pm.decision review [feature]` - Review pending decisions
- `/pm.decision apply [DEC-###]` - Mark decision as applied after updating docs
- `/pm.decision summary [feature]` - Generate stakeholder change summary

---

## Outline

### Mode: Log New Decision (default)

1. **Identify feature context**
   - Accept feature number, name, or path
   - Locate feature folder in `prds/`
   - Load existing `decisions.md` if present

2. **Detect recent changes**
   - Check git diff for modified files in feature folder
   - If changes detected, ask: "I see changes to [files]. Is this decision related to those changes?"
   - If no git or no changes, proceed to manual capture

3. **Guided decision capture** (ask ONE question at a time)
   
   **Step 1: What changed?**
   > "What decision was made? Describe in one sentence."
   
   **Step 2: What triggered this?**
   > "What prompted this change? (stakeholder request / implementation discovery / scope change / priority shift / other)"
   
   **Step 3: Who was involved?**
   > "Who requested this change?"
   > "Who has authority to approve? (or: was this already approved?)"
   
   **Step 4: What documents are affected?**
   - If git changes detected: "These files changed: [list]. Confirm which are affected."
   - If no git: "Which documents does this decision affect? (prd.md / feature-overview.md / ado-workitems.md / other)"
   - For each affected doc: "Which section? (e.g., 'User Stories', 'Requirements', 'Scope')"
   
   **Step 5: What alternatives were considered?**
   > "Were other options considered? (yes / no / not applicable)"
   - If yes: capture alternatives and why rejected
   
   **Step 6: Does this supersede anything?**
   - Scan existing decisions in `decisions.md`
   - "Does this change or reverse a previous decision? (show list of existing)"
   
   **Step 7: Impact assessment**
   > "What's the impact level? (High: timeline/scope change, Medium: requirements change, Low: minor clarification)"

4. **Generate decision entry**
   - Assign next DEC-### ID
   - Create structured entry with all captured data
   - Include precise document links: `prd.md#user-stories` format

5. **Update decisions.md**
   - Append new decision to `prds/[###]-[feature]/decisions.md`
   - Create file from template if it doesn't exist
   - Update summary table at top of file

6. **Prompt for next action**
   - If Status = Proposed: "Remember to get approval and run `/pm.decision apply DEC-###` after updating docs"
   - If Status = Approved: "Update the affected documents, then run `/pm.decision apply DEC-###`"
   - Suggest `/pm.analyze` to validate consistency

---

### Mode: Review Pending Decisions

1. **Load decisions.md**
   - Scan for decisions with Status != Applied
   
2. **Display pending decisions**

## Next Steps

Always conclude with contextual next steps based on decision state:

- **If decision logged as Proposed** → "Get approval, then run `/pm.decision apply DEC-###` after updating docs"
- **If decision logged as Approved** → "Update affected documents, then run `/pm.decision apply DEC-###` to mark as applied"
- **If decision applied** → "Run `/pm.analyze` to validate consistency across all documents"
- **If decision requires stakeholder input** → "Run `/pm.clarify` to gather needed information"
- **If reviewing pending decisions** → "Address oldest pending decisions first to prevent staleness"
   ```
   ## Pending Decisions for [Feature]
   
   | ID | Decision | Status | Days Open | Affected Docs |
   |----|----------|--------|-----------|---------------|
   | DEC-003 | Remove offline mode | Proposed | 5 days | prd.md#scope |
   | DEC-002 | Add admin dashboard | Approved | 12 days ⚠️ | prd.md, ado-workitems.md |
   
   ⚠️ DEC-002 has been approved for 12 days without being applied.
   ```

3. **Offer actions**
   - "Would you like to apply any of these decisions now?"
   - "Would you like to escalate stale decisions?"

---

### Mode: Apply Decision

1. **Load specific decision**
   - Find DEC-### in decisions.md
   - Display decision details and affected documents

2. **Verify changes were made**
   - For each affected document/section:
     - "Have you updated [prd.md#user-stories] to reflect this decision? (yes / no / show me)"
     - If "show me": read and display that section for verification
   
3. **Mark as applied**
   - Update decision status to "Applied"
   - Add application date
   - Add link to changed sections (if git available, include commit reference)

4. **Update decisions.md**
   - Move decision to Applied status
   - Update summary table

---

### Mode: Stakeholder Summary

1. **Gather changes since date**
   > "Generate summary since when? (last week / last sprint / specific date / last stakeholder review)"

2. **Compile changes**
   - All decisions (Proposed, Approved, Applied) since that date
   - Group by impact level
   - Include decision rationale

3. **Generate summary**
   ```markdown
   ## Change Summary: [Feature Name]
   **Period**: [Start Date] to [Today]
   **Prepared for**: [Stakeholder sync / Executive review / etc.]
   
   ### High Impact Changes
   
   #### DEC-004: Removed offline mode from v1 scope
   - **Decided**: 2026-01-18
   - **Requestor**: Engineering (capacity constraints)
   - **Rationale**: Would add 3 weeks to timeline; moved to v1.1
   - **Affected**: prd.md#scope, ado-workitems.md
   - **Status**: Applied ✓
   
   ### Medium Impact Changes
   ...
   
   ### Pending Decisions (Need Input)
   - DEC-005: API rate limiting approach (proposed 2026-01-19)
   ```

4. **Offer export**
   - "Save this summary to `prds/[###]-[feature]/change-summary-[date].md`?"

---

## Rules

- One question at a time—don't overwhelm
- Always link to specific sections, not just files
- Decisions without affected documents are incomplete
- Proposed decisions older than 7 days trigger warnings
- Approved decisions older than 14 days without application trigger escalation prompts
- Never auto-apply decisions—human must confirm docs were updated

## Decision States

```
Proposed ──[stakeholder approves]──► Approved ──[docs updated]──► Applied
    │                                    │
    └──[rejected]──► Rejected            └──[superseded]──► Superseded
```

| State | Meaning | Next Action |
|-------|---------|-------------|
| Proposed | Decision captured, awaiting approval | Get stakeholder sign-off |
| Approved | Approved, docs not yet updated | Update affected documents |
| Applied | Docs updated to reflect decision | None (complete) |
| Rejected | Decision was not approved | Document why, close |
| Superseded | Replaced by later decision | Link to new decision |

## Document Section Links

Use markdown anchor format for precise traceability:

| Reference Style | Example |
|-----------------|---------|
| File + section | `prd.md#user-stories` |
| File + subsection | `prd.md#us-003-configure-settings` |
| Specific requirement | `prd.md#req-007` |
| Work item | `ado-workitems.md#feat-002` |

## Integration Points

| Command | Integration |
|---------|-------------|
| `/pm.analyze` | Checks for unapplied decisions, flags stale Proposed items |
| `/pm.clarify` | Can trigger decision log if clarification changes approved content |
| `/pm.prd` | Prompts "Any decisions to log?" after major PRD updates |
| `/pm.tasks` | Prompts if decisions affect work items |

## Conflict Detection

When logging a new decision, check for conflicts:

```markdown
⚠️ Potential Conflict Detected

Your new decision: "Remove offline mode from scope"
Existing DEC-001: "Offline mode is P0 requirement per customer commitment"

Options:
1. This supersedes DEC-001 (will mark DEC-001 as Superseded)
2. These are compatible (explain how)
3. Cancel and reconsider
```

## Example Interaction

**User**: `/pm.decision 001`

**Agent**: "I'll help you log a decision for feature 001 (AI-powered code review).

I see these files were modified today:
- `prd.md` (User Stories section)
- `ado-workitems.md`

Is this decision related to those changes?"

**User**: "Yes"

**Agent**: "Great. What decision was made? Describe in one sentence."

**User**: "We're removing the auto-fix suggestion feature from v1"

**Agent**: "Got it. What prompted this change?
1. Stakeholder request
2. Implementation discovery  
3. Scope/timeline pressure
4. Priority shift
5. Other"

**User**: "3 - scope pressure"

**Agent**: "Who requested this scope reduction?"

**User**: "Jordan (eng lead) raised it, I agreed"

**Agent**: "Who has authority to approve this decision? Or was it already approved?"

**User**: "I approved it as PM, but need to inform Sarah (director)"

**Agent**: "Understood—I'll mark this as Approved, pending communication.

Which sections of prd.md are affected?"

**User**: "User Stories and the US-001 acceptance criteria specifically"

**Agent**: "Were other options considered?"

**User**: "Yes - we considered reducing other features instead, or extending timeline"

**Agent**: "Why were those rejected?"

**User**: "Other features are more core to MVP. Timeline extension not approved."

**Agent**: "This seems related to existing decisions. Does this supersede any previous decision?"

[Shows list of existing decisions]

**User**: "No, this is new"

**Agent**: "Last question: What's the impact level?
- High (timeline or major scope change)
- Medium (requirements change)  
- Low (minor clarification)"

**User**: "High - removes a headline feature"

**Agent**: 
```
## Decision Logged

**DEC-002**: Remove auto-fix suggestion feature from v1

| Field | Value |
|-------|-------|
| Status | Approved |
| Requestor | Jordan Smith (Eng Lead) |
| Approver | [You] - PM |
| Impact | High |
| Trigger | Scope/timeline pressure |

**Affected Documents**:
- prd.md#user-stories
- prd.md#us-001-receive-ai-code-suggestions
- ado-workitems.md

**Alternatives Rejected**:
- Reduce other features (more core to MVP)
- Extend timeline (not approved)

**Next Steps**:
1. Inform Sarah (director) of this decision
2. Update prd.md and ado-workitems.md
3. Run `/pm.decision apply DEC-002` after updates
```

---

## Suggested Triggers

Prompt users to run `/pm.decision` when:

| Trigger | Prompt |
|---------|--------|
| After `/pm.clarify` on approved PRD | "This clarification modifies an approved document. Log as decision?" |
| After editing approved PRD manually | "I detected changes to approved prd.md. Log the decision?" |
| In `/pm.analyze` | "Found unapplied decisions. Run `/pm.decision review`?" |
| After stakeholder meetings | Best practice: end meetings with `/pm.decision` |

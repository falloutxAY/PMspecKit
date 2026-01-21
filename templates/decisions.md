# Decision Log: [Feature Name]

> **Purpose**: Track post-approval changes, stakeholder discussions, and decision rationale. This document preserves the "why" behind spec changes and provides an audit trail for future reference.

---

## How to Use This Document

1. **When to add an entry**: Any time a decision changes after PRD approval, or when stakeholders disagree and a resolution is reached
2. **Who updates**: PM owns this document, but anyone can propose entries
3. **Link back**: Always reference which PRD sections are affected
4. **Never delete**: Superseded decisions stay for historical context

---

## Decision Summary

| ID | Decision | Date | Status | Impact |
|----|----------|------|--------|--------|
| DEC-001 | [Brief title] | YYYY-MM-DD | Approved | [High/Med/Low] |
| DEC-002 | [Brief title] | YYYY-MM-DD | Superseded by DEC-003 | [High/Med/Low] |

---

## Decisions

### DEC-001: [Decision Title]

| Field | Value |
|-------|-------|
| **Date** | YYYY-MM-DD |
| **Status** | Proposed / Approved / Superseded |
| **Requestor** | [Who raised this issue or requested the change] |
| **Decision Maker** | [Who had authority to approve] |
| **Affected Documents** | prd.md §[Section], ado-workitems.md |
| **Impact Level** | High / Medium / Low |

#### Context

[What prompted this decision? What problem or conflict arose?]

#### The Decision

[Clear statement of what was decided]

#### Rationale

[Why this option was chosen over alternatives]

#### Alternatives Considered

| Option | Pros | Cons | Why Rejected |
|--------|------|------|--------------|
| [Option A] | [Benefits] | [Drawbacks] | [Reason not chosen] |
| [Option B] | [Benefits] | [Drawbacks] | [Reason not chosen] |
| **[Chosen Option]** | [Benefits] | [Drawbacks] | **Selected** |

#### Stakeholder Positions

| Stakeholder | Initial Position | Final Position | Concerns Addressed |
|-------------|------------------|----------------|-------------------|
| [Name/Role] | [What they wanted] | [What they accepted] | [How their concerns were resolved] |

#### Implementation Notes

[Any specific guidance for how this decision affects implementation]

#### Supersedes

[If this reverses or modifies a previous decision, link to it: "Supersedes DEC-00X because..."]

---

### DEC-002: [Decision Title]

| Field | Value |
|-------|-------|
| **Date** | YYYY-MM-DD |
| **Status** | Proposed / Approved / Superseded |
| **Requestor** | [Who raised this issue or requested the change] |
| **Decision Maker** | [Who had authority to approve] |
| **Affected Documents** | prd.md §[Section] |
| **Impact Level** | High / Medium / Low |

#### Context

[What prompted this decision?]

#### The Decision

[Clear statement of what was decided]

#### Rationale

[Why this option was chosen]

#### Alternatives Considered

| Option | Pros | Cons | Why Rejected |
|--------|------|------|--------------|
| [Option A] | [Benefits] | [Drawbacks] | [Reason] |

#### Stakeholder Positions

| Stakeholder | Initial Position | Final Position | Concerns Addressed |
|-------------|------------------|----------------|-------------------|
| [Name/Role] | [Position] | [Position] | [Resolution] |

---

## Escalation History

> Track any decisions that required escalation beyond the immediate team.

| Decision | Escalated To | Date | Outcome |
|----------|--------------|------|---------|
| DEC-00X | [VP Product / Executive] | YYYY-MM-DD | [Resolution] |

---

## Lessons Learned

> After feature ships, capture what the decision log taught us.

| Decision | What We Learned | Apply To Future |
|----------|-----------------|-----------------|
| DEC-00X | [Insight] | [How to use this learning] |

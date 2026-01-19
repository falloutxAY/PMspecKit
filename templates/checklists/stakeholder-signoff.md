# Stakeholder Sign-off Checklist

> **Purpose**: Ensure all required stakeholders have reviewed and approved the PRD before development begins.

---

## Feature Information

| Field | Value |
|-------|-------|
| **Feature ID** | [###] |
| **Feature Name** | [Name] |
| **PRD Location** | [./prd.md](./prd.md) |
| **Target Release** | [Release] |
| **Sign-off Deadline** | [YYYY-MM-DD] |

---

## Pre-Review Checklist

Before requesting sign-off, confirm:

- [ ] PRD is complete (no `[NEEDS CLARIFICATION]` markers)
- [ ] `/pm.analyze` passes with no CRITICAL or HIGH issues
- [ ] All requirements have unique IDs
- [ ] All user stories have acceptance criteria
- [ ] Success metrics are measurable with targets
- [ ] Constitution alignment verified
- [ ] Design mockups/wireframes attached (if applicable)

---

## Required Sign-offs

### Product

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| [Name] | PM Lead | ⬜ Pending / ✅ Approved / ❌ Rejected | | |
| [Name] | Product Director | ⬜ Pending / ✅ Approved / ❌ Rejected | | |

**Product Sign-off Criteria**:
- [ ] Aligns with product strategy
- [ ] Prioritization is appropriate
- [ ] Scope is achievable for target release
- [ ] Success metrics are realistic

---

### Engineering

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| [Name] | Engineering Lead | ⬜ Pending / ✅ Approved / ❌ Rejected | | |
| [Name] | Tech Lead | ⬜ Pending / ✅ Approved / ❌ Rejected | | |

**Engineering Sign-off Criteria**:
- [ ] Requirements are technically feasible
- [ ] Dependencies are identified and manageable
- [ ] Non-functional requirements are achievable
- [ ] No major technical risks unaddressed
- [ ] Estimate aligns with timeline

---

### Design

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| [Name] | UX Lead | ⬜ Pending / ✅ Approved / ❌ Rejected | | |

**Design Sign-off Criteria**:
- [ ] User flows are clear and complete
- [ ] Accessibility requirements addressed
- [ ] Design specs can be completed in timeline
- [ ] No major UX concerns

---

### Other Stakeholders (as needed)

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| [Name] | Legal | ⬜ Pending / ✅ Approved / ❌ Rejected / ⬜ N/A | | |
| [Name] | Security | ⬜ Pending / ✅ Approved / ❌ Rejected / ⬜ N/A | | |
| [Name] | Marketing | ⬜ Pending / ✅ Approved / ❌ Rejected / ⬜ N/A | | |
| [Name] | Support | ⬜ Pending / ✅ Approved / ❌ Rejected / ⬜ N/A | | |

---

## Sign-off Summary

| Category | Required | Obtained | Status |
|----------|----------|----------|--------|
| Product | X | Y | ⬜ / ✅ |
| Engineering | X | Y | ⬜ / ✅ |
| Design | X | Y | ⬜ / ✅ |
| Other | X | Y | ⬜ / ✅ |

**Overall Status**: ⬜ In Progress / ✅ Approved / ❌ Blocked

---

## Blocking Issues

| Issue | Owner | Resolution | Status |
|-------|-------|------------|--------|
| [Issue from review] | [Owner] | [How to resolve] | Open / Resolved |

---

## Revision History

| Version | Date | Changes | Re-approvals Needed |
|---------|------|---------|---------------------|
| 1.0 | [Date] | Initial PRD | All |
| 1.1 | [Date] | [Changes] | [Who needs to re-approve] |

---

## Final Approval

**PRD Approved for Development**: ⬜ No / ✅ Yes

**Approval Date**: [YYYY-MM-DD]

**Approved By**: [Names and roles]

**Conditions** (if any):
- [Any conditions or caveats on the approval]

---

## Next Steps After Approval

- [ ] Create Azure DevOps work items (`/pm.tasks`)
- [ ] Schedule sprint planning
- [ ] Notify stakeholders of approval
- [ ] Begin design specifications

# Workback Schedule: [Feature Name]

> **Purpose**: Plan implementation timeline by working backwards from target launch date. Defines key milestones, dependencies, and buffer periods to ensure realistic delivery.

---

## Metadata

| Field | Value |
|-------|-------|
| **Feature ID** | [###] |
| **Feature Name** | [Name] |
| **PRD Location** | [./prd.md](./prd.md) |
| **Target Launch Date** | [YYYY-MM-DD] |
| **Schedule Created** | [YYYY-MM-DD] |
| **Last Updated** | [YYYY-MM-DD] |
| **Status** | Draft / Approved / In Progress / Complete |

---

## Schedule Overview

**Launch Date**: [YYYY-MM-DD]  
**Total Duration**: [X weeks]  
**Buffer Allocation**: [X%] of timeline  
**Contingency Days**: [X days]

### Schedule at a Glance

```
[Launch Date - X weeks]           [Launch Date]
        ↓                               ↓
[Design] → [Dev] → [Testing] → [Staging] → [Launch]
   2w        4w        2w          1w         •
```

---

## Timeline Assumptions

Document key assumptions that influence the timeline:

- [ ] Team size: [X developers, X designers, X QA]
- [ ] Team availability: [X% capacity, holidays/PTO accounted for]
- [ ] Dependencies: [List external dependencies]
- [ ] Complexity: [Simple / Moderate / Complex]
- [ ] Risk level: [Low / Medium / High]
- [ ] Priority: [P0 / P1 / P2 / P3]

---

## Milestones & Dependencies

### Milestone 1: PRD Approval
**Target Date**: [YYYY-MM-DD] ← [X weeks before launch]

**Activities**:
- [ ] PRD drafted and reviewed
- [ ] Stakeholder feedback incorporated
- [ ] Constitution alignment verified
- [ ] PRD approved by stakeholders

**Dependencies**: None (start of timeline)

**Gate Criteria**:
- [ ] All stakeholders have signed off
- [ ] No unresolved `[NEEDS CLARIFICATION]` markers
- [ ] Risk assessment complete

**Buffer**: +[X days] contingency

---

### Milestone 2: Design Review Complete
**Target Date**: [YYYY-MM-DD] ← [X weeks before launch]

**Activities**:
- [ ] UX wireframes created
- [ ] High-fidelity mockups completed
- [ ] User flow validated
- [ ] Design review meeting held
- [ ] Design approved by stakeholders

**Dependencies**: 
- Blocking: M1 (PRD Approval)
- Parallel: Technical architecture planning

**Gate Criteria**:
- [ ] All P0 screens designed
- [ ] User flows validated with stakeholders
- [ ] Accessibility considerations documented
- [ ] Design system compliance verified

**Buffer**: +[X days] contingency

**Stakeholder Checkpoint**: Design review meeting with [stakeholders]

---

### Milestone 3: Development Start
**Target Date**: [YYYY-MM-DD] ← [X weeks before launch]

**Activities**:
- [ ] Development environment setup
- [ ] Work items created in Azure DevOps
- [ ] Technical architecture approved
- [ ] Sprint planning complete
- [ ] Development kickoff

**Dependencies**: 
- Blocking: M2 (Design Review Complete)
- Parallel: Test plan development

**Gate Criteria**:
- [ ] All work items estimated and prioritized
- [ ] Technical dependencies identified
- [ ] Development team ramped up
- [ ] Sprint goals defined

**Buffer**: +[X days] contingency

---

### Milestone 4: Development Complete
**Target Date**: [YYYY-MM-DD] ← [X weeks before launch]

**Activities**:
- [ ] All P0 requirements implemented
- [ ] All P1 requirements implemented (or deferred)
- [ ] Code reviews completed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Technical debt documented

**Dependencies**: 
- Blocking: M3 (Development Start)
- Parallel: Documentation drafting

**Gate Criteria**:
- [ ] Code freeze for feature
- [ ] No critical bugs open
- [ ] Test coverage meets target ([X%])
- [ ] Performance benchmarks met

**Buffer**: +[X days] contingency

**Stakeholder Checkpoint**: Demo to stakeholders

---

### Milestone 5: Testing Complete
**Target Date**: [YYYY-MM-DD] ← [X weeks before launch]

**Activities**:
- [ ] End-to-end testing complete
- [ ] Performance testing complete
- [ ] Security testing complete
- [ ] Accessibility testing complete
- [ ] Bug fixes completed
- [ ] Regression testing passed

**Dependencies**: 
- Blocking: M4 (Development Complete)
- Parallel: User documentation review

**Gate Criteria**:
- [ ] All P0/P1 bugs resolved
- [ ] P2/P3 bugs triaged (fix or defer)
- [ ] Test sign-off from QA lead
- [ ] Performance meets SLA targets
- [ ] Security scan passed

**Buffer**: +[X days] contingency

**Stakeholder Checkpoint**: Testing sign-off

---

### Milestone 6: Staging Deployment
**Target Date**: [YYYY-MM-DD] ← [X weeks before launch]

**Activities**:
- [ ] Deploy to staging environment
- [ ] Smoke tests passing in staging
- [ ] Stakeholder UAT (User Acceptance Testing)
- [ ] Support team training complete
- [ ] Monitoring and alerts configured
- [ ] Rollback procedure tested

**Dependencies**: 
- Blocking: M5 (Testing Complete)
- Parallel: Communication materials finalized

**Gate Criteria**:
- [ ] Staging environment stable
- [ ] UAT sign-off from key stakeholders
- [ ] Support team trained and ready
- [ ] Launch checklist completed

**Buffer**: +[X days] contingency

**Stakeholder Checkpoint**: UAT sign-off meeting

---

### Milestone 7: Production Launch
**Target Date**: [YYYY-MM-DD] ← [LAUNCH DATE]

**Activities**:
- [ ] Final go/no-go decision
- [ ] Deploy to production
- [ ] Feature flag enabled (if applicable)
- [ ] Monitoring dashboards active
- [ ] Communications published
- [ ] Support team on standby

**Dependencies**: 
- Blocking: M6 (Staging Deployment)
- All previous milestones complete

**Gate Criteria**:
- [ ] All launch readiness checklist items complete
- [ ] No open blockers
- [ ] Team availability confirmed
- [ ] Rollback plan ready

**Buffer**: None (target date)

**Stakeholder Checkpoint**: Go/no-go meeting

---

## Buffer & Contingency Strategy

### Buffer Allocation

| Phase | Estimated Duration | Buffer | Total Time |
|-------|-------------------|--------|------------|
| PRD & Design | [X weeks] | [X days] | [X weeks] |
| Development | [X weeks] | [X days] | [X weeks] |
| Testing | [X weeks] | [X days] | [X weeks] |
| Staging & Launch Prep | [X weeks] | [X days] | [X weeks] |
| **Total** | **[X weeks]** | **[X days]** | **[X weeks]** |

### Contingency Plan

**If running behind schedule:**
1. Review P1/P2 requirements for potential deferral
2. Increase team capacity (if possible)
3. Adjust launch scope (MVP approach)
4. Communicate revised timeline to stakeholders

**Triggers for timeline adjustment:**
- [ ] Critical blocker discovered
- [ ] Dependency delayed by [X days]
- [ ] Team capacity reduced by [X%]
- [ ] Scope change approved

---

## Critical Path

These tasks are on the critical path and cannot be delayed without impacting launch:

1. **PRD Approval** → Must complete by [date] or launch moves
2. **Design Review** → Must complete by [date] or dev can't start
3. **Dev Complete** → Must complete by [date] or testing compressed
4. **Testing Complete** → Must complete by [date] or launch at risk
5. **Staging UAT** → Must complete by [date] or no time to fix issues

### Parallel Tracks (Non-Blocking)

These can proceed in parallel and are not on critical path:
- Documentation drafting (can continue into launch week)
- Blog post preparation (can publish post-launch)
- Support training (can complete during staging)

---

## Stakeholder Review Points

| Checkpoint | Date | Attendees | Purpose | Decision Required |
|------------|------|-----------|---------|-------------------|
| PRD Review | [Date] | [PM, Eng Lead, Design] | Approve requirements | Go/No-Go on design |
| Design Review | [Date] | [PM, Design, Stakeholders] | Approve UX/UI | Go/No-Go on development |
| Dev Complete Demo | [Date] | [PM, Eng Lead, Key Stakeholders] | Review implementation | Approve for testing |
| UAT Sign-off | [Date] | [PM, Stakeholders, Support] | Validate feature | Approve for launch |
| Go/No-Go Meeting | [Date] | [Leadership, PM, Eng Lead] | Launch readiness | Final launch approval |

---

## Risk & Impact Assessment

### Schedule Risks

| Risk | Impact | Probability | Mitigation | Owner |
|------|--------|-------------|------------|-------|
| Design takes longer than estimated | High | Medium | Start parallel tech planning, reduce scope if needed | [Design Lead] |
| Critical bug found late in testing | High | Medium | Allocate extra buffer in testing phase | [QA Lead] |
| Dependency from external team delayed | High | Low | Early communication, identify alternatives | [PM] |
| Key team member unavailable | Medium | Medium | Cross-train team, document knowledge | [Eng Lead] |

### Timeline Confidence

| Phase | Confidence Level | Notes |
|-------|-----------------|-------|
| PRD & Design | High / Medium / Low | [Rationale] |
| Development | High / Medium / Low | [Rationale] |
| Testing | High / Medium / Low | [Rationale] |
| Staging & Launch | High / Medium / Low | [Rationale] |

**Overall Timeline Confidence**: [High / Medium / Low]

---

## Weekly Status Tracking

### Week [X]: [Date Range]

**Status**: On Track / At Risk / Delayed

**Completed**:
- [ ] [Milestone or task completed]
- [ ] [Milestone or task completed]

**In Progress**:
- [ ] [Current work]

**Blockers**:
- None / [Description of blocker]

**Next Week Focus**:
- [ ] [Planned work]

**Timeline Impact**: None / [X days ahead/behind]

---

## Milestone Gantt Chart

```
Milestones                    Week 1  Week 2  Week 3  Week 4  Week 5  Week 6  Week 7  Week 8
PRD Approval                  ████
Design Review                         ████
Development Start                             █
Development                                   ████████████████
Testing                                                       ████████
Staging                                                               ████
Launch                                                                    █
```

---

## Integration with Project Artifacts

This workback schedule integrates with:

- **PRD**: [./prd.md](./prd.md) - Source requirements and success criteria
- **Work Items**: [./ado-workitems.md](./ado-workitems.md) - Detailed task breakdown
- **Launch Checklist**: [../../templates/checklists/launch-readiness.md](../../templates/checklists/launch-readiness.md) - Pre-launch verification

---

## Version History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1 | [YYYY-MM-DD] | [Name] | Initial schedule |
| 0.2 | [YYYY-MM-DD] | [Name] | Adjusted timeline after design review |

---

## Notes

- This schedule is a living document and should be updated weekly
- Use this template to communicate timeline expectations with stakeholders
- Adjust buffer percentages based on team velocity and historical data
- Review and update risk assessment as project progresses

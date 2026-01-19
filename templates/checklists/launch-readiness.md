# Launch Readiness Checklist

> **Purpose**: Ensure all launch prerequisites are complete before releasing the feature to users.

---

## Feature Information

| Field | Value |
|-------|-------|
| **Feature ID** | [###] |
| **Feature Name** | [Name] |
| **PRD Location** | [./prd.md](./prd.md) |
| **Target Launch Date** | [YYYY-MM-DD] |
| **Launch Type** | GA / Preview / Beta / Internal |
| **Rollout Strategy** | Big Bang / Phased / Feature Flag |

---

## Development Readiness

### Code Complete

- [ ] All P0 requirements implemented
- [ ] All P1 requirements implemented (or deferred with approval)
- [ ] Code reviewed and merged
- [ ] No critical bugs open
- [ ] Technical debt documented

### Testing Complete

- [ ] Unit tests passing
- [ ] Integration tests passing
- [ ] End-to-end tests passing
- [ ] Performance testing complete
- [ ] Security testing complete
- [ ] Accessibility testing complete

| Test Type | Status | Coverage | Notes |
|-----------|--------|----------|-------|
| Unit | ⬜ / ✅ | X% | |
| Integration | ⬜ / ✅ | | |
| E2E | ⬜ / ✅ | | |
| Performance | ⬜ / ✅ | | |
| Security | ⬜ / ✅ | | |
| Accessibility | ⬜ / ✅ | | |

---

## Documentation Readiness

### User Documentation

- [ ] User guide complete (`/pm.docs`)
- [ ] Getting started guide complete
- [ ] FAQ updated
- [ ] Screenshots/videos captured
- [ ] Documentation reviewed for accuracy

### Internal Documentation

- [ ] Release notes drafted
- [ ] Known issues documented
- [ ] Runbook/playbook created
- [ ] Architecture documentation updated

| Document | Location | Status | Owner |
|----------|----------|--------|-------|
| User Guide | [Link] | ⬜ / ✅ | [Name] |
| Release Notes | [Link] | ⬜ / ✅ | [Name] |
| Runbook | [Link] | ⬜ / ✅ | [Name] |

---

## Support Readiness

### Support Team Preparation

- [ ] Support team briefed on feature
- [ ] FAQ and troubleshooting guide shared
- [ ] Escalation path defined
- [ ] Support tickets category created
- [ ] SLA reviewed for new feature

### Monitoring & Alerting

- [ ] Monitoring dashboards created
- [ ] Alerts configured
- [ ] On-call rotation confirmed
- [ ] Rollback procedure documented

| System | Dashboard | Alerts | Owner |
|--------|-----------|--------|-------|
| [System 1] | [Link] | ⬜ / ✅ | [Name] |
| [System 2] | [Link] | ⬜ / ✅ | [Name] |

---

## Communication Readiness

### Internal Communication

- [ ] Leadership briefed
- [ ] Sales team trained
- [ ] Customer success briefed
- [ ] Internal announcement drafted

### External Communication

- [ ] Blog post ready (`/pm.blog`)
- [ ] Social media content prepared
- [ ] Email announcement drafted
- [ ] Press release (if applicable)
- [ ] Partner notification (if applicable)

| Communication | Channel | Status | Publish Date | Owner |
|---------------|---------|--------|--------------|-------|
| Blog Post | [Platform] | ⬜ / ✅ | [Date] | [Name] |
| Social | [Platforms] | ⬜ / ✅ | [Date] | [Name] |
| Email | [List] | ⬜ / ✅ | [Date] | [Name] |

---

## Demo & Training Readiness

- [ ] Demo script ready (`/pm.demo`)
- [ ] Demo environment prepared
- [ ] Demo recording available (backup)
- [ ] Training materials created
- [ ] Webinar/training sessions scheduled

---

## Legal & Compliance

- [ ] Terms of service updated (if needed)
- [ ] Privacy policy updated (if needed)
- [ ] Compliance review complete
- [ ] Data handling approved
- [ ] Accessibility compliance verified

| Review | Reviewer | Status | Date |
|--------|----------|--------|------|
| Legal | [Name] | ⬜ / ✅ / N/A | |
| Privacy | [Name] | ⬜ / ✅ / N/A | |
| Security | [Name] | ⬜ / ✅ / N/A | |
| Accessibility | [Name] | ⬜ / ✅ / N/A | |

---

## Rollout Plan

### Rollout Phases

| Phase | Audience | % of Users | Start Date | Duration | Go/No-Go Criteria |
|-------|----------|------------|------------|----------|-------------------|
| 1 | [Internal / Beta] | X% | [Date] | [Duration] | [Criteria] |
| 2 | [Early adopters] | X% | [Date] | [Duration] | [Criteria] |
| 3 | [GA] | 100% | [Date] | - | [Criteria] |

### Feature Flags

| Flag | Description | Default | Rollout % |
|------|-------------|---------|-----------|
| [Flag name] | [What it controls] | Off / On | X% |

### Rollback Plan

- [ ] Rollback procedure documented
- [ ] Rollback tested
- [ ] Rollback owner identified
- [ ] Rollback decision criteria defined

**Rollback Owner**: [Name]

**Rollback Trigger**: [Criteria that would trigger rollback]

---

## Success Metrics Setup

- [ ] Analytics instrumentation complete
- [ ] Dashboards created
- [ ] Baseline metrics captured
- [ ] Success criteria defined

| Metric | Baseline | Target | Dashboard | Owner |
|--------|----------|--------|-----------|-------|
| [From PRD SM-001] | [Value] | [Value] | [Link] | [Name] |
| [From PRD SM-002] | [Value] | [Value] | [Link] | [Name] |

---

## Launch Day Checklist

### Pre-Launch (Day Before)

- [ ] Final go/no-go meeting held
- [ ] All blockers resolved
- [ ] Team availability confirmed
- [ ] War room/channel set up
- [ ] Rollback procedure reviewed

### Launch Day

- [ ] Feature flag enabled (if applicable)
- [ ] Deployment completed successfully
- [ ] Smoke tests passing
- [ ] Monitoring dashboards active
- [ ] Communications published
- [ ] Support team on standby

### Post-Launch (Day After)

- [ ] Metrics reviewed
- [ ] Issues triaged
- [ ] Customer feedback collected
- [ ] Retrospective scheduled

---

## Go/No-Go Decision

### Blockers

| Blocker | Owner | Resolution | Status |
|---------|-------|------------|--------|
| [Issue] | [Name] | [Plan] | Open / Resolved |

### Decision

**Launch Approved**: ⬜ No / ✅ Yes

**Decision Date**: [YYYY-MM-DD]

**Decision Makers**: [Names and roles]

**Conditions** (if any):
- [Any conditions on the launch]

---

## Post-Launch Review

**Scheduled Date**: [YYYY-MM-DD]

**Attendees**: [Roles/Names]

**Agenda**:
- Metrics review
- Issue summary
- Customer feedback
- Lessons learned
- Next iteration planning

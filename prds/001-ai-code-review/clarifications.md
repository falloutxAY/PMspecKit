# Clarifications: AI-Powered Code Review

> **Purpose**: Session log of clarification Q&A for feature 001.

---

## Session 2026-01-17 14:30

### Question
What is the target false positive rate for AI suggestions?

### Context
False positives frustrate developers and reduce trust in the system. Too many incorrect suggestions will cause users to ignore all AI feedback. This affects the accuracy NFR and user satisfaction metrics.

### Recommendation
Industry standard for similar tools is 10-15% false positive rate. Recommend targeting < 10% to differentiate and build trust, with a feedback mechanism to improve over time.

### Answer
Agreed: Target < 10% false positive rate. Add feedback loop for dismissed suggestions to improve model.

### Applied To
- File: feature-overview.md
- Section: Open Questions
- Change: Marked question as resolved with "< 10%" target

---

## Session 2026-01-17 15:00

### Question
Should AI suggestions block PR merge, or be advisory only?

### Context
Blocking could enforce quality but may frustrate developers on urgent fixes. Advisory gives flexibility but may be ignored. This impacts the user flow and acceptance criteria for US-001.

### Recommendation
Advisory only for V1. Developers should be able to merge regardless of AI suggestions. Consider optional "blocking mode" for future release as admin setting.

### Answer
Confirmed: Advisory only. AI suggestions are recommendations, not requirements. Developers can merge with open suggestions.

### Applied To
- File: feature-overview.md
- Section: Open Questions
- Change: Marked as resolved with "No, advisory only"
- File: prd.md
- Section: Non-Goals
- Change: Added NG-003 about not auto-blocking merges

---

## Session 2026-01-18 10:00

### Question
How should we handle proprietary code privacy concerns?

### Context
Enterprise customers are sensitive about code leaving their environment. This is a potential blocker for adoption and affects our security requirements.

### Recommendation
Offer on-premises deployment option for Enterprise tier. For cloud, ensure no code storage (analyze in memory only) and SOC2 compliance.

### Answer
Agreed on multi-tier approach:
1. Cloud: No code storage, SOC2 Type II compliance
2. Enterprise: On-premises deployment option

### Applied To
- File: feature-overview.md
- Section: Open Questions
- Change: Marked as resolved
- File: prd.md
- Section: Non-Functional Requirements
- Change: Added NFR-005 (no code storage) and NFR-006 (SOC2 compliance)

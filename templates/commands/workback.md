---
description: Generate workback schedule from target launch date for implementation planning
handoffs:
  - agent: /pm.analyze
    prompt: Validate timeline assumptions and dependency logic
---

# /pm.workback

## User Input

$ARGUMENTS

## Outline

1. **Locate feature folder**
   - Find the feature folder in `prds/`
   - Can be specified by number (e.g., `001`) or name
   - Verify `prd.md` exists

2. **Extract launch date and constraints**
   - Check PRD for target release date
   - If not in PRD, prompt user for target launch date
   - Ask for team size and availability assumptions
   - Ask for complexity level (Simple / Moderate / Complex)

3. **Calculate timeline working backwards**
   - Start from target launch date
   - Apply standard phase durations based on complexity:
     - Simple: 4-6 weeks total
     - Moderate: 6-10 weeks total
     - Complex: 10-16 weeks total
   - Phase breakdown (% of total timeline):
     - PRD & Design: 20-25%
     - Development: 40-50%
     - Testing: 20-25%
     - Staging & Launch Prep: 10-15%

4. **Apply buffer and contingency**
   - Add 15-20% buffer for Simple features
   - Add 20-30% buffer for Moderate features
   - Add 30-40% buffer for Complex features
   - Distribute buffer proportionally across phases

5. **Define milestone dependencies**
   - Create dependency chain:
     1. PRD Approval (no dependencies)
     2. Design Review (depends on M1)
     3. Development Start (depends on M2)
     4. Development Complete (depends on M3)
     5. Testing Complete (depends on M4)
     6. Staging Deployment (depends on M5)
     7. Production Launch (depends on M6)
   - Identify parallel tracks (docs, training, communications)

6. **Map requirements to phases**
   - Parse PRD requirements (REQ-###)
   - Allocate P0 requirements to development phase
   - Suggest P1/P2 requirements for potential deferral if timeline tight
   - Map non-functional requirements to testing phase

7. **Identify stakeholder checkpoints**
   - Schedule review meetings at key milestones:
     - PRD Review (before design)
     - Design Review (before dev)
     - Dev Complete Demo (before testing)
     - UAT Sign-off (before launch)
     - Go/No-Go Meeting (launch day)

8. **Generate gate criteria**
   - Define completion criteria for each milestone
   - Include quality gates (test coverage, bug thresholds)
   - Add compliance checkpoints (security, accessibility)

9. **Create risk assessment**
   - Identify schedule risks based on:
     - Feature complexity
     - Team size
     - External dependencies
     - Parallel projects
   - Suggest mitigation strategies for each risk

10. **Generate workback schedule document**
    - Create `prds/[###]-[feature-name]/workback-schedule.md`
    - Use the workback-schedule template
    - Populate all dates working backwards from launch
    - Include Gantt-style visualization

11. **Integrate with existing artifacts**
    - Link to PRD for requirements reference
    - Reference ado-workitems.md for detailed tasks
    - Link to launch-readiness checklist

12. **Provide recommendations**
    - Highlight critical path items
    - Suggest where to allocate more buffer
    - Flag if timeline seems unrealistic
    - Recommend scope adjustments if needed

13. **Suggest next steps**
    - Run `/pm.analyze` to validate timeline assumptions
    - Schedule stakeholder review meetings
    - Set up weekly status tracking cadence

## Rules

- Timeline must work backwards from target launch date
- All milestones must have clear dependencies
- Buffer must be allocated based on complexity and risk
- Each milestone must have measurable gate criteria
- Stakeholder checkpoints required at phase transitions
- Critical path must be clearly identified
- Parallel tracks (non-blocking) must be distinguished
- If timeline seems unrealistic, warn user and suggest alternatives
- Timeline should account for team capacity and holidays

## Timeline Calculation Guidelines

### Phase Duration Formulas

For a feature with total duration **T weeks**:

| Phase | Simple (%) | Moderate (%) | Complex (%) |
|-------|-----------|-------------|------------|
| PRD & Design | 20% | 22% | 25% |
| Development | 45% | 45% | 45% |
| Testing | 20% | 22% | 20% |
| Staging & Launch | 15% | 11% | 10% |

### Buffer Allocation

| Complexity | Base Buffer | Additional Risk Buffer |
|-----------|------------|----------------------|
| Simple | 15% | +5% if external dependencies |
| Moderate | 25% | +10% if cross-team dependencies |
| Complex | 35% | +15% if new technology/patterns |

### Team Size Impact

Adjust timeline based on team size:
- **1-2 developers**: Add 20-30% to development phase
- **3-5 developers**: Standard timeline
- **6+ developers**: Reduce development by 10-15% (but add coordination overhead)

### Capacity Adjustments

Account for:
- Holidays and PTO: Add 10% for typical year
- Parallel projects: Add 20% if team at <70% capacity for this feature
- New team members: Add 30% ramp-up time to their contribution

## Example Interaction

**User**: `/pm.workback 001 2024-12-01`

**Agent**: "I'll create a workback schedule for feature 001 targeting a launch date of December 1, 2024.

First, let me gather some information from the PRD at `prds/001-ai-code-review/prd.md`...

I can see this is a new AI-powered feature with cross-team dependencies. Let me ask a few questions to create an accurate schedule:

1. What's the team size for this project?
   - Option A: 1-2 developers (smaller team)
   - Option B: 3-5 developers (standard team)
   - Option C: 6+ developers (larger team)

2. What's the complexity level?
   - Based on the PRD, this seems **Moderate** (new AI integration, existing codebase)
   - Would you like to adjust this?

3. Team capacity?
   - Are there any known holidays or parallel projects affecting availability?"

**User**: "3-5 developers, moderate complexity, one major holiday in November"

**Agent**: "Perfect! Working backwards from December 1, 2024:

**Timeline Summary**:
- Total duration: 10 weeks (with 25% buffer)
- Start date: September 16, 2024
- Launch date: December 1, 2024

**Key Milestones**:
1. PRD Approval: Sept 20 (Week 1)
2. Design Review: Oct 4 (Week 3)
3. Development Complete: Nov 8 (Week 8)
4. Testing Complete: Nov 22 (Week 10)
5. Staging UAT: Nov 29 (Week 11)
6. Production Launch: Dec 1 (Week 12)

**Critical Path Items**:
- Design Review cannot slip past Oct 4 or dev phase compresses
- Testing must start by Nov 8 to have adequate time

I've allocated extra buffer around the November holiday period.

Generating `prds/001-ai-code-review/workback-schedule.md`..."

[Generate complete workback schedule document]

## Template Reference

Use template: `templates/workback-schedule.md`

## Related Commands

- `/pm.prd` - Create PRD with timeline section that feeds this schedule
- `/pm.tasks` - Generate work items to populate schedule phases
- `/pm.analyze` - Validate timeline assumptions
- Launch checklist - Reference for staging milestone details

## Common Adjustments

### If Timeline Too Aggressive

Suggest:
1. Reduce scope (defer P1/P2 features)
2. Add more team members (with ramp-up time)
3. Extend launch date
4. Reduce buffer (higher risk)

### If Timeline Too Conservative

Suggest:
1. Tighten phase durations based on team velocity
2. Parallelize more activities
3. Reduce buffer if low risk

### If Dependencies Cause Issues

Suggest:
1. Start dependent work earlier
2. Identify workarounds or alternatives
3. Escalate to unblock
4. Adjust critical path

## Integration Points

- **PRD Timeline Section**: Update PRD's "Timeline & Milestones" to match workback schedule
- **Work Items**: Tasks in ado-workitems.md should map to schedule phases
- **Launch Checklist**: Staging milestone links to launch-readiness.md checklist
- **Status Updates**: Weekly status section tracks progress against schedule

---
description: Execute full RIPER workflow for a feature
---

# Full RIPER Workflow

I'll guide you through the complete RIPER workflow for: $ARGUMENTS

## Workflow Phases

### Phase 1: RESEARCH
First, I'll use the research-innovate agent in RESEARCH sub-mode to understand the current state of the codebase and gather all necessary information.

### Phase 2: INNOVATE  
Next, I'll use the research-innovate agent in INNOVATE sub-mode to brainstorm different approaches and explore possibilities.

### Phase 3: PLAN
Then, I'll use the plan-execute agent in PLAN sub-mode to create detailed technical specifications that you can review.

**⚠️ APPROVAL GATE**: I will pause here for your explicit approval before proceeding.

### Phase 4: EXECUTE
Once approved, I'll use the plan-execute agent in EXECUTE sub-mode to implement exactly what was planned.

### Phase 5: REVIEW
Finally, I'll use the review agent to validate the implementation against the plan.

## Starting Workflow - Adaptive Mode

### Step 0: Complexity Assessment

First, let me assess task complexity and recall similar past tasks:

**Complexity Factors**:
- File count estimate: [1-2 / 3-5 / 6+]
- Architectural impact: [LOW / MEDIUM / HIGH]
- Ambiguity level: [CLEAR / SOME / SIGNIFICANT]

**Classification**:
- **SIMPLE**: 1-2 files, well-defined scope, low ambiguity
- **MODERATE**: 3-5 files, some design decisions, moderate ambiguity
- **COMPLEX**: 6+ files, architectural changes, high ambiguity

Checking memory: `/memory:recall similar to: $ARGUMENTS`

### Adaptive Phase Execution

Based on complexity assessment, I'll follow the appropriate workflow:

**For SIMPLE tasks**:
1. RESEARCH (1 iteration, convergence threshold: 7/10)
2. PLAN (streamlined)
3. EXECUTE (with substep validation)
4. REVIEW

**For MODERATE tasks**:
1. RESEARCH (up to 2 iterations, convergence threshold: 8/10)
2. INNOVATE (explore 2-3 approaches)
3. PLAN (detailed)
4. EXECUTE (with deep supervision)
5. REVIEW

**For COMPLEX tasks**:
1. RESEARCH (up to 3 iterations, convergence threshold: 9/10)
2. INNOVATE (extensive exploration)
3. PLAN (comprehensive with risk analysis)
4. EXECUTE (substep-by-substep with validation)
5. Mid-execution REVIEW (after 50% complete)
6. Final REVIEW

### Hierarchical Convergence Control

**Research Phase**: Continue iterations until convergence criteria met:
- Understanding confidence >= threshold
- All dependencies mapped
- Edge cases considered
- Context complete

**Execute Phase**: Validate after each substep (deep supervision):
- Check plan compliance
- Assess confidence (must be >= 7/10)
- Document any deviations
- Halt if validation fails

**Memory Tracking**: Save all confidence scores and iteration counts for future workflow optimization.

### Beginning Workflow

Let me begin with complexity assessment and RESEARCH phase for: $ARGUMENTS

[The appropriate agent will be invoked based on the current phase]
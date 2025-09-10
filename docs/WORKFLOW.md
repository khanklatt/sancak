<!-- FRAMEWORK FILE - DO NOT EDIT - This file contains workflow guidelines and process instructions -->

# Workflow Guidelines

## Development State Machine

The development process follows a state machine with four primary states:

```
BEGIN → REQUIREMENTS → TESTS → CODE → REQUIREMENTS (loop)
```

Each state can transition backward when gaps are discovered (failing tests, unclear requirements, implementation blockers).

## State Descriptions

### BEGIN
- **Entry Point:** New project or major feature addition
- **Activities:** Define project objective, gather initial context
- **Exit Condition:** Clear project objective defined
- **Next State:** REQUIREMENTS

### REQUIREMENTS  
- **Active Role:** Technical Product Manager
- **Activities:** 
  - Write/refine functional and non-functional requirements
  - Create architectural decision records
  - Assign states (DRAFT/APPROVED) and MVP tags
  - Perform gap analysis after development cycles
- **Exit Condition:** APPROVED, MVP requirements ready for implementation
- **Next State:** TESTS

### TESTS
- **Active Role:** Developer  
- **Activities:**
  - Generate test specifications from requirements
  - Create task lists for implementation
  - Write failing tests (TDD red phase)
- **Exit Condition:** Comprehensive test suite covering APPROVED, MVP requirements
- **Next State:** CODE

### CODE
- **Active Role:** Developer
- **Activities:**
  - Implement code to make tests pass (TDD green/refactor)
  - Update implementation notes and task status
  - Report test results
- **Exit Condition:** All tests passing for current milestone
- **Next State:** REQUIREMENTS (for milestone review)

## Requirement State Lifecycle

Requirements progress through these states:

- **DRAFT:** Initial requirement, needs refinement/approval
- **APPROVED:** Ready for test creation and implementation  
- **IMPLEMENTED:** Code written, tests passing, functionality complete
- **DEPRECATED:** No longer needed, marked for removal

### State Transitions

- DRAFT → APPROVED: Technical PM validates requirement is testable and necessary
- APPROVED → IMPLEMENTED: Developer completes implementation with passing tests
- Any State → DEPRECATED: Requirement determined unnecessary or obsolete
- IMPLEMENTED → DRAFT-{timestamp}: Requirement needs modification (creates new versioned requirement)

## MVP and Breadth-First Implementation

### MVP Tagging
- Requirements tagged with MVP get priority implementation
- MVP requirements form the "spine" of story mapping
- Implement breadth-first: get end-to-end functionality before depth

### Example Priority Order
```
1.1: APPROVED, MVP - Core user authentication
2.1: APPROVED, MVP - Basic data storage  
3.1: APPROVED, MVP - Simple user interface
1.2: APPROVED - Advanced authentication features
2.2: APPROVED - Data optimization
3.2: APPROVED - Enhanced UI features
```

## Milestone Management

### Completion Criteria
A milestone is complete when:
- All APPROVED, MVP requirements are IMPLEMENTED
- All associated tests are passing
- No critical blockers remain

### Milestone Review Process
1. **Technical PM Validation:**
   - Review remaining DRAFT/APPROVED requirements
   - Move successful implementations to IMPLEMENTED
   - Remove MVP tags from completed requirements
   - Identify requirements to DEPRECATE

2. **Gap Analysis:**
   - Analyze completed work for new insights
   - Create new DRAFT requirements for identified gaps
   - Promote DRAFTs to APPROVED with appropriate MVP tags

3. **Next Iteration Planning:**
   - Developer generates tasks for new APPROVED, MVP requirements
   - Process continues with TESTS state

## Failure Handling Protocol

### When Tests Fail
1. **Root Cause Analysis:** Is the test wrong or is the code wrong?
2. **Requirement Validation:** Does the failing test reflect the actual requirement?
3. **Implementation Review:** Is the code implementing what the test expects?
4. **Decision:** Fix code, fix test, or clarify requirement

### When Requirements Are Ambiguous
1. **Backward Transition:** CODE → REQUIREMENTS
2. **Clarification Process:** Technical PM refines requirement
3. **Test Update:** Developer updates tests based on clarified requirement
4. **Forward Progress:** Resume implementation

### When Architecture Decisions Block Progress
1. **Document Decision Point:** What needs to be decided and why?
2. **Options Analysis:** Document viable approaches with trade-offs
3. **ADR Creation:** Technical PM creates architectural decision record
4. **Implementation Guidance:** Update requirements based on architectural decision

## Scientific Method for Problem Solving

When unexpected outcomes occur:

1. **Observe:** Document exactly what happened vs. expected behavior
2. **Question:** Why did this unexpected outcome occur?
3. **Hypothesize:** Form testable theory about the cause
4. **Experiment:** Design specific test to validate hypothesis
5. **Analyze:** Evaluate experiment results
6. **Conclude:** If hypothesis confirmed, proceed; if not, form new hypothesis
7. **Escalate:** After 3 failed hypothesis cycles, pause and ask for human guidance

## Best Practices

### Requirement Writing
- Use active voice and specific verbs (shall, must, can)
- Include measurable acceptance criteria
- Reference external dependencies and constraints
- Keep requirements atomic (one testable concept per requirement)

### Test Writing  
- Reference specific requirement IDs
- Use Given-When-Then format for clarity
- Test both positive and negative cases
- Keep tests independent and repeatable

### Implementation
- Make tests pass with minimal code
- Refactor only when tests are passing
- Document architectural decisions as they're made
- Update task status frequently

### Documentation Maintenance
- Keep PROJECT.md as single source of truth
- Update states promptly as work progresses
- Maintain clean separation between role responsibilities
- Archive deprecated requirements rather than deleting
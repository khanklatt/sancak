# Role Definitions

## Technical Product Manager Role

### Responsibilities
- Write and maintain functional and non-functional requirements
- Create architectural decision records (ADRs)
- Manage requirement states and MVP prioritization
- Perform gap analysis and requirement refinement
- Validate completed implementations against requirements

### Editing Authority
- May edit: Requirements section, ADR section
- Must request role switch to edit: Test Specifications, Tasks, Implementation Notes

### Context Switching Rules
To edit sections owned by other roles, you must explicitly state:
"Switching to [ROLE] context to edit [SECTION]"

### Lifecycle Responsibilities
At completion of development milestones:
1. **Validation Phase:**
   - Review requirements still in DRAFT/APPROVED - determine if overlooked or should be DEPRECATED
   - Accept successful implementations by moving from APPROVED to IMPLEMENTED
   - Remove MVP attributes from IMPLEMENTED requirements

2. **Planning Phase:**
   - Perform gap analysis for next development iteration
   - Create new DRAFT requirements based on insights from completed sprint
   - Promote DRAFTs to APPROVED and assign MVP attributes for next iteration
   - Signal Developer role to generate tasks for APPROVED, MVP requirements

## Developer Role

### Responsibilities  
- Generate test specifications from requirements
- Create and maintain task lists for APPROVED, MVP requirements
- Implement code to make tests pass (TDD approach)
- Document implementation decisions and blockers
- Report test results for lifecycle management

### Editing Authority
- May edit: Test Specifications, Tasks, Implementation Notes, Test Results
- Must request role switch to edit: Requirements, ADRs

### Context Switching Rules
To edit sections owned by other roles, you must explicitly state:
"Switching to [ROLE] context to edit [SECTION]"

### Implementation Guidelines
- Write tests first, derived from requirements
- Implement code to make tests pass
- One test at a time approach (Kent Beck principle)
- Reference requirement IDs in all tests and code comments
- **Execute one subtask at a time** - do NOT start next subtask without user approval
- Update task list and relevant files section after each subtask
- Run full test suite before suggesting commits

### Task Execution Protocol
1. **Before starting:** Identify next incomplete subtask from task list
2. **During work:** Focus only on current subtask, implement minimal code to make tests pass
3. **After completion:**
   - Mark subtask as completed `[x]` in PROJECT.md
   - Update Relevant Files section with any new/modified files
   - Run full test suite to ensure nothing broke
   - If all subtasks under a parent task are complete, mark parent task `[x]`
4. **Commit suggestion:** If tests pass, suggest commit message with requirement reference
5. **Pause:** Wait for user approval before proceeding to next subtask

### Commit Message Format
Suggest commit messages in this format:
```
Implementation for Req. {requirement_id}: {brief description}

- {key change 1}
- {key change 2}
- Tests: {test status summary}
```

Example:
```
Implementation for Req. 1.1-20250910120000Z: Add OAuth2 authentication

- Created OAuth2 endpoint handler
- Added user session management
- Tests: All authentication tests passing (5/5)
```

### Failure Handling Protocol
When unexpected outcomes occur:
1. **Identify:** Document the unexpected outcome
2. **Hypothesize:** Form hypothesis about why it happened  
3. **Experiment:** Design testable experiment to validate hypothesis
4. **Test:** Execute experiment and evaluate results
5. **Iterate:** If same result after 3 attempts, pause and ask for guidance

## Role Transition Signals

### From Technical PM to Developer
"Requirements review complete. All APPROVED, MVP requirements are ready for implementation. Developer role should now generate tasks and begin TDD cycle."

### From Developer to Technical PM  
"Implementation milestone complete. The following requirements have been implemented and tested: [list]. Technical PM role should review for acceptance and plan next iteration."
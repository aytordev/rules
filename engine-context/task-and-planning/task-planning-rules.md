# Task Planning Rules – Standard for AI Agents

## Objective

This rule ensures that for every prompt or request received, the AI agent operates in two structured modes: **Planning Mode** and **Execution Mode**. The agent must always generate a detailed breakdown of tasks, explain the approach, and present an execution plan for user approval before implementing any solution.

---

## Operating Modes

### 1. Planning Mode

**Whenever a new prompt or project request is received:**

- The agent must **analyze the request** and break down the solution into a list of logical, actionable tasks.
- For each task, the agent must explain:
  - **What** will be done
  - **How** it will be accomplished (tools, methods, steps)
  - **What the expected outcome** or deliverable is
  - **Dependencies** on other tasks or external factors
  - **Estimated effort** and timeline
  - **Risk factors** and mitigation strategies
- The agent must organize all tasks into a **step-by-step execution plan** (ordered list or table), including dependencies if applicable.
- The agent must present the complete execution plan to the user, asking for review, validation, or approval before proceeding.

**Example structure:**

```
## Execution Plan for [Prompt/Project Name]

### Overview
Brief description of the overall objective and approach.

### Task Breakdown

1. **Task Name**
   - Description: Briefly explain what will be done.
   - Approach: Detail tools, frameworks, or techniques to be used.
   - Dependencies: [if any]
   - Estimated Effort: [time/complexity]
   - Risk Level: [Low/Medium/High]
   - Expected Outcome: Describe the expected deliverable or result.

2. **Next Task**
   ...

### Risk Assessment
- High-risk tasks and mitigation strategies
- Potential blockers and workarounds
- Quality assurance checkpoints

### Success Criteria
- Definition of done for the overall project
- Validation methods for each major deliverable
- Rollback procedures if needed
```

- At the end, include a prompt for the user:
  - "**Please review the execution plan and indicate which tasks you approve for execution, or suggest changes as needed.**"

---

### 2. Execution Mode

- Only after explicit user approval does the agent proceed to **Execution Mode**.
- The agent executes the approved tasks step by step, documenting progress, results, decisions, and any obstacles encountered.
- For each completed task, the agent must:
  - Update the task status in the execution plan
  - Document actual vs. estimated effort
  - Record any deviations from the original plan
  - Update relevant memory bank files
  - Validate completion against success criteria
- If unexpected complexity or new subtasks arise, the agent must pause, return to Planning Mode, and update the plan for new approval.
- Progress updates must be provided at regular intervals or upon request.

---

## Task Documentation

- For each prompt or project, create or update a file in the `memory-bank` folder called `tasks_[prompt-name].md`.
- Document in this file:
  - The original user request
  - The proposed execution plan
  - User approval/comments and any modifications
  - Task progress, completion notes, and final deliverables
  - Lessons learned and process improvements
  - Relevant links, references, or artifacts

**Task Documentation Template:**

```markdown
# Task Documentation: [Project Name]

## Original Request
[User's original prompt/request]

## Execution Plan
[Approved plan with task breakdown]

## User Feedback
[Approval status, comments, modifications requested]

## Execution Log
### [Date] - [Task Name]
- Status: [In Progress/Completed/Blocked]
- Progress: [Description of work done]
- Issues: [Any problems encountered]
- Next Steps: [What's planned next]

## Final Deliverables
[List of completed deliverables with links/references]

## Lessons Learned
[Process improvements, things to do differently next time]

## Metrics
- Planned vs. Actual Effort
- Task Completion Rate
- User Satisfaction Score
```

---

## User Approval Flow

- The agent **never proceeds to execution** or delivers code, scripts, documentation, or any action without first presenting the plan and obtaining explicit user approval.
- Approval can be:
  - **Full Approval**: Proceed with all tasks as planned
  - **Partial Approval**: Proceed only with specified tasks
  - **Conditional Approval**: Proceed with modifications or additional requirements
  - **Rejection**: Return to planning with feedback for revision
- This ensures traceability, expectation alignment, and full transparency in the workflow.

### Approval Documentation Requirements

All approvals must be documented with:
- Date and time of approval
- Specific tasks or modifications approved
- Any conditions or limitations
- User identifier/signature
- Next review checkpoint if applicable

---

## Emergency Procedures

### When Emergency Bypass is Permitted

In certain critical situations, the normal planning-execution workflow may be bypassed:

1. **Critical Security Incidents**
   - Active security exploits requiring immediate remediation
   - Data breach containment actions
   - System compromise response

2. **Production System Failures**
   - Complete system outages affecting users
   - Data corruption requiring immediate intervention
   - Critical service disruptions

3. **Urgent Regulatory Compliance**
   - Immediate compliance requirements with legal deadlines
   - Court orders or regulatory enforcement actions

### Emergency Execution Protocol

1. **Immediate Assessment** (within 15 minutes)
   - Classify the emergency level (Critical/High/Medium)
   - Determine if normal workflow can be followed
   - Document emergency justification

2. **Emergency Action** (if bypass is necessary)
   - Take minimum necessary action to address the emergency
   - Document all actions taken in real-time
   - Notify relevant stakeholders immediately
   - Create emergency task log in memory bank

3. **Post-Emergency Documentation** (within 2 hours)
   - Complete full task documentation retroactively
   - Update relevant memory bank files
   - Conduct emergency response review
   - Create proper execution plan for remaining work

4. **Follow-up Review** (within 24 hours)
   - Team review of emergency response
   - Process improvement recommendations
   - Update emergency procedures if needed

### Emergency Escalation Matrix

| Emergency Level | Response Time | Approval Required | Documentation Timeline |
|----------------|---------------|-------------------|----------------------|
| Critical | Immediate | Post-action | Within 1 hour |
| High | < 1 hour | Emergency contact | Within 2 hours |
| Medium | < 4 hours | Team lead | Within 4 hours |

---

## Quality Assurance and Validation

### Planning Phase Validation

Before presenting any execution plan, the agent must verify:
- All tasks are clearly defined and actionable
- Dependencies are identified and manageable
- Risk assessment is complete and realistic
- Success criteria are measurable and achievable
- Resource requirements are reasonable
- Timeline estimates are based on complexity analysis

### Execution Phase Validation

During execution, the agent must:
- Validate each completed task against success criteria
- Maintain task progress documentation
- Update memory bank files consistently
- Report blockers or deviations immediately
- Provide regular progress updates
- Conduct quality checks at defined checkpoints

### Completion Validation

Upon project completion, the agent must:
- Verify all deliverables meet acceptance criteria
- Update all relevant memory bank files
- Document lessons learned and process improvements
- Conduct final quality review
- Obtain user acceptance confirmation
- Archive project documentation properly

---

## Integration with Memory Bank

### Required Memory Bank Updates

During task execution, the following memory bank files must be updated as applicable:

1. **features.md** - When implementing new features
2. **fixes.md** - When resolving bugs or issues
3. **security.md** - When implementing security measures
4. **architecture.md** - When making architectural changes
5. **communication.md** - When modifying APIs or interfaces
6. **version.md** - When preparing releases
7. **project-status.md** - For overall project health updates

### Cross-Reference Requirements

All task documentation must include:
- References to relevant memory bank files
- Links to related issues, PRs, or external resources
- Cross-references to dependent or related tasks
- Version control commit references
- Artifact links (diagrams, documentation, etc.)

---

## Best Practices

### Planning Best Practices

- **Granular Task Definition**: Break complex work into manageable chunks (ideally 2-8 hours each)
- **Clear Acceptance Criteria**: Define what "done" means for each task
- **Risk-First Approach**: Identify and plan for potential issues upfront
- **Dependency Mapping**: Understand and document task relationships
- **Resource Planning**: Consider team capacity and skill requirements
- **Timeline Buffers**: Include reasonable estimates with contingency time

### Execution Best Practices

- **Incremental Progress**: Complete tasks in small, verifiable increments
- **Continuous Documentation**: Update progress and decisions in real-time
- **Quality Gates**: Implement validation checkpoints throughout execution
- **Stakeholder Communication**: Provide regular updates to relevant parties
- **Issue Escalation**: Report blockers quickly with proposed solutions
- **Learning Capture**: Document insights and improvements for future use

### Communication Best Practices

- **Clear Status Updates**: Use standardized status indicators (Not Started/In Progress/Completed/Blocked)
- **Visual Progress Tracking**: Use tables, charts, or dashboards when appropriate
- **Proactive Issue Reporting**: Communicate problems before they become critical
- **Solution-Oriented Updates**: Include proposed solutions with problem reports
- **Regular Checkpoint Reviews**: Schedule periodic plan reviews with stakeholders

---

## Metrics and Continuous Improvement

### Key Performance Indicators

Track the following metrics for process improvement:
- **Planning Accuracy**: Actual vs. estimated effort and timeline
- **Task Completion Rate**: Percentage of tasks completed as planned
- **Quality Metrics**: Defect rates, rework frequency
- **User Satisfaction**: Feedback scores and approval rates
- **Process Efficiency**: Time from planning to delivery
- **Risk Management**: Accuracy of risk predictions and mitigation effectiveness

### Process Improvement Cycle

1. **Regular Reviews**: Conduct weekly/monthly process reviews
2. **Metrics Analysis**: Analyze trends and identify improvement opportunities
3. **Stakeholder Feedback**: Collect and incorporate user feedback
4. **Process Updates**: Implement improvements to planning and execution procedures
5. **Training Updates**: Update team knowledge based on lessons learned
6. **Tool Enhancement**: Improve automation and supporting tools

---

## Integration with Development Tools

### Version Control Integration

- All task-related changes must be committed with descriptive messages
- Link commits to specific tasks in task documentation
- Use consistent branch naming conventions for task work
- Maintain clean commit history for auditability

### CI/CD Integration

- Integrate task validation into build pipelines
- Automate memory bank file validation
- Include task completion verification in deployment processes
- Generate automated progress reports from CI/CD metrics

### Project Management Integration

- Sync with external project management tools (Jira, GitHub Issues, etc.)
- Maintain bidirectional links between tasks and external tickets
- Export task metrics to project dashboards
- Integrate with team capacity planning tools

---

## Example Workflow

### Adding a New Feature

1. **User Prompt:** "Add user profile management with avatar upload functionality"

2. **Agent Planning Mode:**
   ```
   ## Execution Plan for User Profile Management Feature

   ### Overview
   Implement comprehensive user profile management including personal information editing and avatar upload with image processing.

   ### Task Breakdown
   1. **Database Schema Design**
      - Description: Design and implement user profile table extensions
      - Approach: PostgreSQL schema migrations using Prisma
      - Dependencies: None
      - Estimated Effort: 2 hours
      - Risk Level: Low
      - Expected Outcome: Migration scripts and updated Prisma schema

   2. **Backend API Development**
      - Description: Create REST endpoints for profile CRUD operations
      - Approach: Express.js routes with validation middleware
      - Dependencies: Task 1 completion
      - Estimated Effort: 6 hours
      - Risk Level: Medium
      - Expected Outcome: Documented API endpoints with tests

   3. **File Upload Service**
      - Description: Implement secure avatar image upload and processing
      - Approach: Multer for uploads, Sharp for image processing
      - Dependencies: Task 2 completion
      - Estimated Effort: 4 hours
      - Risk Level: High (security considerations)
      - Expected Outcome: Secure upload service with image optimization

   4. **Frontend Implementation**
      - Description: Build user profile management UI components
      - Approach: React components with form validation
      - Dependencies: Tasks 2 and 3 completion
      - Estimated Effort: 8 hours
      - Risk Level: Medium
      - Expected Outcome: Responsive profile management interface

   5. **Testing and Validation**
      - Description: Comprehensive testing of all components
      - Approach: Unit tests, integration tests, and manual testing
      - Dependencies: All previous tasks
      - Estimated Effort: 4 hours
      - Risk Level: Low
      - Expected Outcome: Test suite with >85% coverage

   ### Risk Assessment
   - File upload security: Implement strict validation and sanitization
   - Image processing performance: Use background jobs for large images
   - Data validation: Comprehensive input validation on all endpoints

   ### Success Criteria
   - Users can edit all profile information
   - Avatar upload works with common image formats
   - All security validations pass
   - Performance meets defined benchmarks
   ```

3. **User Approval:** User reviews and approves the plan with minor modifications

4. **Agent Execution Mode:** 
   - Executes tasks sequentially
   - Updates task documentation with progress
   - Updates memory bank files (features.md, backend.md, frontend.md, tests.md)
   - Provides regular status updates

5. **Completion:**
   - Final validation against success criteria
   - User acceptance confirmation
   - Documentation archival
   - Lessons learned capture

---

## Summary

**With this rule active, the agent always operates transparently, collaboratively, and approval-driven, separating Planning from Execution. All solutions are documented and tasks are tracked, ensuring clarity, alignment, and full control for the user while maintaining the flexibility to handle emergency situations when necessary.**

The planning-execution separation ensures that:
- All work is pre-approved and transparent
- Quality is built into the process from the start
- Risks are identified and mitigated early
- Progress is continuously tracked and communicated
- Emergency situations can be handled without compromising overall process integrity

---

**END OF FILE**
# Context Refresh Template

Use this template when you need to refresh an AI agent's context during long conversations or when starting a new session.

## Template

```markdown
## Context Refresh

I need to refresh the context for our project. Please read the following files to understand our current state:

**Required Reading**:
- action_plan.md (project overview and current phase)
- notes.md (important decisions and context)
- progress_log.md (what's completed and what's next)

**Current Situation**:
- **Project**: [Brief project description]
- **Current Phase**: [What phase from action plan we're on]
- **Last Completed**: [What was just finished]
- **Immediate Goal**: [What needs to happen next]

**Specific Request**:
[What you want the agent to do after refreshing context]

Please confirm you understand the current state, then proceed with [specific task].
```

## Usage Examples

### Mid-Conversation Refresh
```markdown
## Context Refresh

I notice our conversation is getting long and you might be losing track of our goals. Please read the following files to understand our current state:

**Required Reading**:
- action_plan.md (project overview and current phase)
- notes.md (important decisions and context)

**Current Situation**:
- **Project**: Task management API with multi-tenant architecture
- **Current Phase**: Phase 3 - Core Task Management (from action plan)
- **Last Completed**: User authentication and organization setup
- **Immediate Goal**: Implement task CRUD operations with proper permissions

**Specific Request**:
Create the Task model with proper MongoDB schema including organization isolation and role-based access.

Please confirm you understand the current state, then proceed with the Task model implementation.
```

### New Session Start
```markdown
## Context Refresh

I'm continuing work on a project from a previous session. Please read the following files to understand where we left off:

**Required Reading**:
- action_plan.md (project overview and development phases)
- progress_log.md (completed work and current status)
- notes.md (important architectural decisions)

**Current Situation**:
- **Project**: E-commerce checkout system with payment processing
- **Current Phase**: Phase 4 - Payment Integration (from action plan)
- **Last Completed**: Shopping cart functionality and user address management
- **Immediate Goal**: Integrate Stripe payment processing with order creation

**Git Status**: 
- Latest commit: "Phase 3: Shopping cart and address management complete"
- Ready to start payment integration

**Specific Request**:
Implement Stripe payment intent creation with proper error handling and webhook verification.

Please confirm you understand our project state and the current objectives, then proceed with the Stripe integration.
```

### Recovery from Confusion
```markdown
## Context Refresh

I think there's been some confusion about our project requirements. Let me reset the context:

**Required Reading**:
- action_plan.md (to understand the original scope and approach)
- notes.md (key decisions that might have been forgotten)

**Clarification Needed**:
You seem to be [describing the confusion], but actually we're building [correct description].

**Current Situation**:
- **Project**: [Correct project description]
- **Current Phase**: [What we're actually working on]
- **Key Constraint**: [Important limitation that was missed]
- **Immediate Goal**: [What we need to focus on]

**Specific Request**:
Please re-read the context files, then let's continue with [specific corrected task].

I want to make sure we're aligned before proceeding further.
```

---

**Usage**: This template helps maintain project continuity across long conversations and multiple sessions. It's essential for preventing token rot and keeping agents focused on the right objectives.

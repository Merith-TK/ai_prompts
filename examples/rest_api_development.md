# Example: Building a REST API with an AI Agent

This example demonstrates the proven file-based methodology for building a REST API with persistent context and effective agent collaboration.

## Initial Prompt

```markdown
I want to build a REST API for a task management application. Please ask any clarifying questions before we start - I'd rather answer questions upfront than fix misunderstandings later.

**Context**: 
- Building a personal task manager
- Need to support multiple users  
- Tasks should have categories and due dates
- This will be used by small teams (5-15 people per instance)

**Technology Stack**: 
- Node.js with Express
- MongoDB for database
- JWT for authentication

**Initial Requirements**:
- User registration and login
- CRUD operations for tasks
- Task categories
- Due date tracking
- Basic authentication
- Role-based permissions (admin/user)

**My Approach**: We'll create an action plan first, then work through it phase by phase with git snapshots. You may ask questions if you think it's necessary.

Can you help me plan this project?
```

## Expected Agent Response

The agent should ask clarifying questions like:

```markdown
I'll help you build this task management API! Before creating the action plan, I have some questions to ensure I understand your vision:

1. **User roles**: You mentioned admin/user roles - what specific permissions should each have?
2. **Task categories**: Should categories be predefined, user-created, or both?
3. **Team structure**: How do you envision multiple users sharing tasks? Per-team isolation or shared workspace?
4. **Due dates**: Any specific requirements like notifications, overdue handling, recurring tasks?
5. **Authentication**: Just JWT or do you need refresh tokens, password reset, etc.?
6. **Database**: Any specific MongoDB schema preferences or should I design from scratch?

Once I understand these details, I'll create a comprehensive action_plan.md file that we can reference throughout development.
```

## User's Comprehensive Response

```markdown
Great questions! Here's the comprehensive picture:

**USER ROLES**: 
- Admin: Can manage all tasks, users, and categories for their team
- User: Can only create/edit their own tasks, view team tasks (read-only)
- Logic: Prevents team members from accidentally modifying each other's work while maintaining visibility

**TASK CATEGORIES**:
- Mix of both: System defaults (Work, Personal, Urgent) + user-created custom categories
- Admin can create team-wide categories, users can create personal ones
- Example: Admin creates "Client Projects", user creates "Learning Goals"

**TEAM STRUCTURE**:
- Each organization is isolated (multi-tenant)
- Users belong to one organization, see only their org's data
- Think Slack workspaces - complete separation between different companies

**DUE DATES**:
- Basic due date tracking for now
- No notifications yet (future feature)
- Just need to identify overdue tasks in queries
- No recurring tasks in v1

**AUTHENTICATION**:
- JWT with refresh tokens
- Password reset via email (use nodemailer)
- 15min access token, 7day refresh token

**DATABASE**:
- Design from scratch, but keep it normalized
- Consider: organizations, users, tasks, categories collections
- Use MongoDB's ObjectId references

Does this help clarify the concept? Please create the action plan and let's start building!
```

## Action Plan Creation

The agent should then create an `action_plan.md` file:

```markdown
# Task Management API - Action Plan

## Project Overview
Multi-tenant task management API with role-based permissions, supporting small teams with isolated workspaces.

## Technology Stack
- Node.js + Express
- MongoDB with Mongoose
- JWT (access + refresh tokens)
- bcryptjs for password hashing
- nodemailer for password reset

## Database Schema
- Organizations (teams/companies)
- Users (linked to organization)
- Tasks (linked to user and organization) 
- Categories (system + custom)

## Development Phases

### Phase 1: Project Setup
- [ ] Initialize Node.js project with dependencies
- [ ] Set up Express server with basic middleware
- [ ] Configure MongoDB connection
- [ ] Create environment variables setup
- [ ] Set up basic error handling

### Phase 2: Authentication System  
- [ ] Create User and Organization models
- [ ] Implement registration (creates org + admin user)
- [ ] Implement login with JWT generation
- [ ] Add refresh token functionality
- [ ] Create password reset flow

### Phase 3: Core Task Management
- [ ] Create Task and Category models
- [ ] Implement task CRUD operations
- [ ] Add category management
- [ ] Implement role-based permissions middleware

### Phase 4: Advanced Features
- [ ] Add filtering and sorting for tasks
- [ ] Implement overdue task identification
- [ ] Add user management (admin features)
- [ ] Create comprehensive error handling

### Phase 5: Testing & Documentation
- [ ] Write unit tests for core functions
- [ ] Create integration tests for API endpoints
- [ ] Generate API documentation
- [ ] Final testing and bug fixes
```

## Implementation Workflow

### Step-by-Step Execution

```markdown
**User**: "Perfect action plan! Let's start with Phase 1. Please work on the project setup."

**Agent**: [Creates project structure, package.json, basic server setup]

**User**: "Great! Server is running on port 3000. Let's git snapshot this and move to Phase 2."

**Command**: git add . && git commit -m "Phase 1: Basic project setup complete"

**User**: "Now let's implement the User and Organization models from Phase 2."

**Agent**: [Implements Mongoose models with proper relationships and validation]

**User**: "Models look good. Let's test the registration endpoint and then snapshot."

**Agent**: [Creates registration route, tests with sample data]

**User**: "Registration works! One issue - I think there was a mix up with the organization creation. 
When a user registers, if they provide an organization name that already exists, they should 
join that org instead of creating a new one. Here's the logic I'm thinking:

FLOW: User registers → Check if org exists → If yes, add user to existing org → If no, create new org + make user admin
REASONING: Prevents duplicate organizations when team members sign up separately
CONSTRAINT: Only allow joining if org has < 50 users (prevent abuse)

Can you update the registration logic?"

**Agent**: [Updates registration with org existence check and user limits]
```

## Key Success Factors Demonstrated

1. **Encouraging Questions**: User explicitly welcomed clarifying questions upfront
2. **Comprehensive Answers**: Detailed responses with context, examples, logic, and constraints  
3. **File-Based Memory**: Action plan stored in persistent file to prevent token rot
4. **Phase-by-Phase Execution**: Breaking complex project into manageable git-tracked phases
5. **Proactive Clarification**: User stopped and clarified when agent misunderstood requirements
6. **Specific Requests**: Each phase had clear, testable objectives

## Methodology Highlights

### Question-Driven Start
- ✅ Agent asked 6 specific clarifying questions
- ✅ User provided comprehensive answers with reasoning
- ✅ Clear understanding established before coding began

### File-Based Context Management  
- ✅ `action_plan.md` created for persistent reference
- ✅ Agent can reference plan throughout development
- ✅ No information lost to token rot

### Iterative Development with Git
- ✅ Each phase ends with git snapshot
- ✅ Safe experimentation with rollback capability
- ✅ Clear progress tracking

### Effective Communication Patterns
- ✅ "I think there was a mix up..." for corrections
- ✅ Context + Examples + Logic + Constraints in clarifications
- ✅ Testing and validation at each step

## Common Pitfalls Avoided

- ❌ Starting coding without sufficient clarification
- ❌ Vague requirements leading to wrong assumptions  
- ❌ No persistent context (token rot vulnerability)
- ❌ Monolithic implementation attempts
- ❌ Not testing intermediate steps
- ❌ Poor communication when requirements misunderstood

## Token Rot Prevention in Action

**If conversation gets long, user can refresh context:**
```markdown
"Please read the action_plan.md file to refresh context about this project, 
then continue with Phase 3 implementation."
```

**If starting new conversation:**
```markdown
"I'm continuing work on the task management API. Please read:
- action_plan.md (project overview and current phase)
- Check git log for completed phases

We're currently working on Phase 3: Core Task Management. 
Let's implement the Task model with proper organization isolation."
```

## Final Result

A production-ready REST API with:
- ✅ Multi-tenant architecture with data isolation
- ✅ Role-based authentication (admin/user permissions)
- ✅ JWT with refresh token implementation
- ✅ Comprehensive task management (CRUD + categories)
- ✅ Password reset functionality
- ✅ Proper error handling and validation
- ✅ Git history with clear phase progression
- ✅ Persistent documentation for future development

## AI Agent Interaction Patterns

### For AI Models Reading This:
When working with users on similar projects:

1. **ASK CLARIFYING QUESTIONS** before coding - users prefer this approach
2. **REQUEST COMPREHENSIVE DETAILS** about business logic, user flows, and constraints
3. **CREATE PERSISTENT FILES** like action_plan.md for context that survives token limits
4. **WORK IN PHASES** with git snapshots between major features
5. **EXPECT CORRECTIONS** - users will stop and clarify when you misunderstand
6. **REFERENCE PLAN FILES** throughout development to maintain focus

### For Humans Reading This:
When working with AI agents on projects:

1. **WELCOME QUESTIONS** explicitly - better to clarify upfront than fix later
2. **PROVIDE CONTEXT + EXAMPLES + LOGIC** in your answers, not just requirements
3. **CREATE ACTION PLANS** in files that agents can reference persistently  
4. **WORK ITERATIVELY** with git snapshots for safe experimentation
5. **INTERRUPT AND CLARIFY** when you see the agent getting confused
6. **TEST FREQUENTLY** - validate each phase before moving forward

---

*This example demonstrates how combining question-driven planning, file-based context management, and iterative development creates highly effective AI agent collaborations.*

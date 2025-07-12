# Example: Building a REST API with an AI Agent

This example demonstrates the proven file-based methodology for building a REST API with persistent context and effective agent collaboration.

> **📝 Important Note**: You don't need to follow the exact structured format shown below. The key is to include all the relevant information and separate different concepts clearly. You can explain your requirements conversationally, as long as you cover the context, objectives, constraints, and technical details. The purpose of the agent's clarifying questions is to ensure nothing gets misunderstood - so provide detail where possible!

## Initial Prompt

```markdown
I want to build a REST API for a task management application. Please ask any clarifying questions before we start - I'd rather answer questions upfront than fix misunderstandings later.

**Context**: 
I'm building a personal task manager that needs to support multiple users. Think of it like a simplified version of Asana or Trello, but focused on small teams of 5-15 people per instance. Users will create tasks, assign them to team members, categorize them, and set due dates. 

**Technology Stack**: 
I want to use Node.js with Express for the backend, MongoDB for the database, and JWT for authentication. I'm comfortable with these technologies and have used them before, but I'm not sure about the best way to structure a multi-user application.

**What I'm envisioning**:
- Users can register and create an account
- When they register, they either join an existing organization or create a new one
- Users can create tasks for themselves or assign them to teammates
- Tasks should have categories (both system defaults and custom ones)
- Due dates with basic tracking (no notifications yet, just identification of overdue items)
- Basic role system - admins can manage the team, regular users can manage their own tasks

**My Approach**: I like to work systematically, so let's create an action plan first and then work through it step by step. I'll use git to snapshot our progress at each major milestone. You may ask questions if you think it's necessary.

Can you help me plan this project and get started?
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
Great questions! Here's the comprehensive picture I have in mind:

**USER ROLES**: 
You asked about admin vs user permissions - here's how I envision it working. Admins should be able to manage the entire team: they can see all tasks, edit anyone's tasks, manage team members (add/remove people), and create organization-wide task categories. Regular users can create and edit their own tasks, assign tasks to teammates, and see all team tasks but only edit their own. The logic here is to prevent team members from accidentally messing up each other's work while still maintaining visibility for collaboration.

**TASK CATEGORIES**:
I want a mix of both predefined and custom categories. The system should come with some sensible defaults like "Work", "Personal", "Urgent" - things that most teams will use. But then admins should be able to create team-wide categories like "Client Projects" or "Marketing Tasks", and individual users should be able to create their own personal categories like "Learning Goals" or "Side Projects". This gives flexibility without overwhelming new users.

**TEAM STRUCTURE**:
This is really important - I need complete data isolation between different organizations. Think of it like Slack workspaces where each company/team has their own completely separate environment. When user@company-a.com logs in, they should only see Company A's tasks, users, and categories. User@company-b.com should have no idea Company A even exists. This prevents any data leakage between different client organizations.

**DUE DATES**:
Keep it simple for version 1. I just need basic due date tracking where we can identify which tasks are overdue in our queries. No email notifications, no recurring tasks, no complex scheduling - just "this task is due on this date" and the ability to see "these tasks are overdue". We can add fancy notification features later.

**AUTHENTICATION**:
I want proper security with both access and refresh tokens. Short-lived access tokens (maybe 15 minutes) for API calls, and longer refresh tokens (7 days) so users don't get constantly logged out. Also need password reset functionality using email - I can use nodemailer for that since I've used it before.

**DATABASE DESIGN**:
Please design the schema from scratch, but keep it normalized and think about the relationships. I'm thinking we'll need collections for organizations, users, tasks, and categories. Use MongoDB's ObjectId references to link them together properly.

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
join that org instead of creating a new one. Let me explain the logic I'm thinking:

So here's the flow I want: User fills out registration → System checks if organization name already exists → If yes, add the user to that existing organization → If no, create new organization and make the user an admin of it.

The reasoning behind this is to prevent duplicate organizations when team members sign up separately. Like if John from Acme Corp registers first, he creates 'Acme Corp' organization. Then when Jane from the same company registers later and also puts 'Acme Corp' as her organization, she should join John's existing organization rather than creating 'Acme Corp (2)' or something.

One constraint though - let's add a user limit check. Only allow joining existing organizations if they have less than 50 users. This prevents abuse where random people try to join organizations they shouldn't have access to.

Can you update the registration logic to handle this?"

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

# Agent Task Template

Use this template for complex development tasks that benefit from the file-based methodology and persistent context.

## Template

```markdown
## Project Context
**Project Type**: [Web app, CLI tool, data analysis, microservice, etc.]
**Technology Stack**: [Languages, frameworks, databases, tools]
**Current State**: [What's already built, what's working, recent progress]
**Overall Goals**: [Business objectives, user needs, technical vision]

## Current Objective
[What you're trying to accomplish in this session - be specific]

## Detailed Requirements
**Functional Requirements**:
- [What the feature should do]
- [User interactions and workflows] 
- [Data handling and persistence]

**Technical Requirements**:
- [Performance expectations]
- [Security considerations]
- [Integration needs]
- [Compatibility requirements]

**Constraints**:
- [Time limitations]
- [Resource limitations]
- [Existing code patterns to follow]
- [Team conventions and style guides]

## Questions Encouraged
Please ask clarifying questions about any requirements, technical details, or implementation approaches. You may ask if you think it's necessary.

## Approach
We'll create an action plan first, then work through it phase by phase with git snapshots for safe progress tracking.

## Success Criteria
[How you'll know the task is complete and working correctly]

## Context Files
[List any relevant files the agent should examine or reference]
- action_plan.md (if continuing previous work)
- [other relevant files]

## Next Steps
[What comes after this task, how it fits the bigger picture]
```

## Usage Example

```markdown
## Project Context
**Project Type**: Multi-tenant SaaS task management application
**Technology Stack**: Node.js, Express, MongoDB, JWT authentication, React frontend
**Current State**: User registration/login working, basic task CRUD implemented, needs team collaboration features
**Overall Goals**: Enable small teams (5-15 people) to collaborate on tasks with role-based permissions and data isolation

## Current Objective
Implement real-time notifications system for task updates, assignments, and due date reminders

## Detailed Requirements
**Functional Requirements**:
- Users receive notifications when assigned to tasks
- Admins get notified of overdue tasks in their organization
- Real-time updates when task status changes
- Email notifications for important events (optional toggle)
- Notification history and mark-as-read functionality

**Technical Requirements**:
- Use WebSocket connections for real-time updates
- Support both in-app and email notifications
- Scalable to 1000+ concurrent users per server
- Database-backed notification persistence
- Mobile-responsive notification UI

**Constraints**:
- Must work with existing authentication system
- Follow established MongoDB schema patterns
- Use existing email service (nodemailer setup)
- Maintain organization data isolation

## Questions Encouraged
Please ask clarifying questions about notification types, real-time architecture, or database design. You may ask if you think it's necessary.

## Approach
We'll create an action plan first, then work through it phase by phase with git snapshots for safe progress tracking.

## Success Criteria
- Users receive real-time notifications for relevant events
- Notification system scales without performance issues
- Email notifications work reliably
- All notifications respect organization boundaries
- Clean, intuitive notification UI

## Context Files
- action_plan.md (reference previous development phases)
- models/User.js (existing user schema)
- models/Task.js (current task structure)
- middleware/auth.js (authentication patterns)

## Next Steps
After notifications, we'll implement advanced task filtering and team analytics dashboard
```

---

**Usage**: This template is ideal for complex features that require planning, multiple implementation phases, and coordination with existing code. It encourages comprehensive requirement gathering and systematic development.

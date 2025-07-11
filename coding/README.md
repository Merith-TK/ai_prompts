# Coding Prompts

Collection of prompts for programming and development tasks using proven AI agent methodologies.

## Core Principles

1. **Always encourage questions** - "You may ask if you think it's necessary"
2. **Create action plans** in files for persistent context
3. **Work in phases** with git snapshots
4. **Provide comprehensive context** when clarifying requirements
5. **Use file-based memory** to prevent token rot

## Categories

### Code Generation
- Function/method creation with comprehensive requirements
- Class implementation with design patterns
- API endpoint development with authentication/validation
- Database schema design with relationships and constraints

### Code Review & Debugging  
- Error analysis with full context and stack traces
- Code optimization with performance requirements
- Security review with threat model considerations
- Performance improvement with specific metrics

### Architecture & Design
- System design with scalability requirements
- Database design with data access patterns
- API design with versioning and documentation
- Code organization with team collaboration in mind

### Testing
- Unit test creation with coverage requirements
- Integration test development with realistic scenarios
- Test strategy planning with CI/CD integration
- Mock implementation with behavior verification

## Effective Coding Prompts

### Basic Structure
```markdown
**Context**: [Project type, tech stack, current state]
**Task**: [Specific coding objective]
**Requirements**: [Performance, security, maintainability needs]
**Questions Welcome**: Please ask any clarifying questions before starting
**Expected Output**: [Format, documentation level, testing needs]
```

### Advanced Structure (For Complex Features)
```markdown
**Project Context**: [Overall project goals and constraints]
**Current Phase**: [What's been built, what's working]
**Immediate Task**: [Specific feature to implement]
**Business Logic**: [Why this feature exists, how it fits the bigger picture]
**Technical Requirements**: [Performance, security, integration needs]
**Questions Encouraged**: Please ask about any unclear requirements
**Deliverables**: [Code, tests, documentation expectations]
**Next Steps**: [How this fits into the broader development plan]
```

## Example: Authentication Middleware

### Effective Prompt
```markdown
**Context**: Building a multi-tenant SaaS task management API using Node.js/Express and MongoDB
**Current State**: User and Organization models implemented, basic registration working
**Task**: Create JWT authentication middleware for protecting API routes
**Business Logic**: 
- Each request needs user identity for data isolation
- Support both access tokens (15min) and refresh tokens (7 days)
- Admin vs User role checking for certain endpoints
**Technical Requirements**:
- Validate JWT signature and expiration
- Extract user_id and org_id from token
- Attach user object to req.user for downstream use
- Handle expired tokens gracefully (return 401 with refresh instruction)
- Support role-based access checking
**Questions Welcome**: Please ask about token structure, error handling preferences, or any other details
**Expected Output**: Complete middleware function with comprehensive error handling and TypeScript types
```

### Agent Should Ask Questions Like:
```markdown
Great! Before implementing the JWT middleware, I have some clarifying questions:

1. **Token Structure**: What claims do you include in your JWT? (user_id, org_id, role, etc.)
2. **Error Responses**: Do you have a standard error response format I should follow?
3. **Role Checking**: Should this middleware handle role validation, or separate middleware?
4. **Refresh Flow**: When access token expires, should I return specific refresh instructions?
5. **Logging**: Any security logging requirements for failed auth attempts?
6. **Development Mode**: Need any special handling for development/testing?

Once I understand these details, I'll implement the middleware with proper error handling.
```

## Working with Existing Code

### Code Analysis Prompt
```markdown
**Context**: I have an existing [language/framework] project that needs [specific improvement]
**Request**: Please examine the codebase and tell me what you think each major component does
**Approach**: Make your best guess about the architecture, data flow, and main functionality
**Questions Welcome**: Ask clarifying questions about anything that's unclear
**Next Step**: Once you understand the codebase, we'll create an action plan for the improvements
```

### Follow-up Clarification Pattern
```markdown
**Feedback on your analysis**:

✅ **CORRECT**: [What the agent got right about the codebase]
❌ **CORRECTIONS**: [What needs to be fixed in their understanding]  
📚 **ELABORATIONS**: [Additional context for areas they missed]

**Business Context**: [Why the code exists, what problem it solves]
**Current Pain Points**: [What's not working well, what needs improvement]
**Goals**: [What the improved version should accomplish]

Now let's create an action plan for the improvements.
```

## File-Based Development Workflow

### 1. Create Action Plan
```markdown
"Please create an action_plan.md file for implementing [feature]. Include:
- Current state assessment
- Step-by-step implementation phases  
- Testing strategy for each phase
- Git commit points
- Potential risks and mitigation"
```

### 2. Phase-by-Phase Execution
```markdown
"Let's work on Phase 1 from the action plan. Please reference the action_plan.md file for context and implement [specific component]."
```

### 3. Git Snapshots
```markdown
"Great! Phase 1 is working. Let's commit this progress:
`git add . && git commit -m 'Phase 1: [description] complete'`

Now let's move to Phase 2."
```

### 4. Context Refresh (When Needed)
```markdown
"Please read the action_plan.md file to refresh context about this project, then continue with [specific task]."
```

## Advanced Techniques

### Progressive Enhancement
```markdown
"Let's build this feature in stages:
1. **Basic Implementation**: Core functionality, minimal error handling
2. **Validation Layer**: Input validation and basic error responses  
3. **Security Hardening**: Rate limiting, input sanitization, logging
4. **Performance Optimization**: Caching, query optimization, monitoring
5. **Testing Suite**: Unit tests, integration tests, edge cases

Please start with stage 1 and ask questions about the requirements."
```

### Debugging Approach
```markdown
"I'm getting [specific error] when [specific action]. Here's the relevant code:
[paste code]

Here's the full error message:
[paste error and stack trace]

**Context**: [What you were trying to accomplish]
**Expected Behavior**: [What should happen]
**Actual Behavior**: [What's happening instead]
**Environment**: [OS, Node version, relevant package versions]

Please help me debug this issue."
```

---

*These patterns have been tested and refined through real-world agent collaborations. They emphasize clear communication, persistent context, and iterative development for maximum effectiveness.*

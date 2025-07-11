# Code Analysis Template

Use this template when you want an AI agent to understand existing code before making modifications.

## Template

```markdown
## Context
**Project Type**: [Brief description of what the project does]
**Technology Stack**: [Languages, frameworks, key libraries]
**Analysis Goal**: [What you want to understand or improve]

## Request
Please examine the codebase and tell me what you think each major component does. Make your best guess about:

1. **Overall Architecture**: How the system is structured
2. **Data Flow**: How information moves through the application  
3. **Main Components**: What each file/module is responsible for
4. **Integration Points**: How different parts connect
5. **Business Logic**: What problem this code solves

## Instructions
- Look at file structure, imports, and function names
- Explain your reasoning for each assessment
- Ask questions about anything that's confusing or unclear
- Don't worry about being 100% correct - I'll provide clarifications

## Next Steps
After your analysis, I'll provide feedback and we'll create an action plan for [specific improvements/features].

## Files to Focus On
[List key files or directories the agent should prioritize]
- [file1.js] 
- [directory/] 
- [config files]
```

## Usage Example

```markdown
## Context
**Project Type**: Personal finance tracking web application
**Technology Stack**: Python Flask backend, SQLite database, vanilla JavaScript frontend
**Analysis Goal**: Need to add expense categorization and budget alerts

## Request
Please examine the codebase and tell me what you think each major component does. Make your best guess about:

1. **Overall Architecture**: How the system is structured
2. **Data Flow**: How transactions are processed and stored
3. **Main Components**: What each Python module handles
4. **Integration Points**: How frontend and backend communicate
5. **Business Logic**: How expense tracking and calculations work

## Instructions
- Look at file structure, imports, and function names
- Explain your reasoning for each assessment  
- Ask questions about anything that's confusing or unclear
- Don't worry about being 100% correct - I'll provide clarifications

## Next Steps
After your analysis, I'll provide feedback and we'll create an action plan for adding smart expense categories and budget monitoring.

## Files to Focus On
- app.py (main Flask application)
- models/ (database models)
- static/js/main.js (frontend logic)
- templates/ (HTML structure)
```

---

**Usage**: This template helps agents understand existing code before making changes, leading to better architectural decisions and fewer breaking modifications.

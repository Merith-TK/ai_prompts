# How to Avoid Token Rot

## Table of Contents
- [What is Token Rot?](#what-is-token-rot)
- [The File-Based Solution](#the-file-based-solution)
- [Proven Workflow for AI Agents](#proven-workflow-for-ai-agents)
- [Working with Existing Code](#working-with-existing-code)
- [Building New Projects](#building-new-projects)
- [Advanced Techniques](#advanced-techniques)

## What is Token Rot?

**Token rot** happens when AI agents start forgetting earlier context in long conversations. Instead of fighting it with conversation management, the solution is **external memory** - using files to maintain persistent context.

### Core Problem
- AI agents have limited context windows
- Long conversations lose early important information
- Agents start giving generic or contradictory responses

## The File-Based Solution

Instead of managing conversation length, create **persistent files** that the agent can reference:

### Key Files to Create
1. **`notes.md`** - Running notes of decisions, context, and important information
2. **`action_plan.md`** - Detailed step-by-step plan for the project
3. **`progress_log.md`** - What's been completed, what's next, current status

### Why This Works
- Files persist beyond conversation limits
- Agent can re-read context when needed
- No information gets lost to token rot
- Easy to restart conversations without losing progress

## Proven Workflow for AI Agents

This workflow has been tested and refined for maximum effectiveness:

### Step 1: Code Understanding (For Existing Projects)
```markdown
"Please look over every file in this project and make your best guess about what this code does. 
Explain in detail what you think each major component accomplishes."
```

**Then in a single follow-up message:**
- ✅ Correct where the agent was wrong
- ✅ Affirm where it was right  
- ✅ Elaborate on areas it didn't fully understand

### Step 2: Planning Phase
```markdown
"Let's discuss what I want to build/modify. We're creating an ACTION PLAN first - 
do NOT modify any code yet. Just planning."
```

### Step 3: Create the Action Plan File
```markdown
"Write this action plan to a file called 'action_plan.md'. This will be our 
persistent reference that won't get lost to token rot."
```

### Step 4: Execute in Phases
For each phase of the action plan:

1. **Work on current phase**
2. **Git snapshot** (`git add . && git commit -m "Phase X complete"`)
3. **Verify functionality** - test that everything works as intended
4. **Create tests** if needed for validation
5. **Allow agent to fix issues** to meet plan expectations
6. **Git snapshot** again
7. **Move to next phase**

### Step 5: Reference System
Always remind the agent:
```markdown
"Remember to reference the action_plan.md file for context about what we're building 
and where we are in the process."
```

## Working with Existing Code

### Initial Code Analysis
```markdown
"Please examine all files in this project. For each major component, tell me:
1. What you think this code does
2. How the different parts work together  
3. What the main functionality appears to be"
```

### Single Correction Message
After the agent's analysis, provide one comprehensive response:
```markdown
"Here's my feedback on your analysis:

✅ CORRECT: [List what the agent got right]
❌ CORRECTIONS: [What needs to be fixed]
📚 ELABORATIONS: [Additional context for areas it missed]

Now let's proceed with planning."
```

## Building New Projects

### Project Initialization
1. **Discuss requirements** - What you want to build
2. **Create action plan** - Agent writes detailed steps to `action_plan.md`
3. **Execute phases** - Work through plan systematically
4. **Git snapshots** - Commit after each major milestone

### Template Action Plan Structure
```markdown
# Project Action Plan

## Overview
[Project description and goals]

## Technology Stack
[Languages, frameworks, tools]

## Phase 1: Setup
- [ ] Initialize project structure
- [ ] Set up dependencies
- [ ] Create basic configuration

## Phase 2: Core Features
- [ ] Implement main functionality
- [ ] Add error handling
- [ ] Create basic tests

## Phase 3: Enhancement
- [ ] Add advanced features
- [ ] Optimize performance
- [ ] Complete testing

## Phase 4: Finalization
- [ ] Documentation
- [ ] Final testing
- [ ] Deployment preparation
```

## Advanced Techniques

### File-Based Memory System
Create these files for persistent context:

**`notes.md`**
```markdown
# Project Notes

## Key Decisions
- [Important architectural choices]

## Current Status  
- [What's working, what's not]

## Next Steps
- [Immediate priorities]
```

**`progress_log.md`**
```markdown
# Progress Log

## Completed
- [✅] Feature A implemented
- [✅] Tests passing

## In Progress  
- [🔄] Feature B development

## Blocked/Issues
- [❌] Issue with database connection
```

### Recovery from Token Rot
If you notice the agent forgetting context:

```markdown
"Please read the action_plan.md and notes.md files to refresh your context about 
this project, then continue with the current task."
```

### Starting Fresh Conversations
When beginning a new session:

```markdown
"I'm continuing work on [project name]. Please read:
- action_plan.md (for project overview and current phase)
- notes.md (for important context and decisions)  
- progress_log.md (for current status)

Then let's proceed with [specific task]."
```

## Why This Method Works

### Benefits
- **Persistent memory** beyond conversation limits
- **Structured approach** prevents confusion
- **Git snapshots** allow safe experimentation
- **Modular execution** makes complex projects manageable
- **Easy recovery** from token rot or interruptions

### Real-World Example
Converting a Python networking tool to Go:
1. Agent analyzed existing Python code ✅
2. Created conversion action plan in `action_plan.md` ✅  
3. Executed phase by phase with git commits ✅
4. Referenced plan file throughout development ✅
5. Successfully completed conversion with minimal confusion ✅

---

*This methodology turns AI agents into reliable development partners by giving them persistent memory and structured workflows.*

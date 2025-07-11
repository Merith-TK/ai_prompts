# Templates Directory

This directory contains reusable prompt templates that implement proven AI agent interaction methodologies.

## Available Templates

### Core Templates
- **[basic_prompt_template.md](./basic_prompt_template.md)** - Simple requests with clear requirements
- **[agent_task_template.md](./agent_task_template.md)** - Complex development tasks with file-based methodology
- **[code_analysis_template.md](./code_analysis_template.md)** - Understanding existing codebases before modification
- **[context_refresh_template.md](./context_refresh_template.md)** - Maintaining context in long conversations

## Template Usage Philosophy

### Question-Driven Approach
All templates include "Questions Welcome" sections that:
- Encourage agent clarification before starting work
- Signal that comprehensive answers are expected
- Prevent wasted time on wrong assumptions

### File-Based Context Management
Complex templates emphasize:
- Creating `action_plan.md` for persistent reference
- Using `notes.md` and `progress_log.md` for context
- Referencing files to prevent token rot

### Iterative Development
Templates support:
- Phase-by-phase execution with git snapshots
- Clear success criteria for each step
- Natural break points for conversation management

## Choosing the Right Template

### Use **Basic Prompt Template** when:
- Requirements are straightforward and well-defined
- Single-session completion expected
- Minimal back-and-forth needed

### Use **Agent Task Template** when:
- Complex feature development required
- Multiple implementation phases needed
- Integration with existing codebase
- Team collaboration involved

### Use **Code Analysis Template** when:
- Working with unfamiliar existing code
- Planning modifications to legacy systems
- Need to understand architecture before changes
- Reverse-engineering functionality

### Use **Context Refresh Template** when:
- Conversation getting long (20+ exchanges)
- Starting new session on existing project
- Agent seems confused about requirements
- Need to realign on project goals

## Customization Guidelines

### Adapt Templates For:
- **Your domain**: Add domain-specific sections (e.g., security for fintech, performance for gaming)
- **Your workflow**: Modify git/testing sections to match your processes
- **Your team**: Include team-specific conventions and standards
- **Your tools**: Reference your specific tech stack and tooling

### Keep Core Elements:
- Question encouragement sections
- Context provision requirements
- File-based memory references
- Clear success criteria

## Template Evolution

These templates have been refined through real-world usage. Continue to:
- **Track what works** - Note which sections lead to better agent responses
- **Identify gaps** - Add sections for common confusion points
- **Simplify language** - Make instructions clearer for both humans and AI
- **Share improvements** - Update templates based on successful patterns

---

*Effective AI agent collaboration starts with good communication structure. These templates provide that foundation.*

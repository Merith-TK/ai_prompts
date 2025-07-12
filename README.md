# AI Prompts Repository

A collection of carefully crafted prompts for AI agents, organized by category and use case.

## Repository Structure

```
ai_prompts/
├── agent/                          # AI agent interaction methodologies
│   ├── how_to_effectively_use_agents.md
│   └── how_to_avoid_token_rot.md
├── creative/                       # Creative writing and content generation
├── analysis/                       # Data analysis and research prompts
├── coding/                         # Programming and development prompts
├── templates/                      # Reusable prompt templates
├── examples/                       # Real-world implementation examples
├── action_plan.md                  # Development roadmap and current phase
├── notes.md                        # Key decisions and methodology insights
└── progress_log.md                 # Development timeline and session notes
```

## Core Methodology

This repository implements **file-based context management** to prevent token rot and enable effective long-term AI agent collaboration:

### Key Files for Context
- **action_plan.md** - Project overview, phases, and current objectives
- **notes.md** - Design decisions, principles, and insights
- **progress_log.md** - Development timeline and session tracking

### Question-Driven Approach
- All templates encourage AI agents to ask clarifying questions
- Comprehensive answers include context, examples, logic, and constraints
- "Questions Welcome" explicitly stated in interaction patterns

## Best Practices

- **Be Specific**: Include clear context and expected outcomes
- **Use Examples**: Provide sample inputs and outputs when possible
- **Version Control**: Track changes and improvements to prompts
- **Test Thoroughly**: Validate prompts across different scenarios
- **Document Results**: Note what works well and what doesn't

## Getting Started

### For New Users
1. **Read the methodology**: Start with `agent/how_to_effectively_use_agents.md`
2. **Understand context management**: Review `agent/how_to_avoid_token_rot.md`  
3. **Choose templates**: Browse `templates/` for your use case
4. **See examples**: Check `examples/` for real-world implementations

### For Continuing Work
1. **Read context files**: `action_plan.md`, `notes.md`, `progress_log.md`
2. **Understand current state**: Check progress log for recent developments
3. **Reference methodology**: Apply question-driven, file-based approach

### For AI Agents
When working on this repository:
```markdown
Please read the following context files to understand this project:
- action_plan.md (current objectives and development phases)
- notes.md (key decisions and design principles)  
- progress_log.md (recent progress and next priorities)

Then proceed with [specific task].
```

## Contributing

When adding new prompts:
1. Place them in the appropriate category folder
2. Use descriptive filenames
3. Include context and usage instructions
4. Document any dependencies or requirements

---

*For detailed guidance on working with AI agents, see the files in the `agent/` directory.*

# AI Prompts Repository - Project Notes

## Key Decisions Made

### Repository Philosophy
- **Question-First Approach**: Every template encourages agents to ask clarifying questions
- **File-Based Memory**: Use persistent files (action_plan.md, notes.md, progress_log.md) to prevent token rot
- **Dual Audience Design**: Content must work for both humans learning the methodology and AI agents applying it
- **Real-World Validation**: Examples based on actual successful agent collaborations, not theoretical scenarios

### Template Design Principles
- **Comprehensive Context Sections**: Templates require users to provide project context, tech stack, current state
- **Success Criteria**: Every template includes clear measures of completion
- **Question Encouragement**: Explicit "Questions Welcome" sections in all templates
- **Progressive Complexity**: From basic prompts to complex multi-phase development workflows

### Content Organization Strategy
- **agent/**: Core methodology guides - the "how to think about" agent interactions
- **templates/**: Reusable structures - the "how to format" requests
- **examples/**: Real implementations - the "what it looks like in practice"
- **coding/**: Domain-specific patterns for development work
- **creative/ & analysis/**: Future expansion for other use cases

### Communication Patterns Identified
1. **Initial Request Pattern**: Context + Objective + Requirements + Questions Welcome + Expected Output
2. **Clarification Response Pattern**: Context + Examples + Logic + Constraints (comprehensive answers)
3. **Context Refresh Pattern**: File references + Current state + Specific next request
4. **Error Correction Pattern**: "I think there was a mix up..." + Clarification + Redirect

### Technical Implementation Notes
- **Markdown Format**: Universal compatibility, easy to read for both humans and AI
- **Clear Section Headers**: Help AI agents parse and reference specific information
- **Code Block Examples**: Show exact prompt formats agents can recognize and follow
- **Cross-References**: Link related documents to build comprehensive understanding

## User Interaction Insights

### What Works Well
- Explicitly welcoming questions leads to better requirement gathering
- Comprehensive answers (with context/examples/logic) prevent repeated clarifications
- File-based action plans keep long projects on track
- Git snapshots between phases enable safe experimentation
- "Stop and clarify" when agents get confused prevents wasted work

### Common Agent Behaviors
- Most agents benefit from structured prompt formats
- Agents will reference external files when explicitly told they exist
- Question-asking needs to be explicitly encouraged in most models
- Context refresh from files works better than conversation summaries
- Agents can follow established patterns when given clear examples

### Methodology Evolution
- Started with conversation management techniques (token limits, context compression)
- Evolved to file-based external memory approach (much more effective)
- Refined to question-driven collaborative approach (prevents assumptions)
- Now includes both human learning guides and AI-parseable patterns

## Integration Considerations

### For Different Development Environments
- **VS Code**: Templates work well with file explorer and git integration
- **Command Line**: Action plans and progress logs complement terminal workflows
- **Team Environments**: Shared files enable collaborative agent interactions
- **CI/CD**: Templates support automated testing and deployment patterns

### For Different AI Models
- **GitHub Copilot**: Excellent with file references and structured prompts
- **ChatGPT**: Needs more explicit question encouragement (tends to be "yes man")
- **Claude**: Good balance of question-asking and comprehensive responses
- **Local Models**: Benefit from very structured, clear prompt formats

---

*These notes capture the thinking behind design decisions and should be referenced when extending or modifying the repository.*

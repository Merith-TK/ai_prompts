# Basic Prompt Template

Use this template for straightforward requests where you have clear requirements.

> **💡 Formatting Flexibility**: You don't need to follow this exact structured format! The important thing is to include all the relevant information and separate different concepts clearly. You can write conversationally and explain things naturally - just make sure to cover the context, objectives, requirements, and examples. The agent's questions are designed to clarify details and prevent misunderstandings, so be thorough in your explanations.

## Template

```markdown
## Context
[Provide relevant background: project type, tech stack, current state]

## Objective  
[Clear statement of what you want to achieve]

## Requirements
[Specific constraints, performance needs, security considerations]

## Questions Welcome
Please ask any clarifying questions before starting - I'd rather answer questions upfront than fix misunderstandings later.

## Expected Output
[Format, documentation level, testing needs]

## Example (if applicable)
[Sample input/output, expected behavior, or similar implementations]
```

## Usage Example

```markdown
## Context
Building a React e-commerce application with TypeScript. Currently have user authentication working and need to add shopping cart functionality.

## Objective
Create a shopping cart component that manages item quantities and calculates totals.

## Requirements
- Add/remove items with quantity controls
- Real-time total calculation
- Persist cart data in localStorage
- Mobile-responsive design
- TypeScript interfaces for type safety

## Questions Welcome
Please ask any clarifying questions before starting - I'd rather answer questions upfront than fix misunderstandings later.

## Expected Output
Complete React component with TypeScript interfaces, basic styling, and localStorage integration.

## Example
User adds product → quantity increases → total updates → data persists on page refresh
```

---

**Usage**: Copy this template and fill in each section. The "Questions Welcome" section encourages agent clarification, leading to better results.

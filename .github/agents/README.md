# Custom Agents

## What Are Agent Files?

Agent files define custom AI assistants with specialized roles, behaviors, and capabilities in GitHub Copilot. Each agent acts as a distinct persona optimized for specific tasks like research, code review, or documentation.

## Format

Agent files use Markdown with YAML frontmatter:

```markdown
---
name: agent-name
description: Brief description shown when selecting the agent
model: [optional] Specific model to use
---

Your agent instructions and behavior guidelines here.
```

### Required Fields
- `name`: Unique identifier for the agent
- `description`: Short explanation of the agent's purpose

### Optional Fields
- `model`: Specify a particular AI model
- Other custom metadata as needed

## Use

GitHub Copilot loads agent files and makes them available for invocation. Users can:
- Select a custom agent when starting a conversation
- Switch agents mid-conversation for specialized tasks
- Chain agents together for complex workflows

Agents are ideal for:
- Research and comparison tasks
- Specialized code reviews
- Domain-specific expertise (e.g., security, performance)
- Standardized reporting formats

## File Pattern

`<name>.agent.md`

## Sample

**File: `api-designer.agent.md`**

```markdown
---
name: api-designer
description: Designs RESTful APIs following best practices
---

You are an API design specialist.

## Guidelines
- Follow RESTful principles
- Use consistent naming conventions (plural nouns for collections)
- Design proper status codes and error responses
- Consider versioning strategy from the start
- Document endpoints with OpenAPI/Swagger format

## Output Format
1. API Endpoint Specification
2. Request/Response Examples
3. Error Handling Strategy
4. Security Considerations
```

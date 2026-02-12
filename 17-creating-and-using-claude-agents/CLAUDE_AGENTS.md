# Creating and Using Claude Code Agents

What agents are, how to use the built-in ones, and how to create your own custom agents.

## What Are Agents?

Agents (also called subagents) are specialized AI assistants inside Claude Code. Each agent has:

- A specific job (e.g. "review code", "run tests", "explore the codebase")
- Its own separate context window (so it doesn't clutter your main conversation)
- Access to specific tools (you control what it can and can't do)
- Optionally a different model (e.g. use a faster model for simple tasks)

When Claude encounters a task that matches an agent's description, it delegates the work to that agent. The agent works independently and returns the results.

## Why Use Agents?

- **Save context** — heavy exploration stays in the agent's window, not yours
- **Specialize** — an agent focused on testing is better than a generalist
- **Reuse** — create once, use across sessions and projects
- **Control costs** — route simple tasks to faster, cheaper models

## Built-in Agents

Claude Code comes with these agents out of the box:

| Agent | What it does | Model |
|-------|-------------|-------|
| **Explore** | Searches files, finds code, answers codebase questions | Haiku (fast) |
| **Plan** | Researches codebase and designs implementation plans | Inherits yours |
| **General-purpose** | Complex multi-step tasks, code modifications | Inherits yours |
| **Bash** | Runs terminal commands in a separate context | Inherits yours |

You don't need to configure these — Claude uses them automatically when appropriate.

## Managing Agents with /agents

Type `/agents` in Claude Code to:

- **View** all available agents (built-in and custom)
- **Create** new agents with a guided setup
- **Edit** existing agent configuration
- **Delete** custom agents

## Creating a Custom Agent

### Method 1: Interactive (easiest)

1. Type `/agents` in Claude Code
2. Select **Create new agent**
3. Choose the scope:
   - **Project-level** — saved in `.claude/agents/`, shared with your team via git
   - **User-level** — saved in `~/.claude/agents/`, available in all your projects
4. Select **Generate with Claude** and describe what the agent should do
5. Choose which tools it can access
6. Pick a model (sonnet, opus, haiku)
7. Save — it's available immediately

### Method 2: Markdown file (more control)

Create a `.md` file in `.claude/agents/` (project) or `~/.claude/agents/` (personal).

#### Example: Code Reviewer
```markdown
---
name: code-reviewer
description: Reviews code for quality and best practices. Use after making code changes.
tools: Read, Grep, Glob, Bash
model: sonnet
---

You are a senior code reviewer. When invoked:

1. Run git diff to see recent changes
2. Focus on the modified files
3. Check for:
   - Code clarity and readability
   - Exposed secrets or API keys
   - Proper error handling
   - Potential bugs

Provide feedback organized by priority:
- Critical (must fix)
- Warnings (should fix)
- Suggestions (nice to have)
```

#### Example: Test Runner
```markdown
---
name: test-runner
description: Runs tests and reports results. Use after writing or modifying code.
tools: Bash, Read, Grep, Glob
model: haiku
---

You are a test runner. When invoked:

1. Determine the test command from package.json
2. Run the tests
3. Report results clearly:
   - How many passed/failed
   - Details of any failures
   - Suggestions for fixing failures
```

#### Example: Debugger
```markdown
---
name: debugger
description: Investigates and fixes bugs, errors, and test failures.
tools: Read, Edit, Bash, Grep, Glob
---

You are an expert debugger. When invoked:

1. Capture the error message and stack trace
2. Find the source of the problem
3. Implement a minimal fix
4. Verify the fix works
```

## Configuration Reference

### File Format

The file has two parts: YAML frontmatter (between `---` lines) and the system prompt (everything after).

```markdown
---
name: my-agent
description: When to use this agent
tools: Read, Grep, Glob
model: sonnet
---

Instructions for the agent go here.
```

### Available Settings

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | Unique name (lowercase, hyphens only) |
| `description` | Yes | Tells Claude WHEN to use this agent |
| `tools` | No | Which tools the agent can use. If omitted, inherits all tools. |
| `model` | No | `sonnet`, `opus`, `haiku`, or `inherit` (default: inherit) |
| `maxTurns` | No | Maximum steps before the agent stops |

### Common Tool Combinations

| Agent type | Tools |
|-----------|-------|
| Read-only (reviewer, explorer) | `Read, Grep, Glob` |
| Research (with web access) | `Read, Grep, Glob, WebFetch, WebSearch` |
| Code writer | `Read, Write, Edit, Bash, Glob, Grep` |
| Terminal only | `Bash` |

## Where Agent Files Live

| Location | Who can use it | Shared via git? |
|----------|---------------|-----------------|
| `.claude/agents/` | Everyone on this project | Yes |
| `~/.claude/agents/` | Only you, across all projects | No |

For team collaboration, put agents in `.claude/agents/` and commit them to git. Everyone on the team gets the same agents.

## How Agents Work in Practice

### Claude delegates automatically
When you say "review my code", Claude sees that a `code-reviewer` agent exists and delegates the task. You don't have to manually invoke agents.

### Background agents
Press **Ctrl+B** while an agent is running to send it to the background. You can keep working while it finishes.

### Agents have isolated context
If an agent reads 50 files while exploring, that doesn't use up your main conversation's context. Only the final result comes back.

## Practical Examples for Collaboration

### Pre-commit reviewer
Create a `code-reviewer` agent that your whole team uses. Before every PR, say "review my changes" and the agent checks for issues.

### Documentation writer
```markdown
---
name: doc-writer
description: Generates documentation for code. Use when docs need updating.
tools: Read, Grep, Glob
model: sonnet
---

You are a documentation specialist. Read the code and generate clear, concise documentation. Focus on what the code does and how to use it, not implementation details.
```

### Project onboarding helper
```markdown
---
name: onboarding
description: Helps new team members understand the codebase. Use when someone asks how things work.
tools: Read, Grep, Glob
model: sonnet
---

You are an onboarding assistant for new developers. When asked about the codebase:

1. Find the relevant files
2. Explain the architecture in simple terms
3. Show the key patterns and conventions
4. Point to related files they should read next
```

## Tips

- **Start simple** — create one agent, test it, then add more
- **Good descriptions matter** — the description tells Claude when to use the agent, so be specific
- **Read-only agents are safest** — they can't accidentally modify your code
- **Use haiku for simple tasks** — it's faster and cheaper than opus/sonnet
- **Share with your team** — put agents in `.claude/agents/` and commit to git

# Getting Started with Claude Code

How to install, launch, and start using Claude Code for the first time.

## What is Claude Code?

Claude Code is a terminal-based AI assistant that can read, write, and modify code on your computer. You type instructions in plain English and it does the work — editing files, running commands, searching code, and more.

## Installation

### Prerequisites
- **Node.js** (version 18 or higher) — download from https://nodejs.org
- **Git** — download from https://git-scm.com

### Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Verify it installed:
```bash
claude --version
```

## Launching Claude Code

Open your terminal, navigate to your project, and type:

```bash
cd C:\code\my-project
claude
```

Claude Code reads files from whatever directory you launch it in. Always `cd` into your project first.

## Your First Session

Once Claude is running, just type what you want in plain English:

```
> explain what this project does
> add a contact form to the homepage
> fix the bug where the login button doesn't work
> create a new file called utils.js with a function to format dates
```

## Key Things to Know

### Claude can read your files
It has access to all files in your project directory. You don't need to paste code — just reference files by name.

### Claude can edit your files
When you ask it to make changes, it directly modifies the files on disk. You'll see exactly what it changed.

### Claude can run commands
It can run terminal commands like `npm install`, `git status`, `python script.py`, etc. It will ask for permission before running anything risky.

### Context window
Claude has a limited memory for each conversation. If the conversation gets long, use `/compact` to summarize it, or `/clear` to start fresh.

### CLAUDE.md
Run `/init` in any project to create a CLAUDE.md file. This teaches Claude about your project's structure, commands, and conventions so it works better each time.

## Basic Workflow

1. `cd` into your project
2. Run `claude`
3. Describe what you want in plain English
4. Review the changes Claude makes
5. Test the changes
6. Use `/clear` when starting a new task

## Tips for Beginners

- **Be specific** — "add a blue button below the title that says Subscribe" works better than "add a button"
- **Ask Claude to explain** — "what does this function do?" or "explain this error"
- **One thing at a time** — tackle tasks individually rather than asking for 10 things at once
- **Check the output** — always review what Claude changed before moving on
- **Use /compact** — when Claude seems to forget earlier context, compact the conversation

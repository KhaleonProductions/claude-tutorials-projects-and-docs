# Claude Code Slash Commands Reference

A complete list of every slash command available in Claude Code and what each one does.

## How to Use Slash Commands

Type `/` in the Claude Code terminal to see all available commands. Type more letters to filter the list (e.g. `/cl` shows `/clear`).

---

## Session & Context Management

| Command | What it does |
|---------|-------------|
| `/clear` | Clears conversation history and starts fresh. Does not affect your code or files. |
| `/compact [instructions]` | Summarizes your conversation to free up context window space. You can add instructions like `/compact focus on the auth changes`. |
| `/context` | Shows a visual grid of what's using up your context window (files, conversation, system prompts). |
| `/resume [session]` | Resume a previous conversation. Opens a session picker if no ID given. |
| `/rewind` | Go back to a previous point in the conversation and/or undo code changes. Also works with `Esc+Esc`. |
| `/rename <name>` | Rename the current session so it's easier to find later with `/resume`. |
| `/export [filename]` | Save the conversation to a file (e.g. `/export conversation.md`) or clipboard (`/export --clipboard`). |
| `/copy` | Copy Claude's last response to your clipboard. |
| `/teleport` | Resume a web session from claude.ai in your local terminal (subscribers only). |

## Configuration & Settings

| Command | What it does |
|---------|-------------|
| `/config` | Open the settings interface. |
| `/model` | Change the AI model (e.g. `/model sonnet`, `/model opus`). Takes effect immediately. |
| `/theme` | Change the terminal color theme. |
| `/permissions` | View or update which tools Claude is allowed to use. |
| `/vim` | Toggle Vim-style editing mode for your input. |
| `/statusline` | Configure Claude Code's status line display. |
| `/terminal-setup` | Install terminal keyboard shortcuts (e.g. Shift+Enter for newlines). |

## Project & Memory

| Command | What it does |
|---------|-------------|
| `/init` | Create a CLAUDE.md file for your project. This teaches Claude about your codebase. Run this first in any new project. |
| `/memory` | Open and edit CLAUDE.md memory files that persist instructions across sessions. |

## Information & Diagnostics

| Command | What it does |
|---------|-------------|
| `/help` | Show all available commands with descriptions. |
| `/cost` | Show how many tokens you've used this session. |
| `/usage` | Show your subscription plan limits and rate limit status. |
| `/stats` | Show daily usage history, session stats, and streaks. |
| `/status` | Show version, model, account, and connection info. |
| `/doctor` | Run health diagnostics on your Claude Code installation. |
| `/debug [description]` | Troubleshoot issues by reading the session debug log. |

## Task Management

| Command | What it does |
|---------|-------------|
| `/todos` | List TODO items tracked during the conversation. |
| `/tasks` | List and manage background tasks running asynchronously. |
| `/plan` | Toggle plan mode — a read-only mode where Claude researches and plans before writing code. |

## Integrations & Tools

| Command | What it does |
|---------|-------------|
| `/mcp` | Manage MCP (Model Context Protocol) server connections. |
| `/agents` | Create, edit, or list custom subagents. |
| `/hooks` | Configure lifecycle event handlers. |
| `/allowed-tools` | Interactively configure which tools Claude can use. |
| `/install-github-app` | Set up GitHub Actions so Claude can automatically review your PRs. |

## Session Control

| Command | What it does |
|---------|-------------|
| `/exit` | Exit Claude Code. |

---

## Shortcuts (Not Slash Commands)

These are typed directly, not as slash commands:

| Shortcut | What it does |
|----------|-------------|
| `! command` | Run a shell command directly (e.g. `! git status`). Output is added to conversation context. |
| `@filename` | Autocomplete a file path to reference in your prompt. |
| `Esc + Esc` | Same as `/rewind` — go back to a previous point. |

## Custom Slash Commands

You can create your own commands by placing Markdown files in:
- `.claude/commands/` — project-specific (shared with your team via git)
- `~/.claude/commands/` — global/personal (only on your machine)

These appear alongside built-in commands when you type `/`.

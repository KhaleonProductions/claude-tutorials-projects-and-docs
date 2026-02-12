# Understanding CLAUDE.md Configuration

What CLAUDE.md files are, why they matter, and how to use them.

## What is CLAUDE.md?

CLAUDE.md is a special Markdown file that teaches Claude about your project. Every time you start a Claude Code session, Claude reads this file first. Think of it as a briefing document — it tells Claude:

- How to build and run your project
- What the code structure looks like
- What rules and conventions to follow
- What tools and frameworks you're using

## Why Does It Matter?

Without CLAUDE.md, Claude starts every session knowing nothing about your specific project. It has to explore and figure things out, which takes time and context.

With CLAUDE.md, Claude immediately knows:
- "This is a Next.js app using pnpm"
- "Tests are run with `npm test`"
- "The database is Supabase on port 54352"

This means faster, more accurate help from the first prompt.

## How to Create One

### Automatic (recommended)
```
/init
```
Claude analyzes your project and generates CLAUDE.md automatically.

### Manual
Create a file called `CLAUDE.md` in your project root and write it yourself.

## What to Include

### Build and run commands
```markdown
## Commands
- `npm run dev` — start dev server on port 3000
- `npm run build` — production build
- `npm test` — run tests
- `npm run lint` — check code style
```

### Project structure
```markdown
## Architecture
- `src/pages/` — Next.js pages (file-based routing)
- `src/components/` — Reusable React components
- `src/lib/` — Utility functions and API clients
- `src/styles/` — CSS modules
```

### Conventions and rules
```markdown
## Conventions
- Use TypeScript strict mode
- Components use PascalCase filenames
- API routes go in `src/pages/api/`
- All database queries go through `src/lib/db.ts`
```

## What NOT to Include

- Obvious stuff ("use proper indentation")
- Information that's easily discoverable by reading code
- Every single file path — focus on the big picture
- Sensitive data (API keys, passwords)

## Where CLAUDE.md Files Live

| Location | Scope | Who sees it |
|----------|-------|-------------|
| `project/CLAUDE.md` | Project-wide | Everyone (committed to git) |
| `project/.claude/settings.local.json` | Project-wide settings | Just you (gitignored) |
| `~/.claude/CLAUDE.md` | Global across all projects | Just you |

## Editing CLAUDE.md

Use the `/memory` command to open and edit your CLAUDE.md files directly from Claude Code.

## Best Practice

Run `/init` when you first start working on any project. Update CLAUDE.md when:
- You add new build commands
- The project structure changes significantly
- You discover conventions the team follows
- Something keeps tripping Claude up

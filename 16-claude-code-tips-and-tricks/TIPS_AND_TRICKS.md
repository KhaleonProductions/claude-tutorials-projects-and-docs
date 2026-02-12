# Claude Code Tips and Tricks

Practical tips to get more out of Claude Code, especially when collaborating on projects.

## Prompting Tips

### Be specific
```
Bad:  "fix the bug"
Good: "fix the bug where clicking the submit button on the contact form shows a blank page instead of a success message"
```

### Give context
```
Bad:  "add authentication"
Good: "add email/password login using Supabase auth — the project already has Supabase set up in src/lib/supabase.ts"
```

### Break big tasks into steps
Instead of:
```
Build a complete e-commerce checkout flow with cart, shipping, payment, and confirmation
```

Do:
```
Step 1: "Add a shopping cart that stores items in localStorage"
Step 2: "Add a checkout page with a shipping address form"
Step 3: "Add Stripe payment integration"
Step 4: "Add an order confirmation page"
```

## Context Management

### When Claude seems to forget things
Your conversation uses a "context window" — Claude's short-term memory. When it fills up, earlier messages get compressed.

```
/compact          # summarize the conversation to free space
/compact focus on the auth changes    # keep specific topics
```

### Starting a new task
```
/clear            # fresh start, full context available
```

### Check your context usage
```
/context          # visual grid showing what's using context
```

## File Operations

### Reference files directly
Use `@` to autocomplete file paths:
```
look at @src/components/Header.tsx and fix the styling
```

### Read before changing
Always ask Claude to read a file before editing it:
```
read src/utils.js and then add a function to format phone numbers
```

### Multiple files at once
```
read all the files in src/components/ and explain how the navigation works
```

## Git Operations with Claude

### Quick commit
```
commit my changes with a good message
```

### Create a PR
```
create a PR for my changes
```

### Check what changed
```
show me what I've changed since my last commit
```

### Review before pushing
```
review my changes before I push
```

## Debugging with Claude

### Error messages
Just paste the error:
```
I'm getting this error: TypeError: Cannot read property 'map' of undefined
```

### Something doesn't work
```
the login button doesn't do anything when I click it — can you figure out why?
```

### Understanding code you didn't write
```
explain what the function processPayment in src/billing.js does
```

## Collaboration Shortcuts

### Start of a work session
```
pull the latest changes from master, then create a branch called feature/my-task
```

### End of a work session
```
commit my changes, push my branch, and create a PR
```

### Catch up on teammate's work
```
show me what changed in the last 5 commits on master
```

## Plan Mode

For complex tasks, use plan mode so Claude researches before writing code:

```
/plan
```

Claude will explore the codebase, design an approach, and show you the plan before making any changes. Approve it, then Claude implements it.

## Custom Commands

Create reusable commands for your team. Add a Markdown file to `.claude/commands/`:

For example, `.claude/commands/deploy.md`:
```markdown
Run the build, then deploy to production using the deploy script.
```

Now everyone on the team can type `/deploy` and Claude follows those instructions.

## Cost Awareness

### Check your usage
```
/cost             # tokens used this session
/usage            # subscription limits
```

### Save tokens
- Use `/compact` regularly on long sessions
- Use `/clear` between unrelated tasks
- Be specific — vague prompts lead to more back-and-forth

## The Most Useful Patterns

1. **"Explain this code"** — learn what unfamiliar code does
2. **"Fix this error: [paste error]"** — fastest debugging method
3. **"Create a PR for my changes"** — handles git workflow for you
4. **"/init"** — always run this in new projects
5. **"/compact"** — when Claude starts giving confused answers
6. **"Review my changes"** — catch mistakes before your teammates see them

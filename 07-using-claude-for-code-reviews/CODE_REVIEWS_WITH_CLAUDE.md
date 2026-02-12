# Using Claude for Code Reviews

How to use Claude Code to review pull requests and understand code changes.

## Why Review Code?

Code reviews catch bugs, improve quality, and help the team learn from each other. When you're new, Claude can help you understand what changed and whether it looks right.

## Reviewing a PR with Claude

### Method 1: Ask Claude directly

```
review PR #3 on our repo
```

Claude will:
- Fetch the PR details from GitHub
- Show you what files changed
- Summarize the changes
- Point out potential issues

### Method 2: Review the diff yourself with Claude's help

```bash
# See what changed between your branch and master
git diff master..my-feature
```

Then ask Claude:
```
explain the changes in the git diff above
```

### Method 3: Review specific files

```
read the file src/auth/login.js and tell me if there are any bugs
```

## What to Look For in a Code Review

Even with limited coding experience, you can check:

### Does it work?
- Ask Claude: "will this code work as intended?"
- Look for obvious errors (typos, missing closing brackets)

### Is it clear?
- Can you understand what the code does by reading it?
- Are variables named descriptively?

### Does it match the project style?
- Does it follow the same patterns as the rest of the codebase?

### Are there edge cases?
- Ask Claude: "what could go wrong with this code?"
- What happens with empty input? Very large input? Special characters?

## Leaving Review Comments

On GitHub, you can comment on specific lines:

1. Go to the PR > Files changed tab
2. Hover over a line number and click the `+` icon
3. Write your comment
4. Click "Add single comment" or "Start a review"

Common comment types:
- **Question**: "What does this variable represent?"
- **Suggestion**: "Could we rename this to be clearer?"
- **Issue**: "This might crash if the list is empty"
- **Praise**: "Nice approach here, this is clean"

## Approving or Requesting Changes

After reviewing:
- Click **Review changes** (green button, top right of Files changed)
- Choose **Approve**, **Request changes**, or **Comment**
- Add a summary of your review

## Using Claude to Create Better PRs

Before submitting your own PR, ask Claude to review your changes:

```
review my changes before I create a PR
```

Claude will look at your uncommitted or staged changes and flag issues before your teammates even see the code.

# GitHub Issues and Task Tracking

How to use GitHub Issues to organize work, track bugs, and plan features.

## What Are GitHub Issues?

Issues are GitHub's built-in task tracker. Each issue is a task, bug report, or feature request that lives in your repository. They help your team:

- Track what needs to be done
- Discuss solutions before writing code
- Know who's working on what
- Keep a history of decisions

## Creating an Issue

### On GitHub
1. Go to your repo > **Issues** tab > **New issue**
2. Write a clear title and description
3. Click **Submit new issue**

### With Claude
```
create a GitHub issue titled "Add dark mode support" with a description of what needs to be done
```

### With the GitHub CLI
```bash
gh issue create --title "Add dark mode support" --body "Add a toggle button that switches between light and dark themes"
```

## Writing Good Issues

### Bug report
```markdown
Title: Login button doesn't respond on mobile

## What happened
Tapping the login button on mobile does nothing.

## Expected behavior
Should open the login form.

## Steps to reproduce
1. Open the site on a phone
2. Tap the "Login" button in the header

## Device info
iPhone 14, Safari browser
```

### Feature request
```markdown
Title: Add PDF export for resumes

## Description
Users should be able to export their resume as a PDF file.

## Requirements
- Button on the resume preview page
- PDF should match the on-screen layout
- Include all sections (education, experience, skills)
```

## Labels

Labels help categorize issues. Common labels:

| Label | Meaning |
|-------|---------|
| `bug` | Something is broken |
| `feature` | New functionality |
| `enhancement` | Improvement to existing feature |
| `documentation` | Docs need updating |
| `good first issue` | Simple task for newcomers |
| `priority: high` | Needs attention soon |

Add labels when creating or editing an issue.

## Assigning Issues

- Assign an issue to yourself or a teammate to show who's working on it
- On the issue page, click **Assignees** on the right sidebar

## Linking Issues to PRs

When your PR fixes an issue, reference it in the PR description:

```markdown
Fixes #12
```

When the PR is merged, issue #12 automatically closes.

## Workflow with Issues

1. **Create an issue** for the task or bug
2. **Assign it** to yourself
3. **Create a branch** named after the issue: `git checkout -b fix/issue-12-login-bug`
4. **Do the work** and commit
5. **Create a PR** that references the issue: "Fixes #12"
6. **Merge the PR** — the issue closes automatically

## Viewing Issues

### On GitHub
Go to the Issues tab in your repo. Filter by label, assignee, or search.

### With CLI
```bash
gh issue list                     # list all open issues
gh issue view 12                  # view issue #12
gh issue list --assignee @me      # issues assigned to you
```

## Tips

- Create an issue BEFORE you start working — it helps you think through the task
- Keep issues focused — one task per issue
- Close issues you won't do with a comment explaining why
- Use issues for discussion — comment with questions, ideas, or updates

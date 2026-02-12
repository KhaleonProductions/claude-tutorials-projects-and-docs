# Working with Multiple Branches

How to manage feature branches, keep them updated, and handle complex branching scenarios.

## Why Multiple Branches?

In a real project, you might have several branches going at once:

```
master              ●───●───●───●───●
                    │       │       │
feature/login       ●───●───●       │     (merged)
                            │       │
feature/dark-mode           ●───●   │     (in progress)
                                    │
fix/header-crash                    ●──●  (in progress)
```

This is normal. Each feature or fix gets its own branch.

## Managing Your Branches

### See all branches
```bash
git branch              # local branches
git branch -r           # remote branches (on GitHub)
git branch -a           # all branches
```

### See which branch you're on
```bash
git branch
```
The `*` marks your current branch.

### Switch between branches
```bash
git checkout feature/dark-mode
```

Important: commit or stash your changes before switching. Uncommitted changes follow you to the other branch, which can cause confusion.

## Keeping Your Branch Up to Date

When your teammates merge PRs into master, your branch falls behind. Update it:

### Method 1: Merge master into your branch
```bash
git checkout master
git pull                            # get latest master
git checkout my-feature
git merge master                    # bring master's changes into your branch
```

### Method 2: Rebase (cleaner history)
```bash
git checkout my-feature
git pull origin master --rebase     # replay your changes on top of latest master
```

Rebasing creates a cleaner history but can be confusing for beginners. Start with merge — it's safer.

## Working on Multiple Features at Once

### Scenario: You're working on dark mode, but need to fix an urgent bug

```bash
# Save your dark mode work
git add .
git commit -m "WIP: dark mode progress"

# Switch to master and create a fix branch
git checkout master
git pull
git checkout -b fix/urgent-bug

# Fix the bug
git add .
git commit -m "Fix crash on login page"
git push -u origin fix/urgent-bug

# Go back to your feature
git checkout feature/dark-mode
```

### Using git stash (alternative)

If you don't want to commit unfinished work:

```bash
git stash                           # save changes temporarily
git checkout master                 # switch branches
# ... do other work ...
git checkout feature/dark-mode      # come back
git stash pop                       # restore your saved changes
```

## Branch Cleanup

After a PR is merged, delete the branch:

```bash
# Delete local branch
git branch -d feature/dark-mode

# Delete remote branch
git push origin --delete feature/dark-mode
```

### See which branches are already merged
```bash
git branch --merged master
```
These are safe to delete.

## Branch Naming Tips

Be consistent with your team:

```
feature/add-login-page
feature/user-settings
fix/broken-nav-links
fix/signup-validation
docs/update-readme
refactor/simplify-auth
```

Rules:
- Use lowercase
- Use hyphens between words
- Start with the type: `feature/`, `fix/`, `docs/`, `refactor/`
- Keep it short but descriptive

## Quick Reference

| What you want to do | Command |
|---------------------|---------|
| List branches | `git branch` |
| Create and switch | `git checkout -b name` |
| Switch to existing | `git checkout name` |
| Update from master | `git merge master` (while on your branch) |
| Stash changes | `git stash` / `git stash pop` |
| Delete local branch | `git branch -d name` |
| Delete remote branch | `git push origin --delete name` |
| See merged branches | `git branch --merged master` |

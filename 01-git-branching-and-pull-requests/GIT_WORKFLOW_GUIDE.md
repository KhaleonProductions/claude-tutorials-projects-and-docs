# Git Branching & Pull Request Workflow Guide

A step-by-step guide to working with branches and pull requests on GitHub.

## Why Use Branches?

The `master` branch is your stable, working code. You never want to break it. Branches let you work on new features safely — your changes stay separate until they're reviewed and approved.

```
master        ●───●───●───●           (stable, always works)
                       \       \
my-feature              ●───●───●     (your work, merged when ready)
```

## The Workflow

### Step 1: Make sure you're on master and up to date

Before starting any new work, always pull the latest changes.

```bash
git checkout master
git pull
```

- `git checkout master` — switches you to the master branch
- `git pull` — downloads the latest changes from GitHub that your teammates may have pushed

### Step 2: Create a new branch

```bash
git checkout -b your-branch-name
```

- `git checkout -b` — creates a new branch AND switches to it in one command
- Name your branch after what you're working on (e.g. `add-dark-mode`, `fix-login-bug`, `update-homepage`)

To check which branch you're on at any time:

```bash
git branch
```

The `*` marks your current branch.

### Step 3: Make your changes

Edit your code, add files, or ask Claude to make changes for you.

### Step 4: Check what changed

```bash
git status
```

This shows you:
- Which branch you're on
- Which files were modified, added, or deleted
- Whether changes are staged (ready to commit) or not

### Step 5: Stage your changes

```bash
git add .
```

- `git add .` — stages ALL changed files (the `.` means "everything")
- To stage specific files only: `git add index.html style.css`
- Staging means "mark these files to be included in the next commit"

### Step 6: Commit your changes

```bash
git commit -m "Add dark mode toggle button"
```

- A commit is a saved snapshot of your code at this moment
- `-m` lets you write the message inline
- Write a short, clear message describing WHAT you changed
- This saves to your LOCAL machine only — GitHub doesn't have it yet

You can combine Steps 5 and 6:

```bash
git add . && git commit -m "Your message here"
```

### Step 7: Push your branch to GitHub

```bash
git push -u origin your-branch-name
```

- `push` — uploads your branch to GitHub
- `-u origin` — sets up tracking so future pushes are simpler (only needed the first time)
- After the first push, you can just use `git push`

### Step 8: Create a Pull Request (PR)

A Pull Request is you saying: "I made these changes — please review them before they go into master."

You can create a PR by:
- Visiting the link GitHub gives you after pushing
- Going to your repo on GitHub and clicking "Compare & pull request"
- Asking Claude: "create a PR"

A PR shows:
- What files you changed
- The exact lines added and removed
- A place for teammates to comment, suggest changes, or approve

### Step 9: Merge the PR

Once the PR is reviewed and approved, merge it. This adds your changes into `master`.

You can merge by:
- Clicking the green "Merge" button on GitHub
- Asking Claude: "merge the PR"

### Step 10: Sync your local master

After merging, switch back to master and pull the merged changes:

```bash
git checkout master
git pull
```

Now your local code matches what's on GitHub, and you're ready to start a new branch for your next feature.

## Quick Reference

| Command | What it does |
|---------|-------------|
| `git checkout master` | Switch to master branch |
| `git pull` | Download latest changes from GitHub |
| `git checkout -b branch-name` | Create and switch to a new branch |
| `git status` | See what files changed |
| `git add .` | Stage all changes for commit |
| `git commit -m "message"` | Save a snapshot with a description |
| `git push -u origin branch-name` | Upload your branch to GitHub |
| `git checkout master && git pull` | Switch to master and sync |
| `git branch` | List all branches and see which one you're on |
| `git log --oneline` | See recent commit history |

## Common Situations

### "I made changes on the wrong branch"

If you haven't committed yet:
```bash
git stash
git checkout correct-branch
git stash pop
```

### "I need to see what my teammate changed"

```bash
git pull
git log --oneline
```

### "I want to delete a branch I'm done with"

```bash
git branch -d branch-name
```

### "I want to see the difference before committing"

```bash
git diff
```

## Tips

- One branch per feature or fix — keep them focused
- Pull from master before creating a new branch so you start with the latest code
- Write clear commit messages — your future self will thank you
- When in doubt, run `git status` to see where you are

# Essential Git Commands for Beginners

The 20 Git commands you'll actually use, explained in plain English.

## Setup (One-Time)

### Configure your identity
Git labels every commit with your name and email.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Check your config
```bash
git config --list
```

## Starting a Project

### Create a new Git project
```bash
git init
```
Run this inside a folder to start tracking it with Git. Creates a hidden `.git` folder.

### Download an existing project
```bash
git clone https://github.com/username/repo-name.git
```
Downloads the entire project and its history to your computer.

## Daily Workflow Commands

### See what's changed
```bash
git status
```
Shows which files are modified, staged, or untracked. Run this often — it's your compass.

### See the actual changes line by line
```bash
git diff
```
Shows exactly what lines were added or removed in your modified files.

### Stage files for commit
```bash
git add filename.txt        # stage one file
git add file1.txt file2.txt # stage specific files
git add .                   # stage everything
```
Staging = marking files to be included in your next commit.

### Save a snapshot (commit)
```bash
git commit -m "Describe what you changed"
```
Creates a permanent snapshot of your staged changes.

### Upload to GitHub
```bash
git push
```
Sends your commits to the remote repository (GitHub).

### Download latest from GitHub
```bash
git pull
```
Gets your teammates' changes. Do this before starting work each day.

## Branch Commands

### See all branches
```bash
git branch
```
The `*` marks which branch you're currently on.

### Create and switch to a new branch
```bash
git checkout -b my-feature
```
Creates a new branch AND switches to it.

### Switch to an existing branch
```bash
git checkout branch-name
```

### Push a new branch to GitHub
```bash
git push -u origin branch-name
```
The `-u` sets up tracking (only needed the first time for each branch).

### Delete a branch you're done with
```bash
git branch -d branch-name
```

## History & Information

### See commit history
```bash
git log --oneline
```
Shows a compact list of recent commits. Press `q` to exit.

### See who changed what in a file
```bash
git log --oneline filename.txt
```

## Fixing Mistakes

### Unstage a file (undo git add)
```bash
git restore --staged filename.txt
```

### Discard changes to a file (go back to last commit)
```bash
git restore filename.txt
```
Warning: this throws away your uncommitted changes to that file.

### Undo the last commit but keep the changes
```bash
git reset --soft HEAD~1
```

## Quick Reference Card

| What you want to do | Command |
|---------------------|---------|
| Start tracking a folder | `git init` |
| Download a project | `git clone <url>` |
| Check what changed | `git status` |
| See line-by-line changes | `git diff` |
| Stage files | `git add .` |
| Commit | `git commit -m "message"` |
| Push to GitHub | `git push` |
| Pull from GitHub | `git pull` |
| Create a branch | `git checkout -b name` |
| Switch branches | `git checkout name` |
| See history | `git log --oneline` |
| Undo staging | `git restore --staged file` |

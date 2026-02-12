# Common Git Mistakes and How to Fix Them

Every developer makes these mistakes. Here's how to recover.

## "I committed to the wrong branch"

You made changes on `master` instead of creating a branch first.

### Fix: Move the commit to a new branch
```bash
git checkout -b correct-branch    # creates new branch WITH your commits
git checkout master               # go back to master
git reset --soft HEAD~1           # undo the last commit on master (keeps files)
git restore .                     # discard the changes on master
```

## "I made changes but haven't committed — and I'm on the wrong branch"

### Fix: Stash and move
```bash
git stash                         # temporarily save your changes
git checkout correct-branch       # switch to the right branch
git stash pop                     # restore your changes here
```

## "I committed with a typo in the message"

### Fix: Amend the last commit message
```bash
git commit --amend -m "Corrected message here"
```

Only do this if you haven't pushed yet. If you already pushed, leave it — a typo in a message isn't worth the hassle.

## "I accidentally staged a file I don't want to commit"

### Fix: Unstage it
```bash
git restore --staged filename.txt
```

Your changes are still there, they're just no longer staged.

## "I want to undo my last commit completely"

### Keep the changes (just undo the commit):
```bash
git reset --soft HEAD~1
```

### Throw away the changes entirely:
```bash
git reset --hard HEAD~1
```

Warning: `--hard` permanently deletes those changes.

## "I deleted a file and I want it back"

### If you haven't committed the deletion:
```bash
git restore filename.txt
```

### If you committed the deletion:
```bash
git checkout HEAD~1 -- filename.txt
```

## "git pull says there are conflicts"

This means you and a teammate edited the same lines. See the "Resolving Merge Conflicts" guide for detailed steps. Quick version:

1. Open the conflicting files
2. Look for `<<<<<<<` markers
3. Choose which code to keep
4. Delete the markers
5. `git add .` and `git commit`

## "I pushed something I shouldn't have (like a password)"

### Fix: Remove it from history
```bash
git reset --soft HEAD~1           # undo the commit
# remove the sensitive file or content
git add .
git commit -m "Remove sensitive data"
git push --force                  # overwrite the remote history
```

Important: If the secret was pushed to a public repo, consider it compromised. Change the password/key immediately.

## "I'm totally lost and everything is broken"

### The nuclear option: start fresh from GitHub
```bash
cd ..
mv my-project my-project-backup   # keep your local changes just in case
git clone https://github.com/user/my-project.git
```

Then manually copy over any changes you want to keep from the backup.

### Or ask Claude
```
my git repo is in a weird state, can you help me figure out what's wrong?
```

Claude will run `git status`, `git log`, and other commands to diagnose the problem.

## Prevention Tips

- **Commit often** — small commits are easier to undo
- **Check `git status` before committing** — make sure you're on the right branch
- **Don't use `--force` unless you understand the consequences**
- **Use `.gitignore`** to prevent sensitive files from being tracked
- **When in doubt, ask Claude** before running a command you're unsure about

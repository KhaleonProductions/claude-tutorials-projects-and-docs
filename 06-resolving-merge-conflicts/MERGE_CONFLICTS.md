# Resolving Merge Conflicts

What merge conflicts are, why they happen, and how to fix them.

## What is a Merge Conflict?

A merge conflict happens when two people edit the **same lines** in the **same file** on different branches. Git doesn't know which version to keep, so it asks you to decide.

## When Do Conflicts Happen?

```
master    ●───●───●
              │
Alice edits line 5 of style.css: color: blue;
Bob edits line 5 of style.css:   color: red;
```

Alice merges first — no problem. When Bob tries to merge, Git finds both people changed line 5 and doesn't know which to use.

## What a Conflict Looks Like

When you run `git merge` or `git pull` and there's a conflict, Git marks the file like this:

```
h1 {
<<<<<<< HEAD
    color: blue;
=======
    color: red;
>>>>>>> bobs-branch
}
```

- Everything between `<<<<<<< HEAD` and `=======` is YOUR version
- Everything between `=======` and `>>>>>>> bobs-branch` is the OTHER version

## How to Fix a Conflict

### Step 1: See which files have conflicts
```bash
git status
```
Files with conflicts show as "both modified".

### Step 2: Open the file and choose what to keep

You have three options:

**Option A: Keep your version**
```css
h1 {
    color: blue;
}
```

**Option B: Keep their version**
```css
h1 {
    color: red;
}
```

**Option C: Combine both (most common)**
```css
h1 {
    color: purple;
}
```

Delete the `<<<<<<<`, `=======`, and `>>>>>>>` markers entirely. Only leave the code you want.

### Step 3: Mark as resolved and commit
```bash
git add style.css
git commit -m "Resolve merge conflict in style.css"
```

## Using Claude to Fix Conflicts

You can ask Claude to help:

```
I have a merge conflict in style.css — can you resolve it?
```

Claude will read the file, understand both versions, and fix it for you.

## How to Avoid Conflicts

1. **Pull often** — `git pull` before starting work each day
2. **Small branches** — merge frequently rather than working on a branch for weeks
3. **Communicate** — tell your team what files you're working on
4. **Different files** — when possible, divide work so people aren't editing the same files

## Practice Scenario

If you want to practice, try this:

1. Create two branches from master
2. Edit the same line in the same file on both branches
3. Merge one branch into master
4. Try merging the second — you'll get a conflict
5. Fix it using the steps above

Conflicts seem scary at first but they become routine. The key is: read both versions, decide what the code should look like, remove the markers, and commit.

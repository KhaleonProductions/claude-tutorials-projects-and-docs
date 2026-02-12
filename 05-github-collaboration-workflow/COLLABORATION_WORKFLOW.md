# GitHub Collaboration Workflow

How to work on a project with teammates using GitHub, from start to finish.

## The Golden Rules

1. **Never push directly to main/master** — always use branches and PRs
2. **Pull before you start working** — get your teammates' latest changes first
3. **Communicate** — use PR descriptions and comments to explain your work
4. **Small, focused PRs** — one feature or fix per PR, not everything at once

## Setting Up for Collaboration

### Getting added to a project
Your team lead or repo owner adds you as a collaborator:
- They go to the repo on GitHub > Settings > Collaborators > Add people
- You accept the invitation via email or GitHub notifications

### Clone the project
```bash
git clone https://github.com/team/project-name.git
cd project-name
```

## Your Daily Workflow

### Morning: Start your day
```bash
git checkout master       # switch to master
git pull                  # get latest changes from teammates
git checkout -b my-task   # create your branch for today's work
```

### During the day: Work on your feature
Make changes, then save your progress:
```bash
git add .
git commit -m "Add login form validation"
```

You can make multiple commits on a branch — think of each as a checkpoint.

### When you're done: Push and create a PR
```bash
git push -u origin my-task
```
Then create a Pull Request (ask Claude: "create a PR for my changes").

### After your PR is merged
```bash
git checkout master
git pull                  # get your merged changes + others' work
git branch -d my-task     # delete the old branch locally
```

## Reviewing Teammates' Pull Requests

When a teammate creates a PR, you review it:

1. Go to the PR on GitHub
2. Click the **Files changed** tab
3. Read through the changes
4. Leave comments on specific lines by clicking the `+` icon
5. Submit your review:
   - **Approve** — looks good, merge it
   - **Request changes** — something needs fixing
   - **Comment** — just leaving thoughts, no blocking decision

You can also ask Claude to help you review:
```
review PR #5 on our repo
```

## Branch Naming Conventions

Use consistent names so everyone knows what a branch is for:

| Pattern | Example | When to use |
|---------|---------|-------------|
| `feature/description` | `feature/dark-mode` | Adding something new |
| `fix/description` | `fix/login-crash` | Fixing a bug |
| `docs/description` | `docs/api-guide` | Documentation changes |
| `refactor/description` | `refactor/cleanup-utils` | Restructuring code |

## Handling Simultaneous Work

When two people work at the same time:

```
master            ●───●───●
                  │       │
alice/feature-a   ●───●   │         Alice's branch
                          │
bob/feature-b             ●───●     Bob's branch
```

Each person works on their own branch. When Alice merges first, Bob's branch doesn't have Alice's changes yet. Bob needs to:

```bash
git checkout master
git pull                          # get Alice's merged changes
git checkout feature-b
git merge master                  # bring Alice's changes into his branch
```

If they edited different files, Git merges automatically. If they edited the same lines, you get a merge conflict (see the Resolving Merge Conflicts guide).

## Communication Tips

- **Write clear PR titles** — "Add user login page" not "updates"
- **Describe what and why in PR descriptions** — help your reviewer understand the context
- **Use GitHub Issues** to track bugs and features before working on them
- **Tag people** in comments with `@username` when you need their input
- **Don't take PR feedback personally** — it's about improving the code, not criticizing you

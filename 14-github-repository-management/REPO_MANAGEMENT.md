# GitHub Repository Management

How to create, clone, configure, and manage repositories on GitHub.

## Creating a Repository

### On GitHub
1. Go to https://github.com > click **+** > **New repository**
2. Enter a name (use hyphens, not spaces: `my-project` not `my project`)
3. Choose Public or Private
4. Optionally add a README, .gitignore, and license
5. Click **Create repository**

### From the terminal (faster)
```bash
# Create a repo from an existing local project
cd C:\code\my-project
git init
git add .
git commit -m "Initial commit"
gh repo create my-project --public --source=. --push
```

```bash
# Create an empty repo on GitHub
gh repo create my-project --public
```

### With Claude
```
create a GitHub repo called my-project and push this code
```

## Cloning a Repository

Cloning downloads a repo from GitHub to your computer.

```bash
git clone https://github.com/username/repo-name.git
```

This creates a folder called `repo-name` in your current directory.

To clone into a specific location:
```bash
git clone https://github.com/username/repo-name.git C:\code\repo-name
```

## Repository Settings

### Add a collaborator
Repo on GitHub > **Settings** > **Collaborators** > **Add people**

### Change visibility (public/private)
Repo > **Settings** > **General** > scroll to **Danger Zone** > **Change visibility**

### Default branch
Repo > **Settings** > **General** > **Default branch** — usually `main` or `master`

### Branch protection (for teams)
Repo > **Settings** > **Branches** > **Add branch protection rule**

Recommended settings for your main branch:
- Require pull request before merging
- Require at least 1 approval
- This prevents anyone from pushing directly to main

## The .gitignore File

This file tells Git which files to NOT track. Create it in your project root.

### Example .gitignore
```
# Dependencies
node_modules/

# Environment variables (contains secrets)
.env
.env.local

# Build output
dist/
.next/

# OS files
.DS_Store
Thumbs.db

# Editor files
.vscode/settings.json
```

You can ask Claude:
```
create a .gitignore file for this project
```

## Forking a Repository

A fork is your own copy of someone else's repo. Used when you want to contribute to a project you don't own.

```bash
gh repo fork username/repo-name
```

This creates a copy under your account. You can make changes and submit a PR back to the original.

## Deleting a Repository

### On GitHub
Repo > **Settings** > scroll to **Danger Zone** > **Delete this repository**

### With CLI
```bash
gh repo delete username/repo-name --yes
```

Warning: This is permanent.

## Repository Organization Tips

- **One project per repo** — unless you have a monorepo with related services
- **Always include a README** — explain what the project is and how to run it
- **Use .gitignore from day one** — prevents accidentally committing secrets or junk files
- **Use descriptive repo names** — `resume-builder-pro` not `project1`
- **Add topics/tags** — helps you filter repos on your GitHub profile

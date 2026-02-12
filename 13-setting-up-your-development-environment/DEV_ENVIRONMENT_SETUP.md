# Setting Up Your Development Environment

Everything you need to install to start developing and using Claude Code on Windows.

## Essential Tools

### 1. Git
Version control — tracks changes to your code.

**Install**: Download from https://git-scm.com/download/windows

During installation:
- Choose "Git from the command line and also from 3rd-party software"
- Choose "Use Windows' default console window" (or your preferred terminal)
- Accept the other defaults

**Verify**:
```bash
git --version
```

**Configure** (one-time):
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### 2. Node.js
JavaScript runtime — required for Claude Code and most web projects.

**Install**: Download the LTS version from https://nodejs.org

This also installs `npm` (Node Package Manager).

**Verify**:
```bash
node --version
npm --version
```

### 3. Claude Code
AI coding assistant in your terminal.

**Install**:
```bash
npm install -g @anthropic-ai/claude-code
```

**Verify**:
```bash
claude --version
```

### 4. GitHub CLI (gh)
Lets you interact with GitHub from the terminal (create repos, PRs, issues).

**Install**: Download from https://cli.github.com

**Authenticate** (one-time):
```bash
gh auth login
```
Follow the prompts — choose GitHub.com, HTTPS, and authenticate via browser.

**Verify**:
```bash
gh auth status
```

### 5. Visual Studio Code (recommended editor)
**Install**: Download from https://code.visualstudio.com

Useful extensions to install:
- **GitLens** — see who changed each line and when
- **Prettier** — auto-format code
- **ESLint** — catch JavaScript errors

Open a project from terminal:
```bash
code C:\code\my-project
```

## Optional Tools

### pnpm (fast package manager)
Some projects use pnpm instead of npm.
```bash
npm install -g pnpm
```

### Windows Terminal
Better terminal experience than Command Prompt.
Install from the Microsoft Store — search "Windows Terminal".

## Folder Structure

Keep your projects organized:
```
C:\code\
├── project-a\
├── project-b\
└── tutorials\
```

Always work inside `C:\code\` or a similar dedicated folder. Don't scatter projects across your Desktop or Documents.

## Verifying Everything Works

Run this checklist:
```bash
git --version          # should show a version number
node --version         # should show v18 or higher
npm --version          # should show a version number
claude --version       # should show a version number
gh auth status         # should show "Logged in to github.com"
code --version         # should show a version number (if VS Code installed)
```

If any command shows "not recognized" or an error, that tool needs to be installed or added to your system PATH.

## What is PATH?

When you type a command like `git`, your computer looks through a list of folders to find the `git` program. This list is called PATH. If a tool is "not recognized", it usually means the installer didn't add it to PATH.

**Fix**: Re-run the installer and check the option to "Add to PATH", or search Windows for "Edit environment variables" and add the folder manually.

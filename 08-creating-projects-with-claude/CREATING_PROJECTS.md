# Creating Projects with Claude

How to use Claude Code to scaffold new projects from scratch.

## Starting a New Project

### Step 1: Create a folder
```bash
mkdir C:\code\my-new-project
cd C:\code\my-new-project
```

### Step 2: Launch Claude
```bash
claude
```

### Step 3: Describe what you want

Be specific about what you're building:

```
Create a personal portfolio website with:
- A homepage with my name, bio, and photo placeholder
- A projects section showing 3 project cards
- A contact form
- Use HTML, CSS, and vanilla JavaScript
- Make it responsive for mobile
```

Claude will create all the files for you.

### Step 4: Initialize Git and CLAUDE.md
```bash
git init
```
Then tell Claude:
```
run /init to create a CLAUDE.md for this project
```

### Step 5: Push to GitHub
```
create a GitHub repo called my-portfolio and push this project
```

## Project Types You Can Ask Claude to Create

### Static website
```
Create a landing page for a coffee shop with a menu, hours, and location map
```

### Node.js API
```
Create an Express.js REST API with endpoints for users and products, using a JSON file for storage
```

### React app
```
Create a React app with a todo list that saves to localStorage
```

### Full-stack app
```
Create a Next.js app with a notes feature, using Supabase for the database
```

## Tips for Better Results

### Be specific about tech stack
Bad: "Create a website"
Good: "Create a website using HTML, CSS, and JavaScript with a responsive layout"

### Describe features clearly
Bad: "Add user stuff"
Good: "Add a sign-up form with fields for name, email, and password"

### Build incrementally
Instead of asking for everything at once:
1. "Create the basic HTML structure with navigation"
2. "Add the homepage content and styling"
3. "Add the contact form with validation"
4. "Make it responsive for mobile screens"

### Review as you go
After each step, open the project in your browser or editor. Make sure it works before asking for the next feature.

## After Creating the Project

1. **Test it** — open it, click everything, try edge cases
2. **Create CLAUDE.md** — run `/init` so future sessions understand the project
3. **Push to GitHub** — protect your work with version control
4. **Create a branch** for your next feature — don't keep building on master

# Writing Good Commit Messages and PR Descriptions

Clear communication through Git makes collaboration smoother for everyone.

## Commit Messages

### The format
```
Short summary of what changed (50 characters or less)
```

For complex changes, add a blank line and more detail:
```
Add user login with email/password

- Created login form component with validation
- Added authentication API endpoint
- Store session token in localStorage
- Redirect to dashboard after successful login
```

### Good examples
```
Add dark mode toggle button
Fix crash when submitting empty contact form
Update homepage hero image and tagline
Remove unused CSS from navigation
```

### Bad examples
```
fixed stuff                    # too vague
updated code                   # what code? what update?
asdfasdf                       # not helpful
WIP                            # don't commit work-in-progress
Changes to multiple files      # every commit changes files
```

### Rules of thumb
- Start with a verb: Add, Fix, Update, Remove, Refactor
- Describe WHAT changed, not HOW (the diff shows the how)
- Keep the first line under 50 characters
- Don't end with a period
- Use present tense: "Add feature" not "Added feature"

## Pull Request Titles

Same rules as commit messages but can be slightly longer:

```
Add user authentication with email and password
Fix mobile navigation not closing after link click
Update pricing page with new plan tiers
```

## Pull Request Descriptions

A good PR description helps reviewers understand your changes quickly.

### Template
```markdown
## Summary
Brief description of what this PR does and why.

## Changes
- List the main changes you made
- One bullet per logical change
- Focus on what matters for review

## How to test
1. Step-by-step instructions
2. To verify the changes work
3. Include any setup needed

## Screenshots (if applicable)
Include before/after screenshots for visual changes.
```

### Example
```markdown
## Summary
Added a dark mode toggle that lets users switch between light and dark themes.

## Changes
- Added toggle button to the header
- Created dark mode CSS styles using a `.dark` class on body
- Button state persists across page reloads via localStorage

## How to test
1. Open the app in your browser
2. Click the moon icon in the top right
3. Verify background turns dark and text turns light
4. Refresh the page — dark mode should persist
5. Click again to switch back to light mode
```

## Asking Claude for Help

If you're not sure what to write:

```
create a PR for my changes with a good description
```

Claude will look at your changes and write the title and description for you.

## Why This Matters

- **For your teammates**: They need to understand your changes to review them
- **For future you**: 6 months from now you'll wonder "why did I change this?"
- **For debugging**: `git log` becomes useful when messages are descriptive
- **For the project**: Good history tells the story of how the codebase evolved

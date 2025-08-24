# Contributing to Documentation

Everyone can and should contribute to our documentation! Here's how.

## Why Contribute?

- **Share knowledge** - Help others learn
- **Save time** - Document it once, reference forever
- **Reduce confusion** - Clear docs = fewer questions
- **Onboard faster** - New folks get up to speed quickly
- **Build culture** - Docs reflect how we work

## Quick Start

### Fixing a Typo (2 minutes)

1. Click "Edit" on any page
2. Make your change
3. Submit PR with description
4. Merge after approval

### Adding New Content (10 minutes)

1. Create new `.md` file in appropriate folder
2. Write in Markdown
3. Update navigation in `mkdocs.yml`
4. Submit PR
5. Preview deploy and merge

## What to Document

### Always Document

- ✅ **Decisions** - Why we chose X over Y
- ✅ **Processes** - How we do things
- ✅ **Onboarding** - What new people need
- ✅ **Troubleshooting** - Common problems & solutions
- ✅ **Architecture** - How systems work
- ✅ **APIs** - How to integrate

### Don't Document

- ❌ **Sensitive data** - Passwords, keys, PII
- ❌ **Temporary info** - Use Slack instead
- ❌ **Personal opinions** - Keep it factual
- ❌ **External docs** - Link, don't copy
- ❌ **Work in progress** - Wait until stable

## How to Contribute

### Method 1: GitHub Web UI (Easy)

1. Navigate to file on GitHub
2. Click pencil icon to edit
3. Make changes in browser
4. Write commit message
5. Create pull request

### Method 2: Local Development

```bash
# Clone repo
git clone git@github.com:yourcompany/docs.git
cd docs

# Create branch
git checkout -b update-deployment-docs

# Make changes
code docs/engineering/deployment.md

# Preview locally
pip install mkdocs-material
mkdocs serve
# View at http://localhost:8000

# Commit and push
git add .
git commit -m "docs: update deployment guide"
git push origin update-deployment-docs

# Create PR on GitHub
```

## Writing Style Guide

### Principles

1. **Clear over clever** - Simple language
2. **Practical over theoretical** - Real examples
3. **Scannable** - Headers, bullets, tables
4. **Inclusive** - Welcoming to all
5. **Up-to-date** - Regular reviews

### Voice & Tone

- **Friendly** but professional
- **Direct** but not blunt
- **Helpful** but not condescending
- **Confident** but not arrogant

### Structure

```markdown
# Clear Title

Brief introduction paragraph explaining what and why.

## Main Section

### Subsection

Content with:
- Bullet points for lists
- **Bold** for emphasis
- `code` for technical terms

## Examples

Show real examples people can use.

## Next Steps

What should reader do next?
```

### Formatting Guidelines

#### Headers
```markdown
# H1 - Page title only
## H2 - Major sections
### H3 - Subsections
#### H4 - Rarely needed
```

#### Lists
```markdown
Unordered:
- Item one
- Item two
  - Nested item

Ordered:
1. First step
2. Second step
3. Third step
```

#### Code Blocks
````markdown
```javascript
// Use syntax highlighting
const example = "Always include language";
```
````

#### Tables
```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data | Data | Data |
```

#### Admonitions
```markdown
!!! note
    Important information

!!! warning
    Be careful about this

!!! tip
    Helpful suggestion
```

### Writing Tips

#### Do's ✅
- Use present tense
- Write short sentences
- Include examples
- Add visuals when helpful
- Link to related docs
- Test your instructions

#### Don'ts ❌
- Don't assume knowledge
- Don't use jargon without explaining
- Don't duplicate existing docs
- Don't write walls of text
- Don't forget to proofread

## Pull Request Process

### Before Submitting

- [ ] **Spell check** - No typos
- [ ] **Preview locally** - Looks good
- [ ] **Links work** - Test all links
- [ ] **Makes sense** - Would a new person understand?
- [ ] **Adds value** - Improves on what exists

### PR Template

```markdown
## What Changed
Brief description of changes

## Why
Problem this solves or value it adds

## Type of Change
- [ ] Fix typo
- [ ] Add new documentation
- [ ] Update existing docs
- [ ] Restructure/reorganize

## Checklist
- [ ] Previewed locally
- [ ] Links tested
- [ ] Spell checked
- [ ] Updated navigation if needed
```

### Review Process

1. **Auto-checks** run (links, spelling)
2. **Preview deployment** created
3. **Reviewer assigned** (usually automatic)
4. **Feedback addressed** if any
5. **Merged** to main
6. **Auto-deployed** to site

## Maintenance

### Regular Reviews

- **Monthly**: Check for outdated info
- **Quarterly**: Review structure
- **Yearly**: Major reorganization

### Outdated Content

Found something outdated?

1. **Quick fix**: Update it yourself
2. **Need help**: Create an issue
3. **Not sure**: Ask in #docs

### Broken Links

- Check weekly with automated tools
- Fix immediately when found
- Update or remove dead links

## Documentation Standards

### File Naming
```
use-kebab-case.md
not fileName_2.md
```

### Front Matter (Optional)
```yaml
---
title: Page Title
description: Brief description
tags: [tag1, tag2]
---
```

### Images
```markdown
![Alt text](../images/filename.png)
```
- Use descriptive alt text
- Optimize image size
- Prefer SVG for diagrams

## Common Patterns

### How-To Guide
```markdown
# How to [Task]

## Prerequisites
What you need before starting

## Steps
1. First step
2. Second step
3. Third step

## Verification
How to know it worked

## Troubleshooting
Common issues and fixes
```

### Reference Doc
```markdown
# [Feature] Reference

## Overview
What this is

## Configuration
Available options

## Examples
Common use cases

## API
Detailed specifications
```

### Explanation
```markdown
# Understanding [Concept]

## What is it?
Definition and purpose

## Why use it?
Benefits and use cases

## How it works
Technical explanation

## Best practices
Recommended approaches
```

## Getting Help

### Questions?
- **Content**: Ask in #docs
- **Technical**: Ask in #engineering
- **Process**: Ask in #operations

### Learning Resources
- [Markdown Guide](https://www.markdownguide.org/)
- [MkDocs Documentation](https://www.mkdocs.org/)
- [Technical Writing Course](https://developers.google.com/tech-writing)

## Recognition

We appreciate documentation contributions! 

- Monthly shoutouts for contributors
- Documentation champion award
- It counts in performance reviews

## Quick Wins

Want to contribute but not sure where? Try these:

1. **Fix a typo** you noticed
2. **Add an example** to existing docs
3. **Update screenshots** that are outdated
4. **Improve unclear** explanations
5. **Document something** you just learned

## Remember

> "The best documentation is the one that exists."

Perfect is the enemy of good. Your contribution doesn't have to be perfect - others can help improve it. The important thing is to share knowledge!

Start small, contribute often, and help us build amazing documentation together! 📝
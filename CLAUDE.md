# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 🚨 CRITICAL BRANCH MANAGEMENT RULE

**NEVER work directly on the `main` branch. This is absolutely forbidden.**

### Mandatory Git Workflow:
- **ALWAYS work on the `draft` branch** - No exceptions
- **NEVER checkout, pull, or switch to `main` branch** - The main branch is off-limits
- **NEVER push directly to main** - All changes must go through draft branch
- **DO NOT merge to main yourself** - Only authorized personnel handle main branch merges
- **NEVER CREATE NEW BRANCHES AUTOMATICALLY** - Branch creation is strictly forbidden. Only use existing branches
- **DO NOT use `git checkout -b` or `git branch`** - Creating branches is not allowed under any circumstances

### Correct workflow:
```bash
# ALWAYS ensure you're on draft branch before any work
git checkout draft  # ONLY checkout existing branches, NEVER create new ones

# Make your changes on draft branch only
git add .
git commit -m "your message"
git push origin draft
```

### FORBIDDEN Commands - NEVER USE:
```bash
# ❌ NEVER create new branches
git checkout -b new-branch  # FORBIDDEN
git branch new-branch       # FORBIDDEN
git switch -c new-branch    # FORBIDDEN

# ❌ NEVER switch to main
git checkout main           # FORBIDDEN
git pull origin main        # FORBIDDEN
```

If accidentally on main branch, immediately switch to draft without making any changes:
```bash
git checkout draft  # Switch to existing draft branch only
```

## Repository Overview

This is a docs-as-code repository using MkDocs with Material theme to create a company documentation hub. The documentation is automatically deployed to GitHub Pages at https://ravikandas.github.io/company-docs/

## Essential Commands

### Local Development
```bash
# Install dependencies
pip install mkdocs-material pymdown-extensions

# Run local development server
mkdocs serve  # Accessible at http://localhost:8000

# Build static site
mkdocs build  # Creates site/ directory
```

### Deployment
```bash
# WARNING: Never deploy manually from your local machine
# Deployment happens automatically when draft branch is merged to main by authorized personnel

# The site auto-deploys when changes are merged to main branch via GitHub Actions
# You should NEVER trigger deployment yourself
```

## Architecture

### Documentation Structure
- **docs/** - All Markdown documentation files
  - **handbook/** - Company policies, values, onboarding
  - **engineering/** - Technical docs, setup guides, standards
  - **processes/** - How we work, meetings, decisions, contributing
- **mkdocs.yml** - MkDocs configuration and navigation structure
- **.github/workflows/deploy.yml** - Automated deployment to GitHub Pages

### Key Configuration Points

1. **Site URL**: Currently set to `https://yourdomain.github.io/docs` in mkdocs.yml - update to match actual deployment
2. **GitHub username**: Replace `yourusername` references with `RaviKandas` in mkdocs.yml and README.md
3. **Navigation**: Defined in mkdocs.yml under the `nav:` section
4. **Theme features**: Material theme with dark/light mode toggle, search, and code copy buttons

### Deployment Flow (Handled by authorized personnel only)
1. Changes are pushed to `draft` branch by contributors
2. Authorized personnel review and merge draft to `main` branch
3. GitHub Actions workflow triggers automatically on main
4. Builds MkDocs site and deploys to `gh-pages` branch
5. GitHub Pages serves from `gh-pages` branch

**Remember: You work on draft branch only. Never interact with main branch.**

## Adding Documentation

### To add a new page:
1. **Ensure you're on draft branch**: `git checkout draft`
2. Create `.md` file in appropriate directory under `docs/`
3. Add entry to `nav:` section in `mkdocs.yml`
4. Commit and push to draft branch: `git push origin draft`
5. Create pull request for review (NEVER merge to main yourself)

### To modify existing content:
1. **Ensure you're on draft branch**: `git checkout draft`
2. Edit the `.md` file directly
3. No need to update mkdocs.yml unless changing navigation
4. Commit and push to draft branch: `git push origin draft`
5. Changes deploy automatically after authorized merge to main

## Important Files to Update

When setting up for a specific company:
1. Update `site_url` in mkdocs.yml
2. Update GitHub links in mkdocs.yml (`extra.social`)
3. Update repository URL in README.md
4. Replace placeholder content in docs with actual company information
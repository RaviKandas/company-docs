# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

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
# Manual deployment to GitHub Pages (automated via GitHub Actions)
mkdocs gh-deploy --force --clean

# The site auto-deploys on push to main branch via GitHub Actions
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

### Deployment Flow
1. Push changes to `main` branch
2. GitHub Actions workflow triggers automatically
3. Builds MkDocs site and deploys to `gh-pages` branch
4. GitHub Pages serves from `gh-pages` branch

## Adding Documentation

### To add a new page:
1. Create `.md` file in appropriate directory under `docs/`
2. Add entry to `nav:` section in `mkdocs.yml`
3. Commit and push to main branch

### To modify existing content:
1. Edit the `.md` file directly
2. No need to update mkdocs.yml unless changing navigation
3. Changes deploy automatically after merge to main

## Important Files to Update

When setting up for a specific company:
1. Update `site_url` in mkdocs.yml
2. Update GitHub links in mkdocs.yml (`extra.social`)
3. Update repository URL in README.md
4. Replace placeholder content in docs with actual company information
# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
# Local development (serves on http://localhost:4000)
bundle exec jekyll serve -l -H localhost

# Docker development
docker compose up

# JavaScript minification
npm run build:js

# Watch JS changes
npm run watch:js
```

## Content Generation

Publications and talks are data-driven from TSV files:

```bash
# Generate publication markdown from TSV
python3 markdown_generator/publications.py

# Generate talk markdown from TSV
python3 markdown_generator/talks.py

# Update CV JSON from markdown
./scripts/update_cv_json.sh

# Generate talk location map
python3 talkmap.py
```

## Architecture

This is a Jekyll-based academic portfolio website using a customized Minimal Mistakes theme.

### Content Collections
- `_publications/` - Research papers (categories: books, manuscripts, conferences)
- `_talks/` - Speaking engagements with geolocation data
- `_teaching/` - Teaching activities
- `_pages/` - Static pages (cv.md, publication.md, talks.md)

### Data Flow
1. Source data in `markdown_generator/publications.tsv` and `markdown_generator/talks.tsv`
2. Python scripts generate individual markdown files with front matter
3. Jekyll builds static HTML from markdown + Liquid templates
4. GitHub Actions auto-runs talkmap notebook on push to talks/

### Key Configuration
- `_config.yml` - Main Jekyll config (site metadata, collections, author info)
- `_data/navigation.yml` - Site navigation structure
- `_data/cv_archive.json` - Structured CV data

### Templates
- `_layouts/` - Page layouts (default, single, archive, cv-layout, talk)
- `_includes/` - Reusable components (author-profile, archive-single variants)
- `_sass/` - SCSS stylesheets

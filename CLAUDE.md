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

Note: `_config.yml` is NOT live-reloaded—restart the server after editing it.

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

### TSV Format (publications.tsv)
Required columns: `pub_date` (YYYY-MM-DD), `title`, `venue`, `excerpt`, `citation`, `site_url`, `paper_url`, `url_slug`. Generated files are named `YYYY-MM-DD-[url_slug].md`.

### Publication Categories
Defined in `_config.yml` under `publication_category`: `books` (Books), `manuscripts` (Journal Articles), `conferences` (Conference Papers). Each publication's front matter `category` field must match one of these keys.

### Publication Views
Two views exist: "Selected" (`_pages/publication-selected.md`) and "All" (`_pages/publication-all.md`). Selected publications are filtered by `selected: true` in front matter.

## Architecture

Jekyll-based academic portfolio site using a customized Academic Pages / Minimal Mistakes theme (theme: `air`).

### Content Collections
- `_publications/` - Research papers (categories: books, manuscripts, conferences)
- `_talks/` - Speaking engagements with geolocation data
- `_teaching/` - Teaching activities
- `_pages/` - Static pages (about, cv, publication, talks, opportunities)

### Data Flow
1. Source data in `markdown_generator/publications.tsv` and `markdown_generator/talks.tsv`
2. Python scripts generate individual markdown files with front matter into `_publications/` and `_talks/`
3. Jekyll builds static HTML from markdown + Liquid templates
4. GitHub Actions auto-runs talkmap notebook on push to `talks/` or `talkmap.ipynb`

### Key Configuration
- `_config.yml` - Main Jekyll config (site metadata, collections, author info, publication categories)
- `_data/navigation.yml` - Site navigation structure (supports dropdown children for sub-pages)
- `_data/cv_archive.json` - Structured CV data (generated via `scripts/update_cv_json.sh`)

### Templates
- `_layouts/` - Page layouts (default, single, archive, cv-layout, talk)
- `_includes/` - Reusable components (author-profile, archive-single variants for publications/talks/CV)
- `_sass/` - SCSS stylesheets; site-level overrides go in `_sass/_themes.scss` or `_sass/layout/`

### Styling
SCSS structure: `_sass/_themes.scss` for theme variables, `_sass/layout/` for component styles, `_sass/vendor/` for third-party (font-awesome, susy grid, breakpoint, magnific-popup). The site theme is set to `air` in `_config.yml`.

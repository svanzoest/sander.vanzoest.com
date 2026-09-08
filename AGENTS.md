# AGENTS Guide: `svanzoest/sander.vanzoest.com`

This repository is a legacy **Jekyll static site** for Sander van Zoest’s personal blog and archived talks.

## Purpose
- Publish blog posts and static pages via Jekyll.
- Preserve historical blog content and talk material.

## Core technologies
- **Jekyll** with Liquid templates
- Markdown engine: **kramdown**
- Syntax highlighter: **rouge**
- Legacy frontend assets from HTML5 Boilerplate / 320 and Up
- Vendored JavaScript libraries in `js/libs`

Primary config:
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/_config.yml`

## Repository layout
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/_posts`  
  Blog content (mostly HTML posts with front matter)
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/_layouts`  
  Site layouts:
  - `default.html`: global page shell
  - `frontpage.html`: index listing of posts
  - `post.html`: individual post layout
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/_includes`  
  Shared partials for CSS/meta and scripts
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/index.md`  
  Homepage content/front matter
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/talks`  
  Archived static talk pages/slides
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/css`, `/js`, `/img`  
  Static frontend assets
- `/home/runner/work/sander.vanzoest.com/sander.vanzoest.com/.github/workflows/jekyll.yml`  
  CI workflow building the Jekyll site in Docker

## Rendering flow (mental model)
1. Jekyll reads `_config.yml`.
2. Content from `_posts` and markdown pages is loaded.
3. Layouts in `_layouts` and includes in `_includes` compose final HTML.
4. Static assets are served from `css`, `js`, and `img`.

## Known legacy/maintenance areas
- `/_import/mt.rb` and `/_db/mt.db`: migration/import artifacts from Movable Type.
- `/build`: old Ant-based optimization scripts from the original boilerplate era.

## Frontend loading detail
- jQuery is loaded from Google CDN with local fallback:
  - `_includes/boilerplate_analytics_scripts.html`
  - `404.html` (mirrors same pattern)

## Working conventions for agents
- Prefer minimal, surgical edits; preserve legacy behavior.
- Keep content and layout responsibilities separate (Jekyll conventions).
- When changing frontend loading or templates, check both shared includes and standalone pages like `404.html` for duplicated patterns.

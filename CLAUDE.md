# CLAUDE.md — Sunholo Websites

## Purpose

This repo hosts generated websites built by the Website Builder agent. Sites are served via GitHub Pages.

## CRITICAL: Git Workflow

**Commit directly to `main`. Do NOT create branches.**

- The executor clones `main` in direct-push mode (`AILANG_PUSH_BRANCH=main`)
- Do NOT run `git checkout -b`, do NOT create feature branches, do NOT create PRs
- Simply: edit files, `git add`, `git commit`, `git push origin main`
- If push fails due to remote changes, do a fast `git pull --rebase` then push again
- Never spend more than one attempt resolving merge conflicts — if rebase fails, force-push your changes

## Repo Structure

```
sites/<userId>/<siteSlug>/      # Generated websites (GitHub Pages serves these)
  index.html                    # Home page (required)
  about.html                    # Additional pages (optional)
  style.css                     # Shared stylesheet
  media/                        # User-uploaded images (already committed)
staging/<userId>/<siteSlug>/    # Raw uploaded files, briefs (not deployed)
```

## Building a Website

When you receive a build brief:

1. Read the brief from the message content (JSON with `description`, `style`, `content`, `instructions`)
2. Follow the `instructions` field — it specifies the exact output path and requirements
3. Create files under `sites/<userId>/<siteSlug>/`
4. Required output: at minimum `index.html` and `style.css`
5. Use relative paths for everything:
   - Page links: `href="about.html"` (not absolute paths)
   - CSS: `href="style.css"` (not absolute paths)
   - Images: `src="media/filename.jpg"` (already committed to media/ folder)
6. Commit all files in a single commit with a descriptive message
7. Push to main

## Style Guidelines

- Generate clean, semantic HTML5
- Responsive design (mobile-first)
- Follow the style direction in the brief (warm, clean, bold, elegant, fun)
- Include navigation between all pages
- Add a consistent header and footer across pages
- Use the site title from the brief

## What NOT to Do

- Do NOT create branches (see Git Workflow above)
- Do NOT modify files outside `sites/<userId>/<siteSlug>/`
- Do NOT delete other users' sites
- Do NOT install dependencies or run build tools
- Do NOT attempt to deploy — GitHub Pages deploys automatically on push to main

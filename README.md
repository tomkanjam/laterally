# laterally

Personal website and blog for the Laterally anonymous founder persona.

## Development

```bash
pnpm install
pnpm dev       # Start dev server at localhost:4321
pnpm build     # Build for production
pnpm preview   # Preview production build
```

## Writing Blog Posts

Create markdown files in `src/content/blog/`:

```markdown
---
title: "Post Title"
date: 2024-12-17
description: "Optional description"
draft: false
---

Your content here...
```

Set `draft: true` to hide from production.

## Deployment

Hosted on Cloudflare Pages. Deploys automatically on push to main.

**Build settings:**
- Build command: `pnpm build`
- Build output: `dist`
- Node version: 18+

## Content Management

See `content/` folder for drafts, ideas, and published content tracking.

Run `/content-review` in Claude Code to generate content ideas from recent development work.

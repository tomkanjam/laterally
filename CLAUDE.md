# CLAUDE.md

This is the Laterally personal brand repository - the anonymous founder persona for building AI products and sharing the journey.

## Project Overview

**Laterally** is an anonymous founder building AI-native products. This repo contains:
- Personal website (Astro static site)
- Blog posts (markdown in `src/content/blog/`)
- Content management system (drafts, ideas, published tracking)
- Claude Code agents and skills for content creation

**Platforms:**
- Website: laterally.ai
- Twitter: @laterallyai
- Hosting: Cloudflare Pages

**Repository:**
- GitHub: git@github.com:tomkanjam/laterally.git
- Sync: SSH (key-based auth on this server)

## The Product Being Built

The app repo is located at `/home/developer/projects/vyx`

It's an AI trading platform that lets users build sophisticated AI Traders using natural language. Key points for content context:
- Autonomous AI agents that trade 24/7
- Custom market filters, AI analysis, strategy execution
- Not a "crypto bot" - genuine trading intelligence
- AI-native (AI is the product, not a feature)
- Solo founder building with AI tools

**PRIVACY:** Never mention "vyx" in public content. Use generic terms like "the product" or "AI trading system."

## Development

```bash
pnpm dev      # Start dev server
pnpm build    # Build for production
pnpm preview  # Preview production build
```

Deploys automatically to Cloudflare Pages on push to main.

## Content Workflow

### Daily Content Review
Run `/content-review` to:
1. Check recent git commits in the vyx repo
2. Check recently closed issues
3. Generate content ideas from real development work
4. Draft posts in the Laterally voice

### Writing Blog Posts
1. Create markdown file in `src/content/blog/`
2. Use frontmatter: `title`, `date`, `description`, `draft`
3. Set `draft: true` while writing, remove when ready
4. Push to deploy

### Content Folders
- `content/drafts/` - Posts awaiting approval
- `content/published/` - Posted content with dates/engagement
- `content/ideas/backlog.md` - Topic ideas

## Voice Guidelines

**Core attributes:**
- Confident, not arrogant
- Dry humour, self-aware
- Technical but accessible
- Low ego, admits mistakes
- Approachable, workable

**Avoid:**
- "Excited to announce..."
- Guru/thought leader energy
- Corporate speak
- Emoji overload
- LinkedIn-style motivation

See `.claude/skills/founder-content/SKILL.md` for full voice guide.

## Privacy Rules (Critical)

**Never reveal:**
- Real name
- Product name (vyx)
- Specific identifying features
- Revenue/user numbers
- Location or employer history

**Safe to share:**
- General technical approaches
- Industry observations
- Lessons learned (anonymized)
- The fact you're building AI trading systems (generic)

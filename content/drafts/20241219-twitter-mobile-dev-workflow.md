# Mobile Dev Workflow

**Platform:** twitter (thread)
**Pillar:** build-in-public
**Status:** draft

## Content

**Tweet 1 (Hook):**
My main dev machine is an iPhone.

Not for emails. For actual development. Shipping features, debugging, deploying to production.

Here's the setup:

**Tweet 2 (Stack):**
The stack:
- Hetzner VPS (cheap, fast, EU)
- Termius (iOS SSH client)
- mosh (survives network switches)
- tmux + custom aliases
- Claude Code for the heavy lifting

Total cost: ~€4/month + whatever you're paying for AI.

**Tweet 3 (Browser Testing):**
"But what about browser testing?"

Chrome DevTools via remote debugging. Steel for automated browser sessions when I need to test flows.

Works better than expected. The phone is just a terminal—the server does everything.

**Tweet 4 (Deploy Flow):**
Deploy flow:
1. Code on server (Claude Code)
2. Commit + push via SSH
3. GitHub triggers Vercel
4. Live in ~30 seconds

No laptop in the loop.

**Tweet 5 (Setup Prompt):**
Want to set this up? Give this prompt to Claude Code or any LLM CLI:

"Set up a mobile dev environment. I need: mosh server, tmux with sensible defaults, tm aliases for quick session management. I'll connect via Termius on iOS. Make it persistent and fast."

**Tweet 6 (Why):**
Why bother?

The best dev environment is the one you actually have with you. Laptop battery dies, gets forgotten, TSA wants to inspect it.

Phone is always there. Muscle memory builds fast.

**Tweet 7 (CTA):**
Full setup guide with the complete LLM prompt on my blog:
laterally.ai/blog/mobile-dev-workflow

## Notes

Thread format, 7 tweets. Could trim to 5 if engagement drops off on longer threads. The prompt in tweet 5 is intentionally short for X - full version on blog.

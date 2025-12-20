---
title: "My main dev machine is an iPhone"
date: 2024-12-19
description: "A complete guide to shipping production code from your phone using a remote server, tmux, and AI coding assistants."
draft: true
---

![](/images/blog/mobile-dev-workflow-header.svg)

My main dev machine is an iPhone.

Not for checking Slack or reviewing PRs—for actual development. Writing features, debugging issues, deploying to production. The laptop stays closed more often than it opens.

This sounds like a flex. It's not. It's just a setup that works, and now I can code from anywhere with cell signal.

Here's everything you need to replicate it.

## The Stack

**Server:** Hetzner VPS (CX22 or similar, ~€4/month)
- Cheap, fast, EU-based
- Ubuntu LTS
- Your code lives here, not on your phone

**Terminal:** Termius on iOS
- Best mobile SSH client I've found
- Supports mosh protocol
- Syncs connections across devices

**Connection:** mosh (Mobile Shell)
- Survives network switches (WiFi → cellular → WiFi)
- Handles latency gracefully
- No dropped sessions when you walk between rooms

**Session Management:** tmux + aliases
- Persistent sessions that survive disconnects
- Multiple panes/windows
- `tm` aliases for fast attach/detach

**AI Assistant:** Claude Code (or Gemini CLI, aider, etc.)
- This is what makes mobile dev actually viable
- The AI writes code, you review and guide
- Typing on a phone keyboard becomes manageable when you're mostly reviewing

**Browser Testing:** Chrome DevTools + Steel
- Remote debugging for Chrome
- Steel for automated browser sessions
- The phone is just a viewport—testing happens server-side

**Deploys:** Vercel + GitHub
- Push to GitHub triggers deploy
- Live in ~30 seconds
- Zero laptop involvement

## Setup Guide

You can set most of this up by giving the following prompt to Claude Code (or any capable LLM CLI). SSH into your server, run your AI assistant, and paste this:

### The Prompt

```
I need you to set up a mobile-friendly development environment on this Ubuntu server. Here's what I need:

1. **mosh server**
   - Install mosh
   - Ensure firewall allows UDP ports 60000-61000
   - Test that mosh-server is running

2. **tmux with mobile-optimized config**
   - Install tmux if not present
   - Create ~/.tmux.conf with:
     - Sensible prefix (Ctrl-a instead of Ctrl-b, easier on mobile)
     - Mouse support enabled
     - Larger scrollback buffer (50000 lines)
     - Status bar with session name, time, and hostname
     - Easy pane splitting (prefix + | for vertical, prefix + - for horizontal)
     - vim-style pane navigation (prefix + hjkl)

3. **tm aliases for session management**
   - Add to ~/.bashrc or ~/.zshrc:
     - `tm` - list sessions or attach to last
     - `tm <name>` - attach to named session or create it
     - `tma` - attach to last session
     - `tml` - list all sessions
     - `tmk <name>` - kill named session
     - `tmn <name>` - new named session

4. **Quality of life for mobile**
   - Set EDITOR to something sensible (nano or vim)
   - Add common aliases (ll, la, gs for git status, etc.)
   - Ensure PATH includes common locations

After setup, show me:
- How to connect via mosh from Termius
- How to test the tmux config
- A quick verification that everything works

Keep it simple and standard. No exotic configs.
```

### Manual Steps

After running the prompt, you'll need to:

1. **Configure Termius on iOS:**
   - Add new host with your server IP
   - Set connection type to Mosh
   - Add your SSH key or password
   - Save and connect

2. **Set up Chrome remote debugging (if needed):**
   ```bash
   google-chrome --remote-debugging-port=9222 --headless
   ```
   Then forward the port via SSH or access directly if firewalled properly.

3. **Install Steel for browser automation:**
   Follow the Steel docs for your setup. I use it for testing user flows without needing a visible browser.

4. **Connect your deploy pipeline:**
   - Push your repo to GitHub
   - Connect Vercel to the repo
   - Every push to main deploys automatically

## Daily Workflow

```
1. Open Termius
2. Connect via mosh (tap saved connection)
3. `tm work` (attaches to work session or creates it)
4. `claude` or whatever AI CLI you use
5. Code, commit, push
6. Vercel deploys automatically
7. Test via forwarded ports or Steel
8. `Ctrl-a d` to detach when done
```

Session persists. Tomorrow you `tm work` and you're right where you left off.

## Why Bother?

Three reasons:

1. **Availability.** Phone is always with me. Laptop isn't. Ideas don't wait for convenient hardware.

2. **Simplicity.** One environment, one place code lives. No syncing, no "works on my machine."

3. **Focus.** A phone terminal is limited. Limitations reduce distraction. You do what you came to do and leave.

The AI assistant is what makes this practical. Without it, mobile coding is a novelty. With it, you're mostly reviewing and guiding rather than thumb-typing functions.

## Cost

- Hetzner CX22: ~€4/month
- Termius: Free tier works, premium is ~$10/month
- Claude/AI: Whatever you're already paying
- Vercel: Free tier for most projects

Under $20/month for a dev environment that fits in your pocket and never runs out of battery.

---

*Have questions about this setup? Find me on [Twitter/X](https://x.com/laterallyai).*

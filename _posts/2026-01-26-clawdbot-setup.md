---
layout: post
author: Xinyu Zhang
tags: [Tech, AI, Tutorial]
---

# Setting Up Clawdbot: A Claude-Powered Telegram Bot

I recently set up [Clawdbot](https://github.com/clawdbot/clawdbot), a self-hosted AI assistant that connects Claude to Telegram and other platforms. Here's what the process looked like and my initial impressions.

## What is Clawdbot?

Clawdbot is essentially a bridge that lets you run Claude (Anthropic's AI) with extended capabilities:
- Chat via Telegram, Discord, Slack, etc.
- Execute commands on your machine
- Access files, browse the web, schedule tasks
- Maintain persistent memory across sessions

Think of it as Claude Code (the CLI tool) but with:
1. Multi-platform messaging interfaces
2. Persistent background operation
3. Automation capabilities (cron jobs, reminders)

## Setup Process

### 1. Installation

```bash
npm install -g clawdbot
clawdbot gateway start
```

That's it for the basic install. The CLI guides you through initial configuration.

### 2. Authentication: Claude Subscription via CLI

I already have a Claude Max subscription, and the good news is Clawdbot can actually use it directly through **Claude Code CLI OAuth** (no separate API billing needed).

**Two authentication options:**
- **Option A: Anthropic API key** → Pay-per-token billing
- **Option B: Claude Code CLI OAuth** → Use your existing Claude subscription

I went with **Option B**. The setup:

```bash
# On any machine with Claude Code CLI installed
claude setup-token

# Then paste the token into Clawdbot
clawdbot models auth paste-token --provider anthropic
```

This lets me use my Claude Max subscription quota instead of setting up separate API billing. Much more convenient if you already pay for Claude.

### 3. Telegram Integration

Clawdbot has built-in Telegram support. The setup:

1. Talk to [@BotFather](https://t.me/botfather) on Telegram
2. Create a new bot (`/newbot`)
3. Get your bot token
4. Add it to Clawdbot config:

```bash
clawdbot gateway config.patch
# Add your Telegram token in the config
```

Within minutes, my bot was live. I could message it from my phone and get Claude responses with full context.

### 4. Web Search

Enabled Brave Search integration for web searches:

```json
{
  "tools": {
    "web_search": {
      "enabled": true
    }
  }
}
```

Now the bot can search the web when needed. Useful for looking up current information or checking facts.

## Initial Impressions

**What works well:**
- **Telegram access** — Having Claude in my pocket is convenient. I can ask questions while away from my computer.
- **Persistent memory** — The bot maintains context across sessions using markdown files in the workspace.
- **Automation potential** — Cron jobs and scheduled tasks open up interesting possibilities (like the stock sentiment analysis I'm planning).

**What I haven't fully utilized yet:**
- **Command execution** — The bot can run shell commands, but I'm still cautious about security. Need to explore this more.
- **Multi-session workflows** — Can spawn sub-agents for parallel tasks. Haven't needed it yet.
- **Skills system** — There's a whole plugin ecosystem I haven't touched.

**Honest assessment:**
So far, I haven't found Clawdbot dramatically better than just using Claude Code directly for most tasks. The main advantages:
1. **Remote access** via Telegram
2. **Background operation** — Can run scheduled tasks
3. **Multi-channel** — Could add Discord, Slack, etc.

For pure coding work, Claude Code is still more direct. But for automation and cross-platform access, Clawdbot opens up new possibilities.

## Hardware: The Accidental Home Server

An interesting side effect of Clawdbot's recent popularity: **Mac minis are getting attention as budget home servers**. At around phone prices, they're perfect for running 24/7 services like this.

I didn't need to buy one though — I had an unused **M2 MacBook Air** sitting around. With [Amphetamine](https://apps.apple.com/us/app/amphetamine/id937984704) (a free Mac app that prevents sleep), it's now my little home server.

**Setup:**
- M2 Air in clamshell mode, tucked away
- Amphetamine keeping it awake
- Clawdbot gateway running in the background
- Still have full access when I need to use it as a laptop

Not as elegant as a headless Mac mini, but it works perfectly. The M2 is efficient enough that power consumption isn't a concern.

## Next Steps

I'm planning to build a daily stock sentiment analysis bot using Clawdbot's cron system. It will:
- Scrape Reddit/StockTwits every morning
- Analyze sentiment on major tech stocks (GOOGL, TSLA, NVDA)
- Detect trending small-cap mentions
- Send a summary to Telegram before market open

This is exactly the kind of automation where Clawdbot shines — scheduled tasks that need AI analysis and messaging integration.

## Verdict

**Worth it if:**
- You want Claude on multiple platforms (Telegram, Discord, etc.)
- You need scheduled/automated AI tasks
- You want persistent context and memory

**Maybe skip if:**
- You just need a coding assistant (Claude Code is simpler)
- You don't have a spare machine to run the gateway 24/7
- Security concerns about command execution bother you

For me, the automation possibilities make it worthwhile. I'll revisit this post in a month to see how the stock analysis project turns out.

---

**Resources:**
- [Clawdbot GitHub](https://github.com/clawdbot/clawdbot)
- [Official Docs](https://docs.clawd.bot)
- [Discord Community](https://discord.com/invite/clawd)

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

### 2. Claude Max Subscription

I already have a Claude Pro subscription for personal use, but Clawdbot requires an **API key** from Anthropic's developer console. This is separate from the web subscription.

**Important distinction:**
- **Claude Pro ($20/mo)** → For web/app usage
- **Claude API** → Pay-per-token for programmatic access

For Clawdbot, you need the API. You can't use your Pro subscription to power the bot.

I set up billing with a small initial credit ($5). For typical personal use (a few dozen messages a day), this lasts quite a while.

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
- You're not ready to run API-based services
- Security concerns about command execution bother you

For me, the automation possibilities make it worthwhile. I'll revisit this post in a month to see how the stock analysis project turns out.

---

**Resources:**
- [Clawdbot GitHub](https://github.com/clawdbot/clawdbot)
- [Official Docs](https://docs.clawd.bot)
- [Discord Community](https://discord.com/invite/clawd)

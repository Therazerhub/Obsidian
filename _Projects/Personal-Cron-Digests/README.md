---
type: "project"
status: "active"
created: "2026-02-09"
tags: [automation, cron, llm, productivity, news]
---

# 🤖 Personal Cron Digest System

> *Replace all your newsletters with AI-curated, personalized content delivered exactly when you want it.*

---

## 🎯 What This Does

Instead of subscribing to 20+ newsletters that flood your inbox with generic content, this system delivers **personally curated** digests on your schedule:

| Digest | Frequency | What You Get |
|--------|-----------|--------------|
| [[GitHub Trending Digest]] | Daily 7am | Top 10 trending repos with analysis |
| [[Hacker News Digest]] | Daily 7am | Top 10 HN stories from past 24h |
| [[AI Twitter Digest]] | Daily 8am | Top 20 viral AI tweets |
| [[Product Hunt Picks]] | Daily 9am | Best 5-7 launches (AI/dev focused) |
| [[Daily Motivation]] | Daily 6am | 10 timeless tweets about building & shipping |
| [[YC Startup Spotlight]] | Weekly Mon 8am | Deep dive on one YC company |

---

## 🏗️ Architecture

```
cron-digests/
├── scripts/
│   ├── github_trending.py
│   ├── hackernews.py
│   ├── ai_twitter.py
│   ├── producthunt.py
│   ├── motivation.py
│   └── yc_spotlight.py
├── output/
│   └── YYYY-MM-DD/
│       ├── github-trending.md
│       ├── hackernews.md
│       └── ...
├── logs/
│   └── digest.log
└── config.json
```

---

## 📋 Setup Instructions

### 1. Prerequisites

```bash
# Ensure Python and pip are installed
python3 --version

# Install dependencies
pip install requests beautifulsoup4 openai
```

### 2. Configure API Keys

Create `~/.openclaw/workspace/cron-digests/config.json`:

```json
{
  "openai_api_key": "sk-...",
  "twitter_bearer_token": "optional",
  "producthunt_api_key": "optional",
  "delivery": {
    "method": "obsidian",
    "vault_path": "/home/ubuntu/.openclaw/workspace/Obsidian",
    "output_folder": "Daily Digests"
  },
  "schedule": {
    "timezone": "UTC"
  }
}
```

### 3. Set Up Crontab

```bash
crontab -e
```

Add these lines:

```cron
# Personal Cron Digests
0 6 * * * /usr/bin/python3 /home/ubuntu/.openclaw/workspace/cron-digests/scripts/motivation.py
0 7 * * * /usr/bin/python3 /home/ubuntu/.openclaw/workspace/cron-digests/scripts/github_trending.py
0 7 * * * /usr/bin/python3 /home/ubuntu/.openclaw/workspace/cron-digests/scripts/hackernews.py
0 8 * * * /usr/bin/python3 /home/ubuntu/.openclaw/workspace/cron-digests/scripts/ai_twitter.py
0 9 * * * /usr/bin/python3 /home/ubuntu/.openclaw/workspace/cron-digests/scripts/producthunt.py
0 8 * * 1 /usr/bin/python3 /home/ubuntu/.openclaw/workspace/cron-digests/scripts/yc_spotlight.py
```

### 4. Test Individual Scripts

```bash
cd /home/ubuntu/.openclaw/workspace/cron-digests
python3 scripts/github_trending.py --test
```

---

## 🔧 Delivery Methods

The system supports multiple delivery methods:

### Option 1: Obsidian Vault (Default)
Saves digests to `Daily Digests/YYYY-MM-DD/` in your vault.

### Option 2: Discord/Slack
Sends formatted messages to a channel.

### Option 3: Email
Sends HTML-formatted emails.

### Option 4: Telegram
Sends messages via Telegram bot.

---

## 📁 Output Format

Each digest creates a markdown file with:

```markdown
---
date: 2026-02-09
type: digest
category: github-trending
---

# GitHub Trending Digest
*February 9, 2026*

## 🚀 Top 10 Trending Repositories

### 1. [repo-name](link)
**⭐ 5,234** | **TypeScript** | **+892 today**

> Brief description of what it does...

**Why it matters:** Analysis of why this is interesting...

---
```

---

## 🔄 Customization

### Adding New Digests

1. Create a new script in `scripts/`
2. Follow the template in `scripts/template.py`
3. Add to crontab
4. Document in this README

### Modifying Curations

Each script has configurable filters:
- Topics to focus on
- Keywords to prioritize
- Sources to include/exclude

---

## 📊 Stats & Tracking

- [[Digest History]] - All generated digests
- [[Digest Analytics]] - What's been most useful

---

## 🔗 Related

- [[Vault Watcher]] - Auto-research on vault notes
- [[Lilly Setup]] - AI assistant configuration

---

*Created: 2026-02-09*  
*By: Lilly 🤖💕*

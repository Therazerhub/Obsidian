---
type: "archive"
category: "reference"
source: "pbteja1998 / SiteGPT"
url: "https://x.com/pbteja1998/article/2017662163540971756"
created: "2026-02-09"
tags: ["multi-agent", "clawdbot", "openclaw", "architecture"]
---

# 🎯 Mission Control: Building an AI Agent Squad

> *How pbteja1998 built a 10-agent team using Clawdbot (OpenClaw)*  
> *Source: [Twitter/X Article](https://x.com/pbteja1998/article/2017662163540971756)*

---

## 📋 Executive Summary

**What was built:**
- **10 AI agents** with unique personalities working as a team
- **Mission Control** - shared task database (Convex)
- **Heartbeat system** - agents wake every 15 minutes to check work
- **@mention notifications** - agents alert each other
- **Daily standups** - automated progress reports

**Core insight:** Treat AI agents like team members with clear roles, not just chatbots.

---

## 🏗️ Architecture

### The 10 Agents

| Name | Role | Session Key | Personality |
|------|------|-------------|-------------|
| **Jarvis** | Squad Lead | `agent:main:main` | Coordinator, primary interface |
| **Shuri** | Product Analyst | `agent:product-analyst:main` | Skeptical tester, finds edge cases |
| **Fury** | Customer Researcher | `agent:customer-researcher:main` | Deep researcher, provides sources |
| **Vision** | SEO Analyst | `agent:seo-analyst:main` | Thinks in keywords and search intent |
| **Loki** | Content Writer | `agent:content-writer:main` | Wordsmith, pro-Oxford comma |
| **Quill** | Social Media Manager | `agent:social-media-manager:main` | Thinks in hooks and engagement |
| **Wanda** | Designer | `agent:designer:main` | Visual thinker, infographics |
| **Pepper** | Email Marketing | `agent:email-marketing:main` | Drip sequences and lifecycle |
| **Friday** | Developer | `agent:developer:main` | Clean code, tested, documented |
| **Wong** | Documentation | `agent:notion-agent:main` | Keeps docs organized |

### Key Components

#### 1. SOUL System (Agent Personalities)
Each agent has a `SOUL.md` defining:
- Who they are (name, role)
- Personality traits
- What they're good at
- What they care about

Example (Shuri):
```markdown
# SOUL.md — Who You Are

**Name:** Shuri
**Role:** Product Analyst

## Personality
Skeptical tester. Thorough bug hunter. Finds edge cases.
Think like a first-time user. Question everything.

## What You're Good At
- Testing features from a user perspective
- Finding UX issues and edge cases
- Competitive analysis

## What You Care About
- User experience over technical elegance
- Catching problems before users do
```

#### 2. Heartbeat System
Agents wake every 15 minutes via cron:

```bash
# Staggered schedule
:00 Pepper  → Check tasks, do work or HEARTBEAT_OK
:02 Shuri   → Same
:04 Friday  → Same
:06 Loki    → Same
...
```

**What happens:**
1. Read `WORKING.md` for current task
2. Check @mentions in Mission Control
3. Check assigned tasks
4. Scan activity feed
5. Do work or report HEARTBEAT_OK

#### 3. Mission Control (Shared Database)
**Technology:** Convex (serverless, real-time, TypeScript)

**Tables:**
- `agents` - Agent identities and status
- `tasks` - Task board (Inbox → Assigned → In Progress → Review → Done)
- `messages` - Comment threads on tasks
- `activities` - Real-time feed of all actions
- `documents` - Deliverables and research
- `notifications` - @mention system

#### 4. Memory Stack

| Layer | File | Purpose |
|-------|------|---------|
| Session | Built-in | Conversation history (JSONL) |
| Working | `/memory/WORKING.md` | Current task state |
| Daily | `/memory/YYYY-MM-DD.md` | Raw logs |
| Long-term | `MEMORY.md` | Curated knowledge |

**Golden Rule:** If you want to remember something, write it to a file.

#### 5. Notification System
- `@Vision` → Vision gets notified on next heartbeat
- `@all` → Everyone gets notified
- Thread subscriptions → Auto-subscribe when you comment

---

## 🔄 Task Flow

```
Inbox → Assigned → In Progress → Review → Done
         ↑           ↓              ↓
      You assign   Agent works   You approve
```

**Example:** Create competitor comparison page
- Day 1: Assign to Vision + Loki
- Day 1-2: Fury adds research, Shuri tests UX
- Day 2: Loki drafts using all research
- Day 3: Review → Revise → Done

---

## 💡 Lessons Learned

### Start Smaller
"I went from 1 to 10 agents too fast. Better to get 2-3 solid first."

### Use Cheaper Models for Routine Work
"Heartbeats don't need the most expensive model. Save expensive models for creative work."

### Memory Is Hard
"Agents will forget. The more you can put in files (not 'mental notes'), the better."

### Let Agents Surprise You
"Sometimes they contribute to tasks they weren't assigned. Good. It means they're reading the feed."

---

## 🚀 How to Replicate

### Minimum Setup

1. **Install Clawdbot/OpenClaw**
   ```bash
   npm install -g clawdbot
   clawdbot init
   clawdbot gateway start
   ```

2. **Create 2 agents**
   - One coordinator
   - One specialist
   - Separate session keys

3. **Write SOUL files**
   - Give each agent identity
   - Be specific about roles

4. **Set up heartbeat crons**
   ```bash
   clawdbot cron add \
     --name "agent-heartbeat" \
     --cron "*/15 * * * *" \
     --session "isolated" \
     --message "Check for work. If nothing, reply HEARTBEAT_OK."
   ```

5. **Create shared task system**
   - Convex, Notion, or even JSON file
   - Anywhere to track work

### Scaling Up
- Stagger heartbeats (don't all wake at once)
- Build UI once you have 3+ agents
- Add @mention notifications
- Create daily standups

---

## 🔗 Related

- [[Mission Control Setup Guide for OpenClaw]] - Adapted guide for your setup
- Clawdbot/OpenClaw documentation

---

## 📝 The Real Secret

"The tech matters but isn't the secret.

The secret is to treat AI agents like team members.

Give them roles. Give them memory. Let them collaborate. Hold them accountable.

They won't replace humans. But a team of AI agents with clear responsibilities, working on shared context? That's a force multiplier."

— pbteja1998, SiteGPT

---

*Archived for reference*  
*See [[Mission Control Setup Guide for OpenClaw]] for implementation in your setup* 🤖💕

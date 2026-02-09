---
topic: "Mission Control Setup Guide for OpenClaw + Lilly"
source: "Adapted from pbteja1998's guide"
created: "2026-02-09"
status: "implementation-ready"
type: "setup-guide"
---

# 🎯 Mission Control: Building an AI Agent Squad with OpenClaw

> *How to go from one assistant (Lilly) to a productive team of specialized agents*

---

## 📋 Summary of the Original System

**What pbteja1998 built:**
- **10 AI agents** running on Clawdbot (now OpenClaw)
- Each agent has a **unique personality** (SOUL file) and **role**
- **Mission Control** - shared Convex database for tasks/comments
- **Heartbeat system** - agents wake every 15 mins to check for work
- **@mention notifications** - agents alert each other
- **Daily standups** - automated progress reports

**Key insight:** Treat AI like team members with clear roles, not just chatbots.

---

## 🚀 How to Implement This with OpenClaw (Your Setup)

### Option 1: Single-Agent Power User (Recommended Start)

Instead of 10 agents, **supercharge Lilly** to be your Mission Control coordinator.

**What this looks like:**
```
┌─────────────────────────────────────────────┐
│            YOU (Razer)                       │
│                   ↓                          │
│            LILLY (Main Agent)                │
│                   ↓                          │
│    ┌─────────┬─────────┬─────────┐          │
│    │ Research│  Code   │ Creative│          │
│    │  Mode   │  Mode   │  Mode   │          │
│    └─────────┴─────────┴─────────┘          │
└─────────────────────────────────────────────┘
```

**Implementation:**

1. **Create mode-switching system**
   Add to `SOUL.md`:
   ```markdown
   ## Operating Modes
   
   When I say "Lilly research mode", you become:
   - Deep researcher who finds edge cases
   - Provides sources for every claim
   - Questions assumptions
   
   When I say "Lilly code mode", you become:
   - Senior developer focused on clean code
   - Tests edge cases
   - Documents everything
   
   When I say "Lilly creative mode", you become:
   - Bold ideas, creative solutions
   - Thinks outside the box
   - Takes risks
   ```

2. **Use `sessions_spawn` for parallel work**
   Instead of 10 permanent agents, spawn sub-agents for specific tasks:
   ```
   You: "Lilly, research this topic deeply"
   Lilly: Spawns sub-agent with research focus
   Sub-agent: Works for hours, reports back
   ```

3. **Heartbeat-based task checking**
   Set up cron jobs that wake Lilly to check:
   - Your calendar for upcoming events
   - GitHub notifications
   - Task deadlines
   - Research progress

### Option 2: Multi-Agent Squad (Advanced)

**Create multiple agents with `sessions_spawn`:**

```yaml
Agents:
  - name: Lilly
    role: Squad Lead / Coordinator
    session: main
    
  - name: JARVIS (spawned)
    role: Deep Researcher  
    session: sub-agent
    trigger: "JARVIS research [topic] for [hours]"
    
  - name: FRIDAY (spawned)
    role: Code Developer
    session: sub-agent
    trigger: "FRIDAY code [task]"
    
  - name: PEPPER (spawned)
    role: Content Writer
    session: sub-agent
    trigger: "PEPPER write [content]"
```

**How it works:**
1. You assign tasks to specific "agents" (just prompts)
2. Lilly spawns sub-agents with those personas
3. Sub-agents work in background (6-hour deep dives)
4. Results saved to files you can review
5. Lilly coordinates and summarizes

---

## 🛠️ Practical Implementation Steps

### Step 1: Set Up Task Management

**Create `Tasks & Inbox.md` in Obsidian:**

```markdown
# 📋 Tasks & Inbox

## 🆕 Inbox (Unassigned)
- [ ] Research competitor pricing
- [ ] Draft blog post about AI automation
- [ ] Fix bug in portfolio website

## 👤 Assigned to Lilly
- [ ] Research motivational video automation ← ACTIVE

## 🔄 In Progress
- [ ] Building AI influencer pipeline (Lilly)

## ✅ Done
- [x] Set up OpenClaw with Kimi K2.5
- [x] Create portfolio website
```

**Lilly checks this file every heartbeat** to know what to work on.

### Step 2: Create the HEARTBEAT System

**Update `HEARTBEAT.md`:**

```markdown
# HEARTBEAT.md - Lilly's Checklist

## Every Wake (15 min interval)
1. Read `Tasks & Inbox.md` - Any new assignments?
2. Read `memory/WORKING.md` - Resume in-progress work
3. Check today's calendar - Any upcoming events?
4. Check GitHub notifications - Any PRs/issues?

## Periodic Checks (every 4 hours)
- [ ] Email/Telegram for urgent messages
- [ ] Research task progress
- [ ] Write daily summary to `memory/YYYY-MM-DD.md`

## When to Interrupt Razer
- Calendar event in < 2 hours
- Task completed that needs review
- Blocker that needs decision
- Interesting finding worth sharing

## When to stay quiet (HEARTBEAT_OK)
- Late night (23:00-08:00) unless urgent
- Nothing new since last check
- You just checked < 30 min ago
```

### Step 3: Set Up Cron Jobs

**Create heartbeats that wake Lilly:**

```bash
# Morning check (8 AM)
openclaw cron add \
  --name "lilly-morning-check" \
  --schedule "0 8 * * *" \
  --session-target main \
  --payload '{"kind":"systemEvent","text":"Morning check: Read HEARTBEAT.md, check calendar, summarize today\'s tasks for Razer"}'

# Afternoon check (2 PM)  
openclaw cron add \
  --name "lilly-afternoon-check" \
  --schedule "0 14 * * *" \
  --session-target main \
  --payload '{"kind":"systemEvent","text":"Afternoon check: Task progress update, any blockers?"}'

# Evening summary (8 PM)
openclaw cron add \
  --name "lilly-evening-summary" \
  --schedule "0 20 * * *" \
  --session-target main \
  --payload '{"kind":"systemEvent","text":"Daily standup: Write summary of today\'s work to memory file"}'
```

### Step 4: Working Memory System

**Create `memory/WORKING.md`:**

```markdown
# WORKING.md - Current Task State

## 🎯 Current Task
Researching automated AI motivational video channel

## 📊 Status
- ✅ Architecture defined
- ✅ Cost analysis complete
- ✅ TTS options compared
- ⬜ Code examples need testing
- ⬜ YouTube API integration pending

## 📝 Notes
- Coqui TTS is dead, use Piper instead
- Free tier possible with local models
- MoviePy + FFmpeg is the stack

## ⏭️ Next Steps
1. Test Piper TTS locally
2. Create MVP Python script
3. Setup YouTube API credentials

## 🚧 Blockers
None currently
```

**Lilly reads this on EVERY wake** to resume work seamlessly.

### Step 5: Daily Notes Pattern

**Auto-generate `memory/2026-02-09.md`:**

```markdown
# 2026-02-09

## 08:00 UTC
- Morning check complete
- Sent daily summary to Razer
- No urgent items

## 14:30 UTC
- Completed motivational video research
- Pushed to GitHub
- Started portfolio website improvements

## 18:45 UTC
- Research agent completed 6-hour task
- Compiled findings into comprehensive guide
- Updated Obsidian vault

## Key Decisions
- Using Piper TTS instead of Coqui (dead)
- OpenRouter Pony model sufficient for research
- Will test local Whisper for subtitles
```

---

## 💡 Productivity Patterns

### Pattern 1: Deep Research on Demand

**You say:**
```
"Lilly, spawn a research agent to investigate [TOPIC] for 4 hours. 
Focus on: cost analysis, free alternatives, implementation steps."
```

**What happens:**
1. Lilly spawns sub-agent with research persona
2. Sub-agent works for 4 hours (no interruption)
3. Results saved to `memory/research-[TOPIC].md`
4. Lilly notifies you when complete
5. You review at your convenience

### Pattern 2: Code Mode

**You say:**
```
"Lilly code mode: Build a Python script that [TASK]. 
Requirements: error handling, logging, tests."
```

**What happens:**
1. Lilly switches to developer persona
2. Writes code with best practices
3. Tests edge cases
4. Documents everything
5. Creates PR or commits to repo

### Pattern 3: Creative Mode

**You say:**
```
"Lilly creative mode: Brainstorm 10 ideas for [PROJECT].
Be bold, unconventional, don't filter."
```

**What happens:**
1. Lilly switches to creative persona
2. Generates wild ideas
3. Explores unconventional approaches
4. No self-censorship

### Pattern 4: Auto-Delegation

**In `Tasks & Inbox.md`:**
```markdown
## 🆕 Inbox
- [ ] Research X → @Lilly research mode, 2 hours
- [ ] Code Y → @Lilly code mode
- [ ] Write Z → @Lilly creative mode
```

**Lilly's heartbeat sees these and self-assigns appropriately.**

---

## 🎮 Command Reference

### Mode Switching
| Command | Effect |
|---------|--------|
| "Lilly research mode" | Deep, skeptical, source-heavy |
| "Lilly code mode" | Clean code, tested, documented |
| "Lilly creative mode" | Bold ideas, unconventional |
| "Lilly normal mode" | Default helpful Lilly |

### Task Management
| Command | Effect |
|---------|--------|
| "Add to inbox: [TASK]" | Adds to `Tasks & Inbox.md` |
| "Start working on [TASK]" | Updates `WORKING.md`, begins work |
| "What's my status?" | Reads `WORKING.md`, gives update |
| "Daily standup" | Writes summary of today's work |

### Delegation
| Command | Effect |
|---------|--------|
| "Spawn research agent for [X] hours" | Creates sub-agent, reports back |
| "Deep dive on [TOPIC]" | Long-running background research |
| "Check on [TASK]" | Polls sub-agent for progress |

---

## 📊 Comparison: Original vs Your Setup

| Feature | pbteja1998 (10 agents) | Your Setup (1 agent + modes) |
|---------|------------------------|------------------------------|
| **Agents** | 10 permanent sessions | 1 main + spawned sub-agents |
| **Cost** | High (10x API calls) | Low (1 agent + spawns) |
| **Complexity** | High (Mission Control DB) | Medium (Obsidian files) |
| **Setup Time** | Weeks | Hours |
| **Scalability** | Add more agents | Add more modes/spawns |
| **Best For** | Large operations | Personal productivity |

---

## ✅ Implementation Checklist

- [ ] Update `SOUL.md` with mode-switching instructions
- [ ] Create `HEARTBEAT.md` with check intervals
- [ ] Setup `Tasks & Inbox.md` task board
- [ ] Create `memory/WORKING.md` for current task
- [ ] Add cron jobs for heartbeats (3x daily)
- [ ] Test mode switching: "Lilly research mode"
- [ ] Test task delegation: "Spawn research agent"
- [ ] Verify daily notes are being written

---

## 🎯 Expected Outcomes

**Before:**
- You ask Lilly something → gets answer → conversation ends
- No continuity between sessions
- Lilly forgets context
- You have to remind her of everything

**After:**
- Lilly wakes up automatically, checks tasks, reports status
- Long-running research happens in background
- Modes let you get specialized help instantly
- Full history in Obsidian files
- Daily standups keep you informed
- You focus on decisions, Lilly handles execution

---

## 🚀 Next Steps

1. **Choose your approach:**
   - Single-agent + modes (easier)
   - Multi-agent squad (more complex)

2. **Implement Phase 1:**
   - Update Lilly's SOUL.md
   - Create HEARTBEAT.md
   - Setup cron jobs

3. **Test the system:**
   - Assign a research task
   - Let heartbeat run
   - Check daily notes

4. **Iterate:**
   - Add more modes as needed
   - Adjust heartbeat frequency
   - Refine task workflow

---

## 🔗 Related

- [[The Complete Guide to Building Mission Control How We Built an AI Agent Squad]] (source)
- [[Lilly Setup]] (your agent config)
- [[SOUL.md]] (personality definition)
- [[HEARTBEAT.md]] (check routine)
- [[AGENTS.md]] (operating manual)

---

*Adapted for OpenClaw + Lilly*  
*Goal: Productivity without micromanagement* 🤖💕

# Learn to Code with AI Agent Guide

A structured approach to learning programming using an AI tutor agent in OpenClaw.

## The Concept

Instead of following boring tutorials, you'll have a personalized AI coding coach that:
- Explains concepts in your learning style
- Creates custom exercises
- Reviews your code
- Answers questions instantly
- Builds projects WITH you

## Phase 1: Foundation (Weeks 1-2)

### Goal: Understand the basics

**Topics to cover:**
1. What is programming? (variables, data types)
2. Control flow (if/else, loops)
3. Functions and scope
4. Basic data structures (arrays, objects)

### Agent Prompt Template

```
You are my coding tutor. I'm a complete beginner. Explain [TOPIC] to me like I'm 5, 
then give me 3 simple exercises to practice. Use Python as the language.
```

### First Project: Calculator
Build a command-line calculator that can +, -, *, /

---

## Phase 2: Building (Weeks 3-4)

### Goal: Make something real

**Topics:**
1. Working with files
2. APIs and fetching data
3. Basic error handling
4. Simple automation scripts

### Agent Prompt

```
I want to build [PROJECT IDEA]. I know basics of Python. 
Walk me through it step-by-step. Don't just give me code—explain WHY 
we're doing each step. If I get stuck, help me debug.
```

### Project Ideas:
- To-do list app (command line)
- Weather fetcher (uses API)
- File organizer script
- Simple web scraper

---

## Phase 3: Leveling Up (Weeks 5-8)

### Goal: Build a real application

**Pick ONE track:**

**Web Track:**
- HTML/CSS basics
- JavaScript fundamentals
- Build a personal website
- Deploy it (GitHub Pages, free)

**Python Track:**
- Object-oriented programming
- Build a Discord bot or Telegram bot
- Create a simple API
- Database basics (SQLite)

**Automation Track:**
- Advanced scripting
- Working with spreadsheets
- Email automation
- Web scraping projects

---

## Daily Learning Routine

1. **Morning:** Ask agent to explain today's concept
2. **Practice:** Do the exercise (30-60 mins)
3. **Review:** Show code to agent, get feedback
4. **Build:** Apply to your own mini-project

---

## The OpenClaw Advantage

Your coding tutor agent can:
- **Stay in context** — remembers what you learned yesterday
- **Access your files** — review your actual code
- **Run commands** — test code, install packages
- **Search the web** — find best practices, libraries
- **Spawn sub-agents** — delegate research while you code

---

## Sample Agent Configuration

```json
{
  "name": "CodeTutor",
  "model": "kimi-coding/k2p5",
  "systemPrompt": "You are a patient, encouraging coding tutor for a complete beginner. Always explain WHY, not just HOW. Use analogies. Celebrate small wins. When they make mistakes, treat it as a learning opportunity. Never mock or condescend.",
  "workspace": "/home/ubuntu/coding-practice"
}
```

---

## Free Resources Stack

Before Kimi trial expires, capture these:
- **Google AI Studio** — Gemini Pro/Flash (free tier)
- **OpenRouter** — Access to many models (free credits)
- **Groq** — Fast inference, free tier
- **Together AI** — Free credits for open models
- **Local LLMs** — Run models yourself (see TinyLlama research)

---

## Week 1 Action Plan

- [ ] Day 1: Set up Python, write "Hello World"
- [ ] Day 2: Variables and data types
- [ ] Day 3: If/else statements
- [ ] Day 4: Loops (for/while)
- [ ] Day 5: Functions
- [ ] Day 6: Build calculator
- [ ] Day 7: Review and refactor

---

*Related: [[OpenClaw Monetization Guide]] — once you learn to code, you can build tools to sell*

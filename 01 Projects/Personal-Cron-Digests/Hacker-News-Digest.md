---
type: "digest-spec"
category: "hacker-news"
frequency: "daily"
time: "07:00 UTC"
status: "planned"
---

# Hacker News Digest

> Top 10 upvoted HN posts from the past 24 hours summarized with links.

## 📊 Specification

### Data Source
- **Source:** Hacker News Firebase API
- **Endpoint:** `https://hacker-news.firebaseio.com/v0/`
- **Timeframe:** Past 24 hours
- **Metrics:** Score, comment count

### Output Format

```markdown
---
date: 2026-02-09
type: digest
category: "hacker-news"
---

# Hacker News Top Stories
*February 9, 2026*

## 🔥 Top 10 Stories

### 1. [Story Title](link) ⭐ 892 💬 156
> Brief summary of the story...

**Key points:**
- Point 1
- Point 2
- Point 3

---

### 2. [Story Title](link) ⭐ 734 💬 89
...
```

### Content Filters
- Prioritize: AI, Dev Tools, Open Source, Startups
- Exclude: Cryptocurrency (unless major)
- Min score threshold: 100+

### Customization
- [ ] Focus topics: AI, Dev Tools, Productivity
- [ ] Min score: 50-200
- [ ] Include/exclude Show HN

---

## 🔗 Related
- [[README]] - Main project documentation
- [[GitHub Trending Digest]] - Complementary content

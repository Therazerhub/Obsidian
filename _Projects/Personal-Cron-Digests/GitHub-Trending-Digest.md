---
type: "digest-spec"
category: "github-trending"
frequency: "daily"
time: "07:00 UTC"
status: "planned"
---

# GitHub Trending Digest

> Top 10 trending repositories with stars, language, and quick takes on why each is interesting.

## 📊 Specification

### Data Source
- **Source:** GitHub Trending (github.com/trending)
- **Timeframe:** Past 24 hours or past 7 days
- **Languages:** All (or configurable filter)

### Output Format

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

> One-line description

**Why it matters:** 2-3 sentence analysis of why this is interesting...

---

### 2. [repo-name](link)
...
```

### Categories (Grouped)
- 🛠️ **Dev Tools** - CLI tools, productivity
- 🤖 **AI/ML** - LLMs, models, AI applications
- 🌐 **Web** - Frameworks, libraries, APIs
- 📱 **Mobile** - iOS, Android, Flutter
- 🔒 **Security** - Security tools, cryptography

### Customization Options
- [ ] Filter by language
- [ ] Exclude forked repos
- [ ] Prioritize recently created
- [ ] Filter by stars threshold

---

## 🔗 Related
- [[README]] - Main project documentation
- [[Digest History]] - Past digests

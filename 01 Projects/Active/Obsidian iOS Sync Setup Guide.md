# Obsidian iOS Sync Setup Guide

Complete guide to sync your Obsidian vault between desktop and iPhone/iPad.

## Option 1: Obsidian Official Sync (Paid - $8/month)

**Best for:** People who want zero-config, bulletproof sync

### Setup Steps:
1. **Desktop:** Settings → Sync → Sign up for Obsidian Sync
2. **iOS:** Download Obsidian app → Sign in with same account
3. Toggle sync on both devices
4. Select which folders to sync (or sync all)

**Pros:** Instant, handles conflicts well, encrypted
**Cons:** Costs money

---

## Option 2: iCloud Drive (Free)

**Best for:** Apple ecosystem users, free option

### Setup Steps:

#### Desktop (Mac/Windows):
1. Move your vault to iCloud Drive folder:
   - Mac: `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/`
   - Windows: `iCloud Drive/Obsidian/`

2. Open Obsidian → "Open folder as vault" → Select the iCloud location

#### iOS:
1. Download Obsidian app
2. "Open folder as vault" → Browse → iCloud Drive → Select your vault
3. Wait for initial sync

**⚠️ Important:**
- Keep vault under 10GB for iCloud reliability
- Don't edit same file on both devices simultaneously
- Can be slow to sync large files/images

**Pros:** Free, native Apple integration
**Cons:** Can be flaky, conflict resolution is manual

---

## Option 3: Git + Working Copy (Free-ish)

**Best for:** Developers, version control nerds

### Setup:
1. Put vault in Git repo
2. Desktop: Use Git normally
3. iOS: Get [Working Copy app](https://workingcopy.app) (free for basic use)
4. Clone repo in Working Copy
5. Open vault from Working Copy in Obsidian

**Pros:** Full version history, free, works offline
**Cons:** Manual sync (commit → push → pull), steep learning curve

---

## Option 4: Self-Hosted (Syncthing, Nextcloud)

**Best for:** Privacy-focused, tech-savvy users

See [[Local OpenClaw Setup Guide]] for similar self-hosting principles.

---

## Recommended for Razer

**Start with iCloud** (free, easy), then upgrade to **Obsidian Sync** if you hit issues or want reliability.

## Quick Start Checklist

- [ ] Decide sync method
- [ ] Move/copy vault to sync location
- [ ] Install Obsidian on iOS
- [ ] Open vault on mobile
- [ ] Test edit on one device, check on other
- [ ] Set up daily backup (just in case)

---

*Related: [[Local OpenClaw Setup Guide]] — similar self-hosting concepts*

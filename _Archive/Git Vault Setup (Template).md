# Git Vault Setup

Template for syncing this vault via Git.

## Quick Reference

```bash
# SSH method (recommended)
git clone git@github.com:Therazerhub/Obsidian.git

# Or with deploy key
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_lilly" git clone git@github.com:Therazerhub/Obsidian.git
```

## Obsidian Git Plugin Settings

- **Remote URL:** `git@github.com:Therazerhub/Obsidian.git`
- **Pull on startup:** ✅
- **Auto commit:** ✅ (every 5 min or on close)

---

**Note:** Actual credentials stored in `_secure/` (not committed).

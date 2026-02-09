# 🔧 Git Vault Setup (Template)

> *Sync your brain across all devices*

---

## 📋 Quick Reference

### 🐙 Clone Commands

```bash
# 🔐 SSH method (recommended)
git clone git@github.com:Therazerhub/Obsidian.git

# 🔑 Or with deploy key
GIT_SSH_COMMAND="ssh -i ~/.ssh/id_lilly" git clone git@github.com:Therazerhub/Obsidian.git
```

---

## ⚙️ Obsidian Git Plugin Settings

| Setting | Value |
|---------|:-----:|
| **Remote URL** | `git@github.com:Therazerhub/Obsidian.git` |
| **Pull on startup** | ✅ |
| **Auto commit** | ✅ (every 5 min or on close) |
| **Auto push** | ⚠️ Configure as needed |

---

## 🔐 Security

> [!WARNING] Credentials
> Actual credentials stored in `_secure/` — **NEVER commit these!**
> 
> - `_secure/API Keys.md`
> - `_secure/OpenClaw Secrets.md`
> - `_secure/Git cloning setup.md`

---

## 🔗 Related Research

- [[Research - Git Vault Setup]]
- [[Research - Or with deploy key]]

---

*Template secured by Lilly* 🤖💕🔒

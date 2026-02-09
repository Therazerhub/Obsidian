# 🔐 OpenClaw Configuration Secrets

> ⚠️ **CRITICAL: NEVER COMMIT TO PUBLIC REPOS**

This file contains all sensitive tokens for OpenClaw setup.
The `_secure/` folder is gitignored — keep it that way.

---

## NVIDIA API

**API Key:**
```
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
```

---

## OpenClaw Gateway

**Token:**
```
f5174d30480ff648aa13452f64cf85ef850c0f23386dc351
```

---

## Telegram Bot

**Bot Token:**
```
8062041399:AAFDZfCG90wZpg1assVqM9__zdX_ljTTTXY
```

---

## OpenRouter API Keys

**Key 1:**
```
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
```

**Key 2:**
```
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
```

---

## Environment Variables

Add these to your `~/.bashrc` or `~/.zshrc`:

```bash
# NVIDIA / OpenClaw
export NVIDIA_API_KEY=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
export OPENCLAW_GATEWAY_TOKEN=f5174d30480ff648aa13452f64cf85ef850c0f23386dc351

# OpenRouter (if needed)
export OPENROUTER_API_KEY=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
```

---

## How to Use

In config files, reference env vars:
```json
"apiKey": "${NVIDIA_API_KEY}"
```

NOT:
```json
"apiKey": "nvapi-..."  // ❌ NEVER hardcode
```

---

*Security audit by Lilly* 🤖💕🔒
*Date: 2026-02-09*

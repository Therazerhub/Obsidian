# Nvidia Kimi K2 Unlimited 💀

**Date:** 2026-02-09  
**Status:** ✅ Complete

---

## Why This Exists

When you hit the daily quota on your main Kimi K2.5 (the fast one), you're screwed — unless you have a backup. This setup adds **two free, unlimited backup models** via NVIDIA API. They're slower, but they work when you're desperate.

Think of them as your "I'm out of premium credits but still need to code" safety net.

---

## What Was Set Up

Two backup models added to the NVIDIA provider:

| Model | Alias | Context | Speed | Cost |
|-------|-------|---------|-------|------|
| `z-ai/glm4.7` | `z-ai` | 128k | Slow | Free |
| `minimaxai/minimax-m2.1` | `minimaxai` | 128k | Slow | Free |

Your main models still work as before:
- `kimi-coding/k2p5` — Primary fast model (current default)
- `nvidia/moonshotai/kimi-k2.5` — alias: `kimi`

---

## 🔐 Secrets Location

All API keys and tokens are stored in:
```
_secure/OpenClaw Secrets.md
```

**Environment Variables (Required):**
```bash
# Add to your shell profile (.bashrc, .zshrc, etc.)
export NVIDIA_API_KEY="${NVIDIA_API_KEY}"
export OPENCLAW_GATEWAY_TOKEN="${OPENCLAW_GATEWAY_TOKEN}"
```

*(Get actual values from `_secure/OpenClaw Secrets.md`)*

---

## OpenClaw Config Location
`~/.openclaw/openclaw.json`

### NVIDIA Provider Block
```json
"nvidia": {
  "baseUrl": "https://integrate.api.nvidia.com/v1",
  "apiKey": "${NVIDIA_API_KEY}",
  "api": "openai-completions",
  "models": [
    {
      "id": "moonshotai/kimi-k2.5",
      "name": "Kimi K2.5",
      "reasoning": false,
      "input": ["text"],
      "cost": { "input": 0, "output": 0, "cacheRead": 0, "cacheWrite": 0 },
      "contextWindow": 200000,
      "maxTokens": 8192
    },
    {
      "id": "z-ai/glm4.7",
      "name": "z-ai",
      "reasoning": false,
      "input": ["text"],
      "cost": { "input": 0, "output": 0, "cacheRead": 0, "cacheWrite": 0 },
      "contextWindow": 128000,
      "maxTokens": 8192
    },
    {
      "id": "minimaxai/minimax-m2.1",
      "name": "minimaxai",
      "reasoning": false,
      "input": ["text"],
      "cost": { "input": 0, "output": 0, "cacheRead": 0, "cacheWrite": 0 },
      "contextWindow": 128000,
      "maxTokens": 8192
    }
  ]
}
```

### Model Aliases
```json
"models": {
  "kimi-coding/k2p5": { "alias": "Kimi K2.5" },
  "nvidia/moonshotai/kimi-k2.5": { "alias": "kimi" },
  "nvidia/z-ai/glm4.7": { "alias": "z-ai" },
  "nvidia/minimaxai/minimax-m2.1": { "alias": "minimaxai" }
}
```

---

## How to Use

### List Available Models
```bash
openclaw models list
```

### Switch to a Backup Model (When You Hit Quota)
```bash
# Option 1: Set as default
openclaw models set nvidia/minimaxai/minimax-m2.1

# Option 2: Use alias for one-off commands
openclaw chat --model minimaxai "your prompt here"

# Option 3: Set via environment
export OPENCLAW_DEFAULT_MODEL=nvidia/minimaxai/minimax-m2.1
```

### Switch Back to Main Kimi
```bash
openclaw models set nvidia/moonshotai/kimi-k2.5
# or
openclaw models set kimi-coding/k2p5
```

---

## Verification

### Test API Directly (cURL)
```bash
# Make sure env var is set first
source ~/.bashrc  # or ~/.zshrc

curl -s -X POST https://integrate.api.nvidia.com/v1/chat/completions \
  -H "Authorization: Bearer $NVIDIA_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "minimaxai/minimax-m2.1",
    "messages": [{"role": "user", "content": "Say hi"}],
    "max_tokens": 50
  }'
```

**Test Result (2026-02-09):** ✅ Working
- Response time: ~2-3 seconds
- Model responds with thinking tags: `<think>...</think>`

---

## Important Notes

1. **Environment Variable Required** — The `NVIDIA_API_KEY` must be set in your shell or OpenClaw won't authenticate
2. **Slower Than Main Kimi** — These are free models; expect 2-5s response times vs instant
3. **Context Window** — 128k vs 256k on your main model
4. **Text Only** — No image support on these backup models
5. **Backup Location** — Original config saved at `~/.openclaw/openclaw.json.backup`

---

## Troubleshooting

### "No API key found for provider"
```bash
# Fix: Export the key (get value from _secure/OpenClaw Secrets.md)
export NVIDIA_API_KEY=your_key_here
```

### Model not showing in list
```bash
# Restart OpenClaw gateway
openclaw gateway restart

# Then check again
openclaw models list
```

### Slow responses
That's expected. These are free tier models. Switch back to `kimi-coding/k2p5` when your quota resets.

---

## Source Material

- Original setup notes: [[_Archive/nvidia-setup-notes-2026-02-09]]
- NVIDIA config reference: [[Projects/OpenClaw NVIDIA + Kimi K2.5 Config]]
- Reddit source: Found workaround for free NVIDIA models via `z-ai/glm4.7` and `minimaxai/minimax-m2.1`

---

**Status:** Ready for quota emergencies 💀🤖

*Last secured by Lilly* 🤖💕🔒

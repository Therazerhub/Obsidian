# ✅ OpenClaw NVIDIA + Kimi K2.5 (FIXED CONFIG)

This configuration correctly runs **Kimi K2.5 via NVIDIA API**
using OpenClaw `2026.2.6-3`.

---

## 🔑 Environment Variables (REQUIRED)

Do **NOT** hardcode secrets in JSON.

```env
NVIDIA_API_KEY=nvapi-REVOKED_AND_REGENERATED
OPENCLAW_GATEWAY_TOKEN=your_gateway_token```
```
🧠 Corrected `openclaw.json`
```{
  "meta": {
    "lastTouchedAt": "2026-02-08T10:05:00Z",
    "lastTouchedVersion": "2026.2.6-3"
  },

  "browser": {
    "headless": true,
    "noSandbox": true,
    "defaultProfile": "openclaw"
  },

  "models": {
    "mode": "merge",
    "providers": {
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
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 200000,
            "maxTokens": 8192
          }
        ]
      }
    }
  },

  "agents": {
    "defaults": {
      "model": {
        "primary": "nvidia/moonshotai/kimi-k2.5",
        "fallbacks": ["gpt", "gemini", "xai", "sonnet"]
      },

      "models": {
        "anthropic/claude-sonnet-4-5": { "alias": "sonnet" },
        "openai/gpt-5.2": { "alias": "gpt" },
        "google/gemini-3-flash-preview": { "alias": "gemini" },
        "xai/grok-4-1-fast-reasoning": { "alias": "xai" },
        "nvidia/moonshotai/kimi-k2.5": { "alias": "kimi" }
      },

      "maxConcurrent": 4,
      "subagents": {
        "maxConcurrent": 8
      }
    }
  },

  "commands": {
    "native": "auto",
    "nativeSkills": "auto",
    "restart": true
  },

  "gateway": {
    "mode": "local",
    "controlUi": {
      "allowInsecureAuth": true
    },
    "auth": {
      "mode": "token",
      "token": "${OPENCLAW_GATEWAY_TOKEN}"
    }
  },

  "plugins": {
    "entries": {
      "whatsapp": { "enabled": true },
      "discord": { "enabled": true },
      "telegram": { "enabled": true },
      "slack": { "enabled": true },
      "nostr": { "enabled": true },
      "googlechat": { "enabled": true },
      "imessage": { "enabled": false },
      "signal": { "enabled": false }
    }
  }
}
```

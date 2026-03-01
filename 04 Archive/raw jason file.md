# Legacy Config: Ollama (Pre-NVIDIA)

This was the working configuration before switching to NVIDIA API. Preserved as history.

**Status:** Legacy — Superseded by NVIDIA cloud provider

---

## Configuration

```json
{
  "meta": {
    "lastTouchedVersion": "2026.2.6-3",
    "lastTouchedAt": "2026-02-07T20:39:40.561Z"
  },
  "wizard": {
    "lastRunAt": "2026-02-07T20:39:40.557Z",
    "lastRunVersion": "2026.2.6-3",
    "lastRunCommand": "onboard",
    "lastRunMode": "local"
  },
  "models": {
    "providers": {
      "ollama": {
        "baseUrl": "http://127.0.0.1:11434/v1",
        "apiKey": "__OPENCLAW_REDACTED__",
        "api": "openai-completions",
        "models": [
          {
            "id": "kimi-k2.5:cloud",
            "name": "kimi-k2.5:cloud",
            "reasoning": false,
            "input": ["text"],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 131072,
            "maxTokens": 16384
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "ollama/kimi-k2.5:cloud"
      },
      "models": {
        "google/gemini-2.5-flash": {},
        "google/gemini-2.5-flash-lite": {},
        "ollama/kimi-k2.5:cloud": {}
      },
      "maxConcurrent": 4,
      "subagents": {
        "maxConcurrent": 8
      }
    }
  }
}
```

---

## Evolution

1. **2026-02-07:** Ollama local setup (this config)
2. **2026-02-08:** Switched to NVIDIA API for cloud compute
3. **2026-02-08 (later):** Switched BACK to Ollama for speed ⚡

---

## Why the Switch?

| Provider | Pros | Cons |
|----------|------|------|
| **Ollama** | Fast (local), free, private | Needs local GPU/CPU |
| **NVIDIA** | Huge context (200k+), no local compute | Latency, API limits |

**Current:** Back on Ollama for responsive chatting.

---

*Legacy configuration — preserved for reference* 📜

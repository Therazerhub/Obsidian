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
        "apiKey": "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",
        "api": "openai-completions",
        "models": [
          {
            "id": "moonshotai/kimi-k2.5",
            "name": "Kimi K2.5 (NVIDIA)",
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
      },

      "ollama": {
        "models": [
          {
            "id": "kimi:2.5",
            "name": "Kimi 2.5 (Ollama)",
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
        "fallbacks": ["ollama/kimi:2.5"]
      },

      "models": {
        "nvidia/moonshotai/kimi-k2.5": { "alias": "kimi" },
        "ollama/kimi:2.5": { "alias": "kimi-local" }
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
      "token": "f5174d30480ff648aa13452f64cf85ef850c0f23386dc351"
    }
  },
"channels": {
    "telegram": {
      "enabled": true,
      "dmPolicy": "pairing",
      "botToken": "8062041399:AAFDZfCG90wZpg1assVqM9__zdX_ljTTTXY"
    }
  },
  "plugins": {
    "entries": {
      "telegram": { "enabled": true }
    }
  }
}

```

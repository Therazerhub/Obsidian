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
  "auth": {
    "profiles": {
      "google:default": {
        "provider": "google",
        "mode": "api_key"
      }
    }
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
            "input": [
              "text"
            ],
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
      "workspace": "/home/ubuntu/.openclaw/workspace",
      "compaction": {
        "mode": "safeguard"
      },
      "maxConcurrent": 4,
      "subagents": {
        "maxConcurrent": 8
      }
    }
  },
  "messages": {
    "ackReactionScope": "group-mentions"
  },
  "commands": {
    "native": "auto",
    "nativeSkills": "auto"
  },
  "channels": {
    "telegram": {
      "enabled": true,
      "dmPolicy": "allowlist",
      "botToken": "__OPENCLAW_REDACTED__",
      "allowFrom": [
        "6001922744"
      ],
      "groupPolicy": "allowlist",
      "streamMode": "partial"
    }
  },
  "gateway": {
    "port": 18789,
    "mode": "local",
    "bind": "loopback",
    "controlUi": {
      "enabled": true,
      "basePath": "/openclaw"
    },
    "auth": {
      "mode": "token",
      "token": "__OPENCLAW_REDACTED__"
    },
    "tailscale": {
      "mode": "off",
      "resetOnExit": false
    }
  },
  "skills": {
    "install": {
      "nodeManager": "npm"
    },
    "entries": {
      "notion": {
        "apiKey": "__OPENCLAW_REDACTED__"
      }
    }
  },
  "plugins": {
    "entries": {
      "telegram": {
        "enabled": true
      }
    }
  }
}

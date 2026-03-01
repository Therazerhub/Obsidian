# NVIDIA Kimi K2.5 Provider Config (Original Source)

This is the raw configuration found on Reddit that became the basis for the working NVIDIA setup.

---

## Provider Block

```json
{
  "nvidia": {
    "baseUrl": "https://integrate.api.nvidia.com/v1",
    "apiKey": "${NVIDIA_API_KEY}",
    "api": "openai-completions",
    "models": [
      {
        "id": "moonshotai/kimi-k2.5",
        "name": "Kimi K2.5",
        "reasoning": true,
        "input": [
          "text",
          "image"
        ],
        "cost": {
          "input": 0,
          "output": 0,
          "cacheRead": 0,
          "cacheWrite": 0
        },
        "contextWindow": 256000,
        "maxTokens": 8192
      }
    ]
  }
}
```

## Model Reference

```json
{
  "model": {
    "primary": "nvidia/moonshotai/kimi-k2.5"
  }
}
```

---

## Differences from Deployed Config

| Aspect | This Source | Deployed |
|--------|-------------|----------|
| Context Window | 256,000 tokens | 200,000 tokens (conservative) |
| Reasoning | `true` | `false` (current choice) |
| Input Types | `text`, `image` | `text` only |

**Note:** The deployed config in [[Projects/OpenClaw NVIDIA + Kimi K2.5 Config]] uses slightly conservative values. Can be expanded to match this if needed.

---

## Source

Found on Reddit — r/OpenClaw or similar community discussion.

---

*Preserved for reference — original "found something" discovery doc* 🔍

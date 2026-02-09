Nvidia Api Key 
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

OPENCLAW_GATEWAY_TOKEN=f5174d30480ff648aa13452f64cf85ef850c0f23386dc351

json config which might work it was working before but was really slow but still god if we exceed the daily quota of our kimi code 2.5 
{
  "baseUrl": "https://integrate.api.nvidia.com/v1",
  "apiKey": "${NVIDIA_API_KEY}",
  "api": "openai-completions",
  "models": [
    {
      "id": "z-ai/glm4.7",
      "name": "kimi",
      "reasoning": false,
      "input": ["text"],
      "cost": {
        "input": 0,
        "output": 0,
        "cacheRead": 0,
        "cacheWrite": 0
      },
      "contextWindow": 128000,
      "maxTokens": 8192
    }
  ]
}



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

its something i had found out on reddit 
ere is a solution on Linux.

1. Backup your openclaw.json (default path: ~/.openclaw)
    
2. Find out "providers": { location, then add the configuration, here is an example.
    

  "nvidia": {
    "baseUrl": "https://integrate.api.nvidia.com/v1",
    "apiKey": "your build.nvidia.com API",
    "api": "openai-completions",
    "models": [
      {
        "id": "z-ai/glm4.7",
        "name": "z-ai",
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
        "contextWindow": 128000,
        "maxTokens": 8192
      },
      {
        "id": "minimaxai/minimax-m2.1",
        "name": "minimaxai",
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
        "contextWindow": 128000,
        "maxTokens": 8192
      }
    ]
  }

3. then add the model with cli

# set default model
openclaw models set nvidia/minimaxai/minimax-m2.1
# check the model list
openclaw models list

4. restart the openclaw

Hope this can help you.


so you can try this and make this model working , so 
we get 2 models one we currently using kimi k2.5 code and 
nvidia kimi 2.5 which is free and unlimited but slow as fuck 

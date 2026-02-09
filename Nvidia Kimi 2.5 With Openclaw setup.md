Here is a solution on Linux.

1. Backup your openclaw.json (default path: ~/.openclaw)
    
2. Find out "providers": { location, then add the configuration, here is an example.
    

  ```"nvidia": {
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
```

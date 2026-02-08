"nvidia": {

"baseUrl": "[https://integrate.api.nvidia.com/v1](https://integrate.api.nvidia.com/v1)",

"apiKey": "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",

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

And then reference it like this:  
"model": {

"primary": "nvidia/moonshotai/kimi-k2.5"

},
# Welcome to Groq

Groq is an AI solutions company delivering ultra-low latency inference with the first ever LPU™ Inference Engine. Groq API enables developers to integrate state-of-the-art LLMs such as Llama-2 into low latency applications. Learn more at [groq.com](https://groq.com/).



## Quick Start

**Note:** For the following to work with `--json`and `jq`, the minimum `curl` version required is v7.82.0. See [here](https://everything.curl.dev/http/post/json) for usage with older `curl` versions.



**List available models:**

```
curl -s -H"Authorization: Bearer ${APIKEY}" https://api.groq.com/v1/model_manager/models | jq
```

**Select desired model and generate inference by replacing "model\_id" parameter with desired model:**

```
curl -s -H"Authorization: Bearer ${APIKEY}" --json '{"model_id": "llama2-70b-4096", "system_prompt": "You are an unhelpful assistant", "user_prompt": "Are you a fish?"}' https://api.groq.com/v1/request_manager/text_completion | jq
```

**Note:** Mixtral is only available to select users at this time. If you are interested, please email us at [api@groq.com](mailto:api@groq.com).


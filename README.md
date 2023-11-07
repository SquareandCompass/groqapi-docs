# Welcome to Groq


Groq is an AI solutions company delivering ultra-low latency inference with the first ever Language Processing Unit™ accelerator. Groq API enables developers to integrate state-of-the-art LLMs such as Llama-2 into low latency applications. Learn more at [groq.com](https://groq.com).

## Quickstart

To generate an inference With Groq API, you must first generate a short-lived (1hr) authentication token like so:
```bash
# Export provided keys
GROQ_ACCESS_KEY_ID="<organization id field>"
GROQ_SECRET_ACCESS_KEY="<key provided>"
GROQ_DEFAULT_REGION="us-west-1"

# Retrieve token
TOKEN=$(curl -sH"Authorization: Bearer ${GROQ_SECRET_ACCESS_KEY}" https://api.groq.com/v1/auth/get_token | jq -r ".access_token")
```
Once you have done so, you can use the token to access the API:

<!-- checked -->
### Generate Code-Llama Inference
```bash
curl -sq --keepalive-time 60 -H"Authorization: Bearer ${TOKEN}" --json '{"model_id": "codellama-34b", "system_prompt": "You are helpful and concise coding assitant", "user_prompt": "Write a beautiful blogging website in html/css"}' https://api.groq.com/v1/request_manager/text_completion | jq
```

<!-- checked -->
### Generate Llama2 Inference
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" --json '{"model_id": "llama2-70b-4096", "system_prompt": "You are an unhelpful assistant", "user_prompt": "Are you a fish?"}' https://api.groq.com/v1/request_manager/text_completion | jq
```

<!-- checked -->
### List Models
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" https://api.groq.com/v1/model_manager/models | jq
```

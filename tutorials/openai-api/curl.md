# curl

Before you begin, ensure that you have a valid authentication token. See our Authentication page for more info.

> Note, you need to be using at least `curl` v7.82.0 for these to work with `--json`, as well as `jq`. For use with older `curl` versions look [here](https://everything.curl.dev/http/post/json)

Once you have done so, you can use the token to access the API:

{% tabs %}
{% tab title="Generate Code-Llama Completion" %}
{% code overflow="wrap" %}
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" https://api.groq.com/openai/v1/completions -H "Content-Type: application/json" -d '{ "stream": true, "model": "codellama-34b", "prompt": "Say this is a test", "max_tokens": 7, "temperature": 0.9 }'
```
{% endcode %}
{% endtab %}

{% tab title="Generate Llama2 Chat Completion" %}
{% code overflow="wrap" %}
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" https://api.groq.com/openai/v1/chat/completions -H "Content-Type: application/json" -d '{ "model": "llama2-70b-4096", "stream": true, "messages": [ { "role": "system", "content": "You are a helpful assistant." }, { "role": "user", "content": "Hello!" } ] }'
```
{% endcode %}
{% endtab %}

{% tab title="List Models" %}
{% code overflow="wrap" %}
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" https://api.groq.com/openai/v1/models | jq
```
{% endcode %}
{% endtab %}
{% endtabs %}

If you are already using the Official OpenAI client SDK in your favorite language, feel free to just change the endpoint to `https://api.groq.com/openai/v1` and you should be good to go.

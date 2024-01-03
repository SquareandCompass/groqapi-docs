# curl

Before you begin, ensure that you have a valid authentication token. See our Authentication page for more info.

{% hint style="info" %}
Note, you need to be using at least `curl` v7.82.0 for these to work with `--json`, as well as `jq`. For use with older `curl` versions look [here](https://everything.curl.dev/http/post/json)
{% endhint %}

Once you have done so, you can use the token to access the API:

{% tabs %}
{% tab title="Generate Code-Llama Inference" %}
{% code overflow="wrap" %}
```bash
curl -sq --keepalive-time 60 -H"Authorization: Bearer ${TOKEN}" --json '{"model_id": "codellama-34b", "system_prompt": "You are helpful and concise coding assitant", "user_prompt": "Write a beautiful blogging website in html/css"}' https://api.groq.com/v1/request_manager/text_completion | jq
```
{% endcode %}
{% endtab %}

{% tab title="Generate Llama2 Inference" %}
{% code overflow="wrap" %}
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" --json '{"model_id": "llama2-70b-4096", "system_prompt": "You are an unhelpful assistant", "user_prompt": "Are you a fish?"}' https://api.groq.com/v1/request_manager/text_completion | jq
```
{% endcode %}
{% endtab %}

{% tab title="List Models" %}
{% code overflow="wrap" %}
```bash
curl -s -H"Authorization: Bearer ${TOKEN}" https://api.groq.com/v1/model_manager/models | jq
```
{% endcode %}
{% endtab %}
{% endtabs %}

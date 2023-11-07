# Authentication

## API Auth
To authenticate with the API, use your provided auth token to generate a short-lived (1hr) token like so:

<!-- checked -->

```bash
# Export provided keys
GROQ_ACCESS_KEY_ID="<organization id field>"
GROQ_SECRET_ACCESS_KEY="<key provided>"
GROQ_DEFAULT_REGION="us-west-1"

# Retrieve token
TOKEN=$(curl -sH"Authorization: Bearer ${GROQ_SECRET_ACCESS_KEY}" https://api.groq.com/v1/auth/get_token | jq -r ".access_token")
```
You can now use this token as a Bearer Token in any of our APIs, like so

```bash
curl -s -H"Authorization: Bearer ${TOKEN}" https://api.groq.com/v1/model_manager/models | jq
```

## JWT Decode

If you would like to decode the JWT returned via `get_token`, you can use the following one-liner:
```bash
jq -R 'split(".") |.[0:2] | map(@base64d) | map(fromjson)' <<< $TOKEN
```

Output:
```json
[
  {
    "alg": "RS256",
    "kid": "b9ac601d131fd4ffd556ff032xxxxxxxxxx",
    "typ": "JWT"
  },
  {
    "aud": "234534543553453-xxxxxxxxx.apps.googleusercontent.com",
    "azp": "xxxxxxxxxx@xxxxxxxxxxxxx.iam.gserviceaccount.com",
    "email": "xxxxxxxxxxxxxx@xxxxxxxxxxx.iam.gserviceaccount.com",
    "email_verified": true,
    "exp": 1696280000,
    "iat": 1696280000,
    "iss": "https://accounts.google.com",
    "sub": "1000414895292000000"
  }
]
```
You can use this to find the expiration timestamp.

# API documentation
Your users can generate audio and video content with our AI-powered Fliki API. They can generate content in more in 75+ languages, 750+ voices and 100+ dialects!

## Pricing

| From | To | Price per credit |
| --- | --- | --- |
| 0 | 600 (10 min) | $0 |
| 600 (10 min) | 10800 (3 hrs) | $0.0035 |
| 10800 (3 hrs) | 21600 (6 hrs) | $0.003 |
| 21600 (6 hrs) | ∞ | $0.0025 per credit |

Note:
- Your card will be billed for usage worth of every $30.
- A one time payment of $9 will be charged upon API activation (to prevent abuse and validate your card).

## API key
Head over to [Accounts → API](https://app.fliki.ai/account/api-access) section and get the API key.

## API endpoints

### Language list
Get list of languages
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -X GET https://api.fliki.ai/v1/languages
```

### Dialect list
Get list of dialects
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -X GET https://api.fliki.ai/v1/dialects
```

### Voice list
Get list of voices (along with supported voice styles) by language (required) and dialect (required)
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"languageId": "<LANUGAGE ID>", "dialectId": "<DIALECT ID>"}' \
  -X POST https://api.fliki.ai/v1/voices
```

### Usage
Get usage for current billing period
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -X GET https://api.fliki.ai/v1/usage
```

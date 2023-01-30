# API documentation
Your users can generate audio and video content with our AI-powered Fliki API. They can generate content in 75+ languages, 900+ voices and 100+ dialects!

## Pricing
API is bundled with the [premium plan](https://fliki.ai/pricing).

## API key
- Subscribe to premium plan [Accounts → Credits](https://app.fliki.ai/account)
- Head over to [Accounts → API](https://app.fliki.ai/account/api) section and get the API key.

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

### Generate audio
Generate audio for given content (plain text or SSML, required), voice (required) and voiceStyle (optional)
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"content": "<CONTENT>", "voiceId": "<VOICE ID>", "voiceStyleId": "<VOICE STYLE ID>"}' \
  -X POST https://api.fliki.ai/v1/generate/audio
```
Note: The file generated are hosted on Fliki's storage server and is deleted automatically after one month. We expect you to copy it to your own storage server for long term availability.

Input data field `content` is limited to 2000 characters.

### Generate video
> Coming soon. Please fill out [this form](https://tally.so/r/nGegWe) to get early access to the video API.

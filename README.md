# API documentation
Your users can generate audio and video content with our AI-powered Fliki API. They can generate content in 75+ languages, 900+ voices and 100+ dialects!

## Pricing
API is bundled with the [premium plan](https://fliki.ai/pricing).

## API key
- Subscribe to premium plan [Accounts → Credits](https://app.fliki.ai/account)
- Head over to [Accounts → API](https://app.fliki.ai/account/api) section and get the API key.

## Samples
- [NodeJS](samples/node)

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
Returns list of dialects.

### Voice list
Get list of voices (along with supported voice styles) by language (required) and dialect (required)
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"languageId": "<LANUGAGE ID>", "dialectId": "<DIALECT ID>"}' \
  -X POST https://api.fliki.ai/v1/voices
```
Returns list of voices.

### Generate video / voiceover
Generate video or voiceover for given scenes
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"format": "video", "scenes": [{"content": "<CONTENT 1>", "voiceId": "<VOICE ID>"}, {"content": "<CONTENT 2>", "voiceId": "<VOICE ID>"}], "settings": {}}' \
  -X POST https://api.fliki.ai/v1/generate
```
Returns ID which you can pass to [Generate status](#generate-status) to check status and receive download URL.

format = `video` | `audio`

settings = 

```
{
 aspectRatio: 'portrait' | 'square' | 'horizontal',
 subtitle: {
   fontColor: 'yellow',
   backgroundColor: 'black',
   placement: 'top' | 'middle' | 'bottom',
 }
}
```

### Generate status
Check status for generate requests and download generated file
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"id": "<ID>"}' \
  -X POST https://api.fliki.ai/v1/generate/status
```
Returns status and download URL.

### Generate text-to-speech
Generate audio for given content (plain text or SSML, required), voice (required) and voiceStyle (optional)
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"content": "<CONTENT>", "voiceId": "<VOICE ID>", "voiceStyleId": "<VOICE STYLE ID>"}' \
  -X POST https://api.fliki.ai/v1/generate/audio
```
Returns download URL.

### Generate text-to-image
Generate image using AI for given content (plain text, required)
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"content": "<CONTENT>"}' \
  -X POST https://api.fliki.ai/v1/generate/text-to-image
```
Returns download URL.

### Generate tweet-to-video
Turn Tweet into video
```bash
curl \
  -H "Authentication: Bearer <API KEY>" \
  -H "Content-Type: application/json" \
  -d '{"url": "<Tweet URL>", "voiceId": "<VOICE ID>"}' \
  -X POST https://api.fliki.ai/v1/generate/tweet-to-video
```
Returns ID which you can pass to [Generate status](#generate-status) to check status and receive download URL.

## Note
- Input data field `content` across all applicable endpoint is limited to 1000 characters.
- The file generated are hosted on Fliki's storage server and is deleted automatically after one month. We expect you to copy it to your own storage server for long term availability.
- The API service is in early access only. The endpoints and other workings of API is subjected to change without notice.

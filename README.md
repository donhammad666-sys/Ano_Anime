# Ano Anime Studio

Production workspace for original anime episodes: silent video + script → persistent character voices → editable dialogue/SFX/music timeline → final MP4.

## Implemented
- Silent video upload and preview.
- Script parsing into dialogue segments.
- Persistent character voice profiles and voice-lock state.
- Separate dialogue, SFX and music timeline tracks.
- Per-segment preview, edit, timing, volume, mute, remove and regenerate workflow.
- Version/revision model in Supabase.
- Secure Supabase Edge Function adapter for TTS and rendering providers.
- Dark green/olive responsive UI.

## Real generation/rendering

The browser must not contain provider secrets or perform long 1-hour+ renders. The Supabase Edge Function `ano-anime-audio-api` is the secure adapter.

Set these Supabase Edge Function secrets:
- `TTS_PROVIDER_URL`
- `TTS_PROVIDER_KEY`
- `RENDER_PROVIDER_URL`
- `RENDER_PROVIDER_KEY`

Never put these values in `index.html`, `app.js`, or GitHub.

Google Cloud Text-to-Speech is a practical TTS starting point. Current Google documentation lists monthly free character allowances for Standard and WaveNet voices and permits generated audio in applications/media subject to Google Cloud terms. Custom/instant voice is separate, so free voice cloning should not be assumed.

Shotstack provides a REST video/audio editing API with a free new-account allowance for testing and paid production credits. Commercial API rendering is supported; submitted media/assets still need proper rights.

Free allowances are suitable for testing; long 60–90 minute episodes will normally require additional capacity.

## Voice consistency

A character profile stores the provider voice ID and settings. Regenerating one line reuses that profile, so the rest of the episode is not regenerated and the character voice remains consistent.

Only clone a voice you own or have explicit permission to use commercially.

## Licensed audio

Do not scrape YouTube/TikTok or random “no copyright” sites. Use your own audio or assets with a license that permits your intended commercial YouTube use.

## YouTube

No provider can guarantee YPP approval. Keep the story, characters, direction, editing, sound design and final episode meaningfully original.

## Supabase data model
- `anime_projects`
- `characters`
- `episodes`
- `episode_versions`
- `audio_segments`
- `segment_revisions`

## Deployment

Frontend can be hosted on GitHub Pages. Provider credentials remain in Supabase secrets.

# Ano Anime Studio

A browser-first anime post-production workspace for original videos.

## Current build
- Upload a silent anime video.
- Preview it locally.
- Paste a screenplay/dialogue script.
- Detect scene blocks and dialogue lines.
- Select a commercial-use voice/audio policy.
- Generate a production audio plan.
- No copyrighted anime clips, music, SFX, or voices are bundled.

## Important licensing design
This app deliberately does not scrape or automatically download random "no copyright" media. For monetized YouTube work, connect only providers/assets whose current license explicitly permits your intended commercial use.

The app cannot guarantee YouTube Partner Program approval. YouTube evaluates the finished channel/content for originality and repetitive or mass-produced content.

## Full renderer architecture
GitHub Pages can host the frontend, but long video rendering and private API keys should not run in browser code. Add a server-side rendering endpoint (Supabase Edge Function, Cloudflare Worker plus a rendering service, or another backend) and store provider keys as server secrets.

Recommended API contract:
- POST /api/analyze — receives video metadata + script, returns scene/audio cues.
- POST /api/voice — sends dialogue to a TTS provider whose plan explicitly permits commercial use.
- POST /api/assets — selects only user-owned or commercially licensed music/SFX.
- POST /api/render — combines the original video with generated dialogue, SFX and music using a server-side media renderer.
- GET /api/render/:id — returns render status and final MP4.

Never put provider API keys in index.html or app.js.

## Safe production rules
1. Use original characters, scripts and video.
2. Do not import clips/OSTs from existing anime.
3. Do not scrape YouTube/TikTok audio.
4. Do not use a voice clone unless you own the voice or have explicit permission.
5. Keep a license/source record for every external music/SFX/voice asset.
6. Prefer assets explicitly licensed for commercial use.
7. Keep final videos meaningfully edited and story-driven; AI assistance alone does not guarantee monetization.

## Local run
Open index.html directly for the browser-only prototype, or serve the folder with any static web server.

## Deployment
The repository is ready for GitHub Pages as a frontend prototype. A backend is required for the requested automatic voice/SFX/music generation and final MP4 rendering.

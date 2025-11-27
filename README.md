# SafariSense

SafariSense is a location-aware, voice-first audio guide for Kenya’s sites and parks. It uses GPS plus an AI assistant to deliver short narrations, handle live Q&A, and adapt content to the visitor’s exact position.

## What it does
- **Location-aware stories:** Plays site- and POI-specific narration as you move (geofence triggers).
- **Push-to-talk Q&A:** Hold the mic, ask a question, get a concise answer; barge-in cancels current speech.
- **Speech-to-text + GPT:** Records audio, transcribes via Whisper, and answers via GPT with site/POI and coordinates as context.
- **Multi-site selection:** Home page lists sites (e.g., Karura Forest, Fort Jesus, Nairobi National Park preview) and jumps into a guided map per site.
- **Map + simulation:** Leaflet map shows POIs and user position; arrow keys move a simulated dot; “Center on me / Use GPS / Start at Gate A” controls recentering.
- **Mock mode:** API can return placeholder responses to avoid spending credits (`MOCK_OPENAI`).

## Key pieces
- **Web (React/Vite):** Landing page, site cards, Leaflet map, mic controls, captions, sidebar POI preview/ask buttons.
- **API (Express):** Endpoints for transcription (`/transcribe` via Whisper) and answers (`/ask` / `/ask-text` via GPT), with logging and mock fallbacks.
- **Content:** POI data for Karura (gates, waterfall, caves, boardwalk, etc.) with English/Swahili snippets; more sites can be added via `sites.ts` and `poiData.ts`.

## UX highlights
- Hero landing with SafariSense branding, CTA buttons for featured sites, and a large background hero image.
- Guided view: sticky top controls (Lang, Detail, Barge-in), POI list with “Play Preview” and “Ask About,” and a bottom player bar.
- Mobile drawer for POIs and filters; map hint overlay and recenter controls.
- Captions show what was heard and answered; logs include coordinates and nearest POI IDs.

## Notes
- Place hero/brand assets in `apps/web/public/` (e.g., `hero.jpg`, `logo.png`).
- `.env` lives under `apps/api/.env` (keys like `OPENAI_API_KEY`, `MOCK_OPENAI`, `CORS_ORIGIN`, `PORT`).
- Nearest POI is sent with Q&A requests so answers can be POI-aware (no more `poiId: null`).

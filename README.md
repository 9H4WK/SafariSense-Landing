# SafariSense

SafariSense is a location-aware, voice-first audio guide for Kenya's sites and parks. It uses GPS plus an AI assistant to deliver short narrations, handle live Q&A, and adapt content to the visitor's exact position.

<img width="1920" height="888" alt="image" src="https://github.com/user-attachments/assets/663a9842-ed0a-40c0-8d17-2838d462fe7d" />

<img width="1920" height="957" alt="image" src="https://github.com/user-attachments/assets/90b6e205-6e12-43b5-bd75-22818b025edc" />


## What it does
- **Location-aware stories:** Plays site- and POI-specific narration as you move (geofence triggers).
- **Push-to-talk Q&A:** Hold the mic, ask a question, get a concise answer; barge-in cancels current speech.
- **Speech-to-text + stored content:** Records audio, transcribes, and answers using mapped site/POI data plus your coordinates for context.
- **Multi-site selection:** Home page lists sites (e.g., Karura Forest, Fort Jesus, Nairobi National Park preview) and jumps into a guided map per site.
- **Map + simulation:** Leaflet map shows POIs and user position; arrow keys move a simulated dot; "Center on me / Use GPS / Start at Gate X" controls recentering.

## Key pieces
- **Web (React/Vite):** Landing page, site cards, Leaflet map, mic controls, captions, sidebar POI preview/ask buttons.
- **API (Express):** Endpoints for transcription (`/transcribe`) and answers (`/ask`), using stored site/POI data with coordinates to ground responses; logging and mock fallbacks included.
- **Content:** POI data for Karura (gates, waterfall, caves, boardwalk, etc.) with English/Swahili snippets; more sites can be added via `sites.ts` and `poiData.ts`.

## UX highlights
- Hero landing with SafariSense branding, CTA buttons for featured sites, and a large background hero image.
- Guided view: sticky top controls (Lang, Detail, Barge-in), POI list with "Play Preview" and "Ask About," and a bottom player bar.
- Mobile drawer for POIs and filters; map hint overlay and recenter controls.
- Captions show what was heard and answered; logs include coordinates and nearest POI IDs.

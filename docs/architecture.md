# AquaGuard Architecture

AquaGuard has a React/Vite frontend and a Node.js/Express backend.

## Request flow

1. The frontend sends a location to `/risk` and `/summary`.
2. The backend risk engine combines seeded alert/report records with live weather and news signals.
3. The backend returns a score, confidence value, contributing factors, and supporting payloads.
4. The summary route sends the assessment context to IBM watsonx.ai when configured. Otherwise it returns a deterministic local summary.
5. The frontend renders the risk card, weather, news, alerts, and summary.

## Feature boundaries

- `backend/services/weatherService.js` calls Open-Meteo using the static city coordinate catalog.
- `backend/services/newsService.js` calls NewsAPI and filters results for water and environmental relevance.
- `backend/data/mockStore.js` supplies seeded dashboard alerts and reports used by the base risk calculation.
- `backend/data/reports.js` supplies seeded report-page records and stores new report-page submissions in memory.
- `frontend/src/context/UserAuthContext/index.jsx` implements local prototype authentication and persists users and the current profile in browser `localStorage`.
- `frontend/src/components/Leaderboard.jsx` supplies the seeded leaderboard users and scores.
- `frontend/src/pages/Overview/index.jsx` currently disables the backend overview path and generates country ratings locally from the ISO mapping.

## Configuration

Set `NEWSAPI_KEY` in the backend environment to enable NewsAPI results. Set the `WATSONX_*` variables documented in the root README to enable generated summaries. No API credential is committed as a fallback in source code.

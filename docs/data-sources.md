# AquaGuard Data Sources

AquaGuard is a hackathon prototype combining live, static, seeded, computed, and locally persisted data.

| Feature | Data source | Type |
|---|---|---|
| Weather | Open-Meteo forecast API | Live API |
| News | NewsAPI | Live API |
| Risk scoring | Local deterministic risk engine | Computed |
| Dashboard alerts | `backend/data/mockStore.js` | Seeded prototype data |
| Community reports | Seeded records plus backend in-memory submissions | Prototype data |
| Local advisories and flood zones | Backend data modules | Static/local data |
| Global risk map | ISO mapping plus hardcoded and deterministic ratings | Demo/generated data |
| Leaderboard | Seeded users plus local user points | Demo data |
| Account/profile | Browser `localStorage` | Prototype/local persistence |
| AI summary | IBM watsonx.ai, with deterministic fallback | AI plus fallback |

## Important boundaries

- Live weather and news depend on external services and configured credentials where required.
- Dashboard alerts and the base risk inputs are seeded prototype records.
- Community submissions are held in backend memory and are lost when the backend restarts.
- Browser authentication is local prototype authentication. Account data, including passwords, is stored in browser `localStorage`; it is not production authentication.
- The global map demonstrates a visualization pattern. Its country ratings are not live global contamination measurements.
- watsonx.ai summaries are generated only when the required environment variables are available and the service responds successfully.

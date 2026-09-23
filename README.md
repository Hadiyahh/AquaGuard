# 💧 AquaGuard

### Real-Time Water Risk Intelligence for Communities

🏆 **Winner — Best UN Hack, IBM × UNSA Hackathon**

AquaGuard is an AI-assisted water-risk intelligence platform that combines live environmental signals with community and prototype datasets to generate transparent, location-based water-risk assessments.

🌐 **[Live Demo](https://ibmz-kyfhs.vercel.app/)**  
🏆 **[Devpost — Best UN Hack](https://devpost.com/software/tbd-aqua-health-secure)**

<img
  width="1200"
  alt="AquaGuard dashboard showing location-based water risk, live weather, alerts, community signals, and an AI-assisted summary"
  src="https://github.com/user-attachments/assets/35fde3a5-803d-4e03-b294-b7f4f5e6df99"
/>

---

## 🎯 Overview

Water-safety information is often scattered across weather conditions, advisories, flood information, news, and community reports.

AquaGuard brings these signals into one dashboard so users can quickly understand:

- the current water-risk level for a location,
- how confident the system is in that assessment,
- which signals contributed to the result, and
- a plain-language explanation of the available evidence.

### Key Features

When a user searches for a location, AquaGuard can provide:

- **Risk Level** — Low / Medium-Low / Medium / Medium-High / High
- **Risk Score** — Numerical score from 0–100
- **Confidence Score** — Indicates how much supporting evidence is available
- **Live Weather Data** — Environmental conditions from Open-Meteo
- **Live News Signals** — Location-aware water and environmental news through NewsAPI
- **Contributing Factors** — Signals that influenced the assessment
- **Community Reporting** — Users can submit local water-condition reports
- **AI-Assisted Explanation** — IBM watsonx.ai can convert structured findings into plain-language guidance
- **Global Overview** — Prototype visualization showing how geographic risk patterns could be presented

> The global overview is a prototype visualization. Country ratings are locally generated from a combination of predefined and deterministic values and should not be interpreted as live global contamination measurements.

---

## 🧠 How It Works

### Core Philosophy

**Generative AI does not determine the water-risk score.**

AquaGuard separates deterministic risk calculation from AI-generated explanation.

1. **Collect Signals**  
   AquaGuard gathers available environmental and community information, including live Open-Meteo weather data, NewsAPI results, and prototype alert/report datasets.

2. **Calculate Risk**  
   Deterministic scoring logic evaluates the available signals and produces a risk score and classification.

3. **Calculate Confidence**  
   AquaGuard estimates how much supporting information is available for the assessment.

4. **Explain the Result**  
   When IBM watsonx.ai credentials are configured, a Granite model generates a human-readable explanation based on the structured result and supporting evidence.

5. **Display Evidence**  
   The dashboard surfaces risk level, confidence, contributing factors, weather, alerts, news, and community information.

If IBM watsonx.ai is unavailable, AquaGuard can return a deterministic fallback summary instead.

### Processing Pipeline

```text
User Searches Location
          ↓
React + Vite Frontend
          ↓
Node.js + Express API
          ↓
┌───────────────────────────────┐
│ Live Open-Meteo Weather       │
│ Live NewsAPI Results          │
│ Prototype Alerts              │
│ Prototype Community Reports   │
└───────────────────────────────┘
          ↓
Deterministic Risk Engine
          ↓
Risk Score + Confidence
+ Contributing Factors
          ↓
IBM watsonx.ai
(when configured)
          ↓
Plain-Language Explanation
          ↓
AquaGuard Dashboard
```

---

## 👩‍💻 My Contribution

AquaGuard was built collaboratively during the **IBM × UNSA Hackathon**.

My primary contributions focused on **full-stack integration and live environmental data**:

- Connected the **React + Vite frontend** with the **Node.js + Express backend**
- Integrated live weather data using **Open-Meteo**
- Helped integrate news, advisory, flood, and community-report signals
- Replaced mock dashboard content with live API-backed signals where available
- Connected external signals to the deterministic risk-scoring workflow
- Updated dashboard components to surface live risk information
- Added loading and fallback states for external API calls
- Added source-verification links for live signals
- Helped coordinate data flow between the frontend, backend, and risk engine
- Contributed to technical documentation and the hackathon presentation

🏆 AquaGuard received **Best UN Hack** at the IBM × UNSA Hackathon.

---

## 🏗️ Architecture

```text
                    ┌─────────────────────┐
                    │   React + Vite UI   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Node.js + Express   │
                    │       API           │
                    └──────────┬──────────┘
                               │
             ┌─────────────────┼─────────────────┐
             ▼                 ▼                 ▼
       Open-Meteo          NewsAPI        Prototype Data
         Weather                              Sources
             └─────────────────┼─────────────────┘
                               ▼
                    ┌─────────────────────┐
                    │ Deterministic Risk  │
                    │       Engine        │
                    └──────────┬──────────┘
                               │
                      Risk + Evidence
                               │
                               ▼
                    ┌─────────────────────┐
                    │ IBM watsonx.ai      │
                    │ Granite Models      │
                    └──────────┬──────────┘
                               │
                               ▼
                    Human-Readable Summary
```

---

## 🛠️ Tech Stack

| Area | Technology |
|---|---|
| **Frontend** | React, Vite |
| **Backend** | Node.js, Express |
| **AI** | IBM watsonx.ai, Granite models |
| **Weather Data** | Open-Meteo |
| **News Data** | NewsAPI |
| **Styling** | Tailwind CSS |
| **Architecture** | REST APIs |
| **Cloud / AI Authentication** | IBM Cloud, IBM IAM |

---

## ⚙️ Risk Scoring Logic

AquaGuard uses deterministic scoring rules rather than asking a generative AI model to decide the water-risk level.

### Example Prototype Weights

| Signal | Example Weight |
|---|---:|
| Boil-water advisory | +50 |
| Flood warning | +20 |
| Sewage overflow risk | +15 |
| Multiple community reports | +10 |

### Risk Classification

| Score | Classification |
|---:|---|
| 0–24 | Low |
| 25–39 | Medium-Low |
| 40–59 | Medium |
| 60–79 | Medium-High |
| 80–100 | High |

> The current hackathon prototype combines live signals with seeded and locally generated data. These values demonstrate the scoring architecture rather than representing a production water-quality model.

---

## 🏆 Hackathon Recognition

AquaGuard was developed for the **IBM × UNSA Hackathon** and received:

### 🏆 Winner — Best UN Hack

The project was designed around the United Nations Sustainable Development Goals, with its primary focus on:

### SDG 6 — Clean Water and Sanitation

Supporting areas include:

- 🏥 **SDG 3** — Good Health and Well-Being
- 🏗️ **SDG 9** — Industry, Innovation and Infrastructure
- 🏙️ **SDG 11** — Sustainable Cities and Communities
- 🌡️ **SDG 13** — Climate Action

➡️ **[View the winning Devpost submission](https://devpost.com/software/tbd-aqua-health-secure)**

---

## ⚠️ Prototype Boundaries

AquaGuard is a hackathon prototype rather than a production water-monitoring platform.

Current limitations include:

- Dashboard alerts begin with seeded prototype data
- Community reports begin with seeded records and new submissions are stored in memory rather than a durable database
- Submitted reports are lost when the backend restarts
- The global overview uses locally generated prototype country ratings rather than live global contamination measurements
- The leaderboard contains seeded demo users and scores
- User accounts and profile information are stored locally in browser `localStorage`
- The current login flow is prototype authentication and should not be treated as production security
- Some advisory and flood-data integrations exist in the project but are not yet fully connected to the active dashboard risk calculation
- IBM watsonx.ai summaries require valid IBM Cloud credentials
- News results depend on NewsAPI availability and relevance filtering

For a more detailed breakdown, see:

- [Data Sources & Prototype Boundaries](docs/data-sources.md)
- [Architecture](docs/architecture.md)

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- npm
- IBM watsonx.ai credentials *(optional; enables AI-generated summaries)*
- NewsAPI key *(optional; enables live news results)*

### Clone the Repository

```bash
git clone https://github.com/Hadiyahh/AquaGuard.git
cd AquaGuard/aquaguard
```

### Install Frontend Dependencies

```bash
cd frontend
npm install
```

### Install Backend Dependencies

```bash
cd ../backend
npm install
```

### Configure Environment Variables

Create a `.env` file in the backend directory.

```env
# IBM watsonx.ai
WATSONX_API_KEY=<your-api-key>
WATSONX_PROJECT_ID=<your-project-id>
WATSONX_BASE_URL=https://us-south.ml.cloud.ibm.com
WATSONX_MODEL_ID=<optional>
WATSONX_TIMEOUT_MS=10000

# News
NEWSAPI_KEY=<your-newsapi-key>

# Optional API protection
API_SHARED_TOKEN=<optional-token-for-post-requests>
```

> Never commit API keys, passwords, or credentials to source control.

---

## ▶️ Run Locally

### Start the Backend

```bash
cd aquaguard/backend
npm start
```

The backend runs at:

```text
http://localhost:4000
```

### Start the Frontend

In another terminal:

```bash
cd aquaguard/frontend
npm run dev
```

The frontend runs at:

```text
http://localhost:5173
```

---

## 🧪 Useful Commands

### Backend

```bash
npm start
npm run smoke
npm run test:contract
```

### Frontend

```bash
npm run dev
npm run build
npm run preview
```

---

## 📡 API Overview

The backend exposes REST endpoints used by the AquaGuard frontend.

| Endpoint | Method | Purpose |
|---|---|---|
| `/health` | GET | Backend health check |
| `/risk` | GET | Calculate risk for a location |
| `/alerts` | GET | Retrieve alert records |
| `/summary` | GET | Retrieve an AI-assisted or fallback summary |
| `/report` | POST | Submit a water-condition report |
| `/statistics/overview` | GET | Retrieve prototype overview statistics |
| `/user/companies` | GET | Retrieve prototype organization data |
| `/countries` | GET | Retrieve available country data |

### Example Risk Request

```bash
curl -sG "http://localhost:4000/risk" \
  --data-urlencode "location=Calgary, AB"
```

### Example Summary Request

```bash
curl -sG "http://localhost:4000/summary" \
  --data-urlencode "location=Calgary, AB"
```

### Example Community Report

```bash
curl -X POST "http://localhost:4000/report" \
  -H "Content-Type: application/json" \
  -d '{
    "location": "Windsor, ON",
    "issueType": "cloudy water",
    "description": "Water appears cloudy this morning."
  }'
```

---

## 🔐 Rate Limits & API Protection

| Policy | Current Limit |
|---|---|
| `/summary` | 25 requests/minute per IP |
| `/report` | 15 requests/minute per IP |
| Optional API guard | `API_SHARED_TOKEN` when configured |

---

## 📁 Project Structure

```text
AquaGuard/
├── aquaguard/
│   ├── backend/
│   │   ├── routes/
│   │   ├── services/
│   │   ├── lib/
│   │   ├── data/
│   │   └── server.js
│   │
│   └── frontend/
│       ├── src/
│       │   ├── api/
│       │   ├── components/
│       │   ├── pages/
│       │   ├── services/
│       │   └── utils/
│       │
│       └── index.html
│
├── docs/
│   ├── architecture.md
│   └── data-sources.md
│
└── README.md
```

---

## 📚 Documentation

More detailed technical information is available in:

- [Architecture](docs/architecture.md)
- [Data Sources & Prototype Boundaries](docs/data-sources.md)

---

## 🔮 Future Improvements

Potential next steps include:

- Improve environmental-news relevance filtering
- Connect additional advisory and flood-data services to the active risk engine
- Replace seeded alert/report data with durable live sources
- Add PostgreSQL or another persistent data store
- Replace local prototype authentication with secure backend authentication
- Improve risk-score calibration using validated environmental datasets
- Add multilingual support
- Add alert subscriptions for changing local conditions
- Add stronger community-report validation
- Expand observability and API monitoring
- Add production-grade deployment infrastructure

---

## ⚠️ Disclaimer

AquaGuard is an educational hackathon prototype intended to explore environmental-data aggregation, deterministic risk scoring, community reporting, and AI-assisted communication.

It should **not** be used as a substitute for official municipal water advisories, public-health guidance, emergency alerts, or professional environmental testing.


# 🌉 SevaSetu — Bridging Voices, Building India

**SevaSetu turns citizens' local development concerns — shared by text, voice, or photo in their
preferred Indian language — into structured, location-aware requests, and gives policymakers a live
dashboard of community priorities to guide public investment.**

> Built for **Build with AI: Code for Communities — Second Edition** (Hack2skill × Google Cloud).
> A Digital Public Good prototype — designed to scale across every state from one codebase.

🔗 **Live demo:** https://sevasetu-ai-yeke.onrender.com/
📹 **Demo video:** [add your YouTube/Drive link here]
📊 **Pitch deck:** [add your deck link here]

---

## The Problem

Citizen development requests across India live in fragmented systems — panchayat registers,
WhatsApp groups, grievance portals, word of mouth. They are never aggregated, never comparable,
and never aligned with national infrastructure data or investment plans. The result: public
spending follows legacy plans rather than live citizen demand, infrastructure gaps go unseen,
and the impact of large digital public infrastructure is hard to measure.

## What SevaSetu Does

**For citizens** — a voice-first, multilingual portal:
- Submit a development request by **voice, text, or photo** in any Indian language
- **AI intake** (Gemini): transcription, translation to English, category detection,
  urgency assessment *with a reason*, and district identification
- **GPS auto-location** → district, with a map pin
- Transparent status tracking: Received → Acknowledged → In progress → Resolved

**For policymakers** — a planning intelligence dashboard:
- **District demand hotspots** on a map (Google Maps with satellite/hybrid toggle)
- **Transparent priority score** per district: demand + urgency + infrastructure deficit +
  momentum + equity — auditable, not a black box
- **Gemini-generated project recommendations** mapped to real national schemes
  (Jal Jeevan Mission, PMGSY, Ayushman Bharat, etc.) with rationale and KPIs
- Live KPI cards, category breakdowns, and an AI executive brief — all in the
  policymaker's chosen language
- **Simulate live reports** mode for demos

## Google AI Stack (end-to-end)

| Layer | Google service | Used for |
|---|---|---|
| Generative AI | **Gemini API** (via Google AI Studio free tier) | Transcription, translation, classification, urgency + reason, photo analysis, project recommendations, executive briefs |
| Geospatial | **Google Maps JavaScript API** (Maps Demo Key) | Interactive map, satellite/hybrid views, demand hotspots |
| Geocoding | Google Geocoding API (key) with keyless fallback | GPS coordinates → district |
| Backend | **Firebase** (Anonymous Auth + **Cloud Firestore**) | Cross-device report sync, shared dashboard state |
| Voice | Web Speech API (voice input) + Google TTS voices | Voice-first intake and readouts |
| Hosting | Render (static) / Netlify / Vercel | Live deployment |

**No custom server.** The backend is serverless: the browser app talks directly to Firebase,
secured by Firestore rules. This keeps the prototype zero-cost and instantly scalable.

## Architecture Flow
 
Citizen (voice / text / photo / GPS)
        │
        ▼
Gemini API — structured extraction (language, category, urgency + reason, district, translation)
        │
        ▼
Cloud Firestore — single source of truth, synced live to every device
        │
        ▼
Policy Dashboard — hotspot aggregation → transparent priority score → Gemini scheme-mapped
recommendations → localized executive brief
```

## Repository Contents

| File | Purpose |
|---|---|
| `index.html` | The entire application — UI, AI intake, dashboard, Firebase client wiring |
| `firestore.rules` | Database security rules (this is the "backend" code) |
| `README.md` | This file |
| `logo.png` | Optional — app logo (inline SVG is used if absent) |

## Run Locally

No build step, no dependencies to install:

1. Download `index.html`
2. Double-click it — the app opens in your browser

> For voice and GPS, browsers require **HTTPS** — use the deployed link for those features.

## Backend Setup (Firebase, free Spark plan — no credit card)

1. [console.firebase.google.com](https://console.firebase.google.com) → create a project
2. **Firestore Database** → Create database
3. **Authentication** → Sign-in method → enable **Anonymous**
4. **Firestore → Rules** → publish the rules in [`firestore.rules`](firestore.rules)
5. **Authentication → Settings → Authorized domains** → add your deployed domain
   (e.g. `sevasetu-ai-xfre.onrender.com`)
6. **Project settings → Your apps → Web app** → copy the config into the app's ⚙️ settings
   (`apiKey`, `authDomain`, `projectId`, `storageBucket`, `messagingSenderId`, `appId`)

Once configured, the header shows **"☁️ Cloud sync on"** and reports submitted on any device
appear on every device.

## Optional Keys (app works without them in fallback mode)

| Key | Where to get it | Cost |
|---|---|---|
| Gemini API key | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) | Free tier, no billing |
| Google Maps Demo Key | [developers.google.com/maps/documentation/javascript/demo-key](https://developers.google.com/maps/documentation/javascript/demo-key) | Free, no billing, prototype use |

Without keys, the app runs in **demo mode**: rule-based text intake, keyless satellite map
tiles, and local-only storage. With keys, the full multilingual AI pipeline activates.

## Note on the Demo Build's Keys

For this hackathon demo, a **disposable free-tier Gemini key** is pre-seeded in the page so
judges can experience the full AI pipeline with zero setup. This key:
- has **no billing account linked** (it can never generate a charge — only free-tier quota limits),
- is **revoked and replaced after judging**, and
- would, in production, be replaced by a **Cloud Run proxy** so the key never reaches the browser.

The Firebase web config is public by design (it is client configuration, not a secret); data is
protected by Firestore rules. No service-account credentials are committed.

## Privacy & Safeguards

- Citizen identity is **anonymous** (Firebase anonymous auth) — no personal data required
- AI outputs are **decision support**, not automated decisions — a human reviews priorities
- Priority scoring is a **transparent, auditable formula** shown in the dashboard
- Reports are **append-only** for clients (rules disallow client update/delete)

## Limitations & Production Roadmap

- **AI calls run client-side** for the prototype → production moves Gemini behind Cloud Run
  (key server-side, rate limiting, logging, audit trail)
- **Free-tier quotas are shared** across demo visitors → production uses a billed project with
  per-user quotas
- **Rule-based demo fallback** when no key/quota → production guarantees AI availability
- Next: BigQuery warehouse for national-scale analytics, Earth Engine layers for
  climate/agriculture tracks, WhatsApp/messaging ingestion, Dialogflow voice IVR

## Scale Across India

One static codebase serves every state: multilingual by design (UI + AI in the citizen's
language), zero server infrastructure to provision, Firestore scales automatically, and the
priority engine works for any district given demographic and infrastructure inputs.

---

*SevaSetu complements India's grievance systems — it doesn't replace them. It turns them into a
planning intelligence layer.*


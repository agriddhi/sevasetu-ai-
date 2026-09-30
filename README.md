
# 🌉 SevaSetu — Bridging Voices, Building India

**SevaSetu turns citizens' local development concerns — shared by text, voice, or photo in their
preferred Indian language — into structured, location-aware requests, and gives policymakers a live
dashboard of community priorities to guide public investment.**

> Built for **Build with AI: Code for Communities — Second Edition** (Hack2skill × Google Cloud).
> A Digital Public Good prototype — designed to scale across every state from one codebase.

🔗 **Live demo:** https://sevasetu.onrender.com
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


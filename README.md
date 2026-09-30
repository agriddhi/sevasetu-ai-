
# 🌉 SevaSetu — Bridging Voices, Building India

**SevaSetu turns citizens' local development concerns — shared by text, voice, or photo in their
preferred Indian language — into structured, location-aware requests, and gives policymakers a live
dashboard of community priorities to guide public investment.**

> Built for **Build with AI: Code for Communities — Second Edition** (Hack2skill × Google Cloud).
> A Digital Public Good prototype — designed to scale across every state from one codebase.

🔗 **Live demo:** https://sevasetu-ai-yeke.onrender.com/
📹 **Demo video:** https://drive.google.com/file/d/1-KKQkeGR6X5em794AObSJn-Pn1jB1D4X/view?usp=sharing
📊 **Pitch deck:** https://github.com/agriddhi/sevasetu-ai-/blob/main/SevaSetu%20%E2%80%94%20Pitch%20Deck.pdf

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
- **AI intake**: transcription, translation to English, category detection,
  urgency assessment *with a reason*, and district identification
- **GPS auto-location** → district, with a map pin (permission-based, with manual correction)
- Transparent status tracking: Received → Acknowledged → In progress → Resolved

**For policymakers** — a planning intelligence dashboard:
- **District demand hotspots** on a map (Google Maps with satellite/hybrid toggle)
- **Transparent priority score** per district: demand + urgency + infrastructure deficit +
  momentum + equity — auditable, not a black box
- **AI project recommendations** mapped to real national schemes
  (Jal Jeevan Mission, PMGSY, Ayushman Bharat, etc.) with rationale and KPIs
- Live KPI cards, category breakdowns, and an AI executive brief — all in the
  policymaker's chosen language
- **Simulate live reports** mode for demos

## Google AI Stack (end-to-end)

| Layer | Google service | Used for |
|---|---|---|
| Generative AI | **Gemini API** (via Google AI Studio) | Transcription, translation, classification, urgency + reason, photo analysis, project recommendations, executive briefs |
| Geospatial | **Google Maps JavaScript API** | Interactive map, satellite/hybrid views, demand hotspots |
| Geocoding | Google Geocoding API (with keyless fallback) | GPS coordinates → district |
| Backend | **Firebase** (Anonymous Auth + **Cloud Firestore**) | Cross-device report sync, shared dashboard state |
| Voice | Web Speech API + Google TTS voices | Voice-first intake and readouts |
| Hosting | Render (static) | Live deployment |

**No custom server.** The backend is serverless: the browser app talks directly to Firebase,
secured by Firestore rules. This keeps the prototype zero-cost and instantly scalable.

## Architecture Flow

```text
Citizen (voice / text / photo / GPS)
        │
        ▼
AI Intake — structured extraction (language, category, urgency + reason, district, translation)
        │
        ▼
Cloud Firestore — single source of truth, synced live to every device
        │
        ▼
Policy Dashboard — hotspot aggregation → transparent priority score
                   → scheme-mapped recommendations → localized executive brief


# SevaSetu — Bridging Voices, Building India

Multilingual AI platform that turns citizen development requests (voice, text, photo,
GPS) in any Indian language into prioritized, scheme-mapped project recommendations
for national policymakers. Digital Public Good prototype — Build with AI Hackathon.

## Architecture
- Frontend: single-file HTML/JS (Tailwind CDN, Google Maps + Leaflet fallback)
- AI: Google Gemini API (transcription, translation, classification, urgency, vision, briefs)
- Backend: Firebase Anonymous Auth + Cloud Firestore (serverless, no custom server)
- Maps: Google Maps JS API (satellite/hybrid) with keyless Esri fallback
- Hosting: Netlify / Vercel (static)

## Backend setup (Firebase, free Spark plan)
1. console.firebase.google.com → create project
2. Firestore → Create database → then publish the rules in `firestore.rules`
3. Authentication → Anonymous → Enable
4. Project settings → Web app → copy config into the app's ⚙️ settings
   (FIREBASE_API_KEY, FIREBASE_AUTH_DOMAIN, FIREBASE_PROJECT_ID,
   FIREBASE_STORAGE_BUCKET, FIREBASE_MESSAGING_SENDER_ID, FIREBASE_APP_ID)

## Optional keys (app works without them in fallback mode)
- Gemini: aistudio.google.com/apikey (free)
- Google Maps Demo Key (free, no billing): developers.google.com/maps/documentation/javascript/demo-key

## Note on secrets
No API keys are committed. All keys are entered at runtime in the app's settings
and stored only in the user's browser. Firestore access is governed by firestore.rules.


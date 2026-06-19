# Sample — Fitness Mobile App (Early-Career Wireframes)

Personal research sample from my early Business Analyst / Product Analyst work. A 9-screen wireframe set for a consumer fitness tracking mobile app.

## Screens
1. **Login** — username + password, forgot-password, sign-up CTA
2. **Registration** — gender, age, height, weight
3. **Dashboard** — Body Fat %, BMI, recommended daily kCal, quick-log tiles (Coffee, Water, Diet, Bar, Study, Snacks, Cycling, Jogging, Exercise)
4. **Exercise** — target vs actual calories, total time, add-workout
5. **Diet** — target vs consumed kCal, add-meal
6. **Cycling** — target vs actual, minutes spent, add-meal
7. **Statistics Report** — target vs actual; download as PDF / Excel
8. **Social Sharing** — share progress to social
9. **Interactive Notifications** — diet target, workout target, share status

## What this sample shows
- Early BA capability: turning a consumer-app brief into a complete screen flow
- KPI-led dashboard design (BMI, body fat, calorie deltas)
- Cross-cutting features (sharing, export, notifications) treated as first-class

## Today's lens
A current take would replace static wireframes with: Health Connect / Google Fit / Apple Health ingestion → FHIR Observation normalization → RAG-grounded recommendations citing clinical guidelines (ADA, JNC-8). See [vittobh/pm-os PRD #7 — wellness-iot-rag](https://github.com/vittobh/pm-os/blob/main/prds/07-wellness-iot-rag.md).

---
Author: **Vittobha Vignesh S** · [Portfolio](https://vittobh.github.io) · [GitHub](https://github.com/vittobh)
License: MIT

---

## 🚀 Live Prototype
**[https://vittobh.github.io/sample-fitness-app-wireframes/](https://vittobh.github.io/sample-fitness-app-wireframes/)**

Working front-end with light + dark mode (toggle in header). Mock backend by default; add an Anthropic/Gemini/Grok key to browser localStorage to attempt live calls.

## 🤖 AI Use Cases (2026)
See **[AI_USE_CASES.md](AI_USE_CASES.md)** — agentic upgrade plan, OSS stack, concrete prompts, evals.

## ⚠️ Limitations
See **[LIMITATIONS.md](LIMITATIONS.md)** — what's mocked vs needs API keys / server proxy.

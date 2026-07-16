# 📱 AI PM in Consumer & Social — Scale Amplifies Everything

> **TL;DR:** Consumer AI lives and dies on habit formation, and social products run the largest ML systems on earth (feeds, moderation). The PM tension unique to this domain: engagement optimization vs. user wellbeing — at a scale where a 0.1% error rate is a million bad experiences a day.

---

## 1. The AI surface area

| Use case | Scale reality | PM notes |
|---|---|---|
| **Feed ranking & recommendations** | TikTok/Reels/YouTube — the most consequential ML products ever shipped | Engagement objectives shape culture; guardrails are ethics at scale |
| **Content moderation** | Billions of items/day, ML-first with human appeal layers | Precision/recall tradeoffs are *speech policy*; adversaries adapt weekly |
| **AI assistants & companions** | ChatGPT (900M weekly actives, 50M paying — Feb 2026, verified), Meta AI across apps, character/companion apps | Retention beyond novelty is THE problem; companions raise attachment/safety questions |
| **Creative tools** | Filters, generative images/video, music (Spotify AI DJ — launched Feb 2023) | Provenance/deepfake handling now expected & increasingly regulated |
| **Search & discovery** | Answer-engines (Perplexity et al.) vs. classic search | Citation UX + publisher-ecosystem tension |
| **Personalization everywhere** | Duolingo's Birdbrain (per-exercise difficulty prediction) as the craft example | Invisible AI often outvalues chatty AI |

## 2. What's different in consumer

- **Novelty is a liar.** AI features spike then crater; judge at day-30/60/90 retention, never launch week ([metrics traps](../03-product-craft/metrics-for-ai-products.md)). The consumer-AI graveyard is full of viral demos.
- **Latency & cost at consumer scale**: 100M free users × pennies per session = a margin catastrophe without routing/caching/small-model discipline; free tiers are loss-leaders that must convert or cap ([cost](../02-technical-depth/model-selection-and-cost.md)).
- **The error budget is public.** Consumer failures trend on TikTok within hours (see: every chatbot scandal in the [failure files](../06-case-studies/failures-hall-of-lessons.md) — Tay's 16-hour lifespan remains the canonical adversarial-users lesson).
- **Trust & safety is a core loop, not a department**: minors, self-harm-adjacent content, parasocial attachment to companions, deepfakes of real people — consumer AI PMs own mitigations in-product (age gates, classifiers, escalation UX), with regulation active (DSA in the EU, minors' codes, deepfake laws).
- **Engagement vs. wellbeing** is the defining tension: the ranker that maximizes watch-time can maximize outrage; strong candidates volunteer counter-metrics (creator diversity, "time well spent" proxies, user-stated satisfaction) and note where they'd cap optimization.

## 3. Monetization patterns (consumer AI, 2026)

| Pattern | Example (verified) | Note |
|---|---|---|
| Freemium subscription | ChatGPT Plus (50M+ payers across tiers, Feb 2026) | The reference conversion machine |
| Premium AI features on core sub | Duolingo Max (GPT-4-powered Roleplay/Explain-My-Answer, launched Mar 2023 at $29.99/mo) | AI as tier-differentiator |
| Free AI + ads/commerce | Meta AI's path across its apps | Assistant as engagement surface for the ad machine |
| Usage credits for creation | Image/video-generation apps | Aligns cost, adds friction |

## 4. Interview drill

**"Design an AI feature for Instagram to help creators."** *(A representative consumer product-sense prompt — Meta's AI-track interviews live here.)* Strong path: creator segments (aspiring vs. mid vs. top — pick mid: enough data, most pain) → jobs (ideation, editing, posting-time, audience Q&A, monetization) → pick ideation+remix: "what's resonating in your niche" insights + AI draft variations of *their own* content (grounded in their voice, not generic slop) → design: suggestions in the creation flow, always editable, clearly labeled AI-assist → tensions to name unprompted: feed flooding with AI content (platform-level provenance labels), homogenization of creator voice (measure content diversity), minors as creators (guardrails) → metrics: creator retention & posting cadence, content performance lift vs. control, *audience-side* engagement quality (guardrail: report rate on AI-assisted posts), platform content-diversity index → rollout: opt-in beta with mid-tier creators, watch qualitative feedback for voice-authenticity complaints.

**The Duolingo arc is worth retelling in consumer interviews:** a decade of quiet personalization ML (Birdbrain) → first-mover GPT-4 partnership (Max, launched with GPT-4 on day one) → then the 2025 "AI-first" memo triggering user backlash and a public CEO walk-back. Lessons: invisible AI compounds; visible AI strategy is a brand statement; consumer trust punishes "AI replaces humans" framing fast ([case study](../06-case-studies/duolingo.md)).

## 5. Know these names
TikTok's For You page (the recommendation benchmark) · ChatGPT growth curve (fastest-to-100M estimate, Jan 2023; 900M WAU Feb 2026) · Meta AI + "Product Sense with AI" interview round · Spotify Discover Weekly/AI DJ · Duolingo Birdbrain/Max · Tay (2016) · DSA (EU platform regulation) · provenance/watermarking (C2PA) · companion-app safety debates.

---
*Related: [consumer metrics traps](../03-product-craft/metrics-for-ai-products.md) · [failures](../06-case-studies/failures-hall-of-lessons.md) · [Duolingo case](../06-case-studies/duolingo.md)*

# 🛒 AI PM in E-commerce & Retail — The Original ML Playground

> **TL;DR:** E-commerce is where product ML grew up: recommendations, search, pricing, forecasting. High data volume + high error tolerance + direct revenue attribution = the fastest experimentation loops in AI PM. The craft here is *incrementality* — proving your model beats the baseline in dollars, not vibes.

---

## 1. The AI surface area

| Use case | The gold-standard example | PM notes |
|---|---|---|
| **Recommendations** ("you may also like", homepage ranking) | Amazon; Netflix's rec system (personalization influencing ~80% of streaming hours, self-estimated $1B+/yr retention value — 2015 paper, the canonical citation) | The baseline to beat is "popularity" — and it's embarrassingly strong |
| **Search & discovery** | Semantic search fixing "dress for beach wedding" ≠ keyword match | Hybrid (keyword+vector) wins ([rag.md](../02-technical-depth/rag.md) concepts apply) |
| **Dynamic pricing & promotions** | Airlines/rideshare heritage | Fairness/perception landmines — personalized pricing reads as discrimination fast |
| **Demand forecasting & inventory** | Every major retailer | Quiet, huge ROI; classic ML, seasonal drift management |
| **GenAI: product content** — descriptions, images, video, translation | Catalog-scale content generation | Brand-consistency evals; marketplaces do this at million-SKU scale |
| **GenAI: shopping assistants & conversational commerce** | The 2024–26 wave (+ agentic checkout experiments) | Grounding on live catalog/inventory is everything — a bot recommending out-of-stock items is worse than none |
| **Customer service automation** | Returns/WISMO ("where is my order") deflection | The Klarna arc applies verbatim ([case study](../06-case-studies/klarna-ai-assistant.md)) |
| **Fraud & abuse** | Payment fraud, returns abuse, review fraud | Threshold economics ([fintech](fintech.md) cousins) |

## 2. What makes this domain *easy* (and what that does to the bar)

- **Errors are cheap**: a bad recommendation costs a shrug. This unlocks aggressive automation — no human-in-loop for ranking.
- **Feedback is instant and monetary**: clicks, carts, conversions arrive in hours; A/B infrastructure is mature.
- **Data is abundant**: behavioral exhaust at scale, self-labeling (purchases = labels).

Consequence: **the bar is incrementality, not capability.** Nobody asks "can AI recommend products?" — they ask "does your model beat the current one by enough basis points of conversion to matter, at what serving cost?" Interview answers here must be experiment-shaped: hypothesis → A/B → revenue-per-session lift → guardrails (returns, margin mix, diversity of catalog exposure).

## 3. The metrics culture

North stars: **conversion rate, revenue per session, AOV, repeat rate.** AI-specific guardrails worth naming:

- **Recommendation diversity / serendipity** — pure engagement-optimization converges on bestsellers and cannibalizes discovery (the filter-bubble of shopping).
- **Marketplace fairness** — does the ranker starve new sellers? (cold start as a *policy* question).
- **Margin-aware ranking** — clicks ≠ profit; watch the model learning to push low-margin bestsellers.
- **Returns rate** — the counter-metric for persuasive AI (great at convincing, wrong for the customer).
- **Popularity-baseline delta** — always report lift vs. the dumb baseline, or you're measuring theater.

## 4. GenAI-era patterns (2024–2026)

- **Catalog intelligence**: normalize messy seller data → structured attributes (the unglamorous unlock for search, recs, and ads).
- **Grounded shopping assistants**: RAG over live catalog + inventory + policies; hallucinated specs/prices = complaints and legal exposure (price promises are quasi-contractual — the Chevy-$1-Tahoe energy applies to commerce bots).
- **Agentic commerce** (emerging): AI agents that search, compare, and *check out* on the user's behalf — raises brand-new questions: who is your customer when an agent shops (bot-vs-human detection inverts), how do you rank for agents, payment authorization UX. Great "frontier" topic to raise in interviews.
- **Content at scale with brand evals**: generated descriptions/imagery gated by brand-voice rubrics ([evals](../02-technical-depth/evals.md)) and provenance disclosure where required.

## 5. Interview drill

**"Design an AI-powered gift-finding experience for an e-commerce platform."** Strong path: user & moment (panic gifter, 3 days out, knows recipient not products) → why current search fails (queries describe *people*, catalogs describe *products*) → design: conversational or structured elicitation (recipient, occasion, budget) → semantic matching to catalog + reranking on availability/delivery-by-date (**grounding on live inventory + shipping promise** — call this out) → output as curated sets with "why this fits" explanations → metrics: gift-flow conversion, delivery-date hit rate (the trust metric for gifting), return rate vs. control, repeat usage next occasion → experiment plan vs. curated-gift-guide baseline. Bonus: cold start (no recipient history — elicit, don't infer) and seasonal load (Q4 latency budgets).

## 6. Know these names
Amazon's recommendation legacy · Netflix 2015 paper (80% / $1B figures — date them) · Spotify Discover Weekly (100B+ tracks streamed in its first decade — verified 2025) as the personalization-brand case · Shopify (democratized AI features for SMB merchants) · "WISMO deflection" · popularity baseline · multi-armed bandits (explore/exploit for cold start) · agentic checkout debates.

---
*Related: [metrics](../03-product-craft/metrics-for-ai-products.md) · [strategy](../03-product-craft/ai-product-strategy.md) · [Netflix case study](../06-case-studies/netflix-recommendations.md)*

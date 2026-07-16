# 📊 Question Bank: Execution, Metrics & Analytical

> The round where AI PM candidates most often stumble: quoting model metrics when asked about product success. Arm yourself with the [three-layer stack](../../03-product-craft/metrics-for-ai-products.md) and the [GAME-AI frame](../answer-frameworks.md). 🔵 = reported/sourced · ⚪ = practice.

---

## Tier 1: Reported 🔵

1. "You launch a new embedding model API. What are your top three success metrics?" *(coach-compiled; worked in [metrics §7](../../03-product-craft/metrics-for-ai-products.md))*
2. "Define a north star metric for Instagram Reels, and explain the trade-off if you prioritize Reels over Stories." *(Meta analytical; the conflicting-metrics pattern: find the shared upstream goal, state the decision rule, name the counter-metric)*
3. "How would you measure success for OpenAI? What if instrumentation went down?" *(also a strategy question; the blind-flying half tests judgment: leading proxies, support volume, finance signals, qualitative pulse)*
4. "Your chatbot's response quality dropped 15% last week. How do you debug this?" *(the debugging classic; five-step method in [evals §6](../../02-technical-depth/evals.md))*
5. "What guardrail metrics would you track?" *(Perplexity)*
6. "Tell me about a time you cut scope to ship faster." *(OpenAI engineering-collab round: execution behavioral; have the story with the tradeoff reasoning explicit)*

## Tier 2: Metric definition drills ⚪

Define north star + 2 guardrails + 1 counter-metric for each (90 seconds apiece):

7. AI meeting summarizer in a work suite. *(worked version: [metrics §7](../../03-product-craft/metrics-for-ai-products.md))*
8. AI-generated product descriptions for marketplace sellers.
9. AI symptom-checker in a telehealth app. *(guardrails ARE the product here: escalation correctness, unsafe-advice rate)*
10. Code-review AI in enterprise CI. *(velocity × quality pairing; [developer-tools](../../05-domains/developer-tools.md))*
11. AI travel-booking agent. *(task completion, booking-error rate, override rate; [agents §5](../../02-technical-depth/ai-agents.md))*
12. "AI overviews" atop a search product. *(user: answer quality/time-to-info; ecosystem: publisher clicks; business: ad interaction; a three-way tension, name it)*
13. AI onboarding assistant for a B2B SaaS. *(time-to-first-value, activation rate; counter-metric: support tickets merely deferred)*

## Tier 3: Analysis & debugging scenarios ⚪

14. AI draft-reply feature: acceptance rate 60% and rising, feature retention falling. Diagnose. *([metrics self-test](../../03-product-craft/metrics-for-ai-products.md))*
15. Your AI feature's A/B shows +12% task completion but +30% session length. Good or bad? What do you check? *(is longer engagement value or friction? segment: struggling users vs. delighted power users)*
16. Thumbs-down rate doubled after a model upgrade, but eval scores improved. Explain the contradiction and your next steps. *(eval set no longer represents production distribution; or the upgrade changed style/tone in ways the rubric doesn't capture; or a vocal segment shifted; slice, then refresh the golden set)*
17. Enterprise tenant reports "the AI got worse this month." No global metric moved. Investigate. *(per-tenant slicing: their data/index changed, their use case drifted, their new users differ; B2B quality is per-tenant, not global; [enterprise-saas](../../05-domains/enterprise-saas.md))*
18. Your support AI's deflection rate hit the 70% target, but NPS fell 8 points. Walk your analysis. *(the Klarna pattern: check reopens, escalation friction, resolution-vs-abandonment split; [case study](../../06-case-studies/klarna-ai-assistant.md))*
19. Usage of your AI feature spikes every Monday 9-11am and the p95 latency triples. What do you do this week vs. this quarter? *(this week: rate limiting/queue UX/cache warm; quarter: capacity planning, routing, precompute)*
20. Leadership asks "what's our AI feature's ROI?" Your instrumentation only tracks usage. Build the answer plan. *(proxy chain: usage → time-saved estimates (validated by study on a sample) → cost; be explicit about confidence levels; propose the instrumentation you actually need)*

## Tier 4: Launch & rollout ⚪

21. Design the rollout plan for an AI feature in a product with 50M users. *(shadow → internal → 1% canary gated on evals + live guardrails → segment expansion → GA; kill criteria pre-committed; [PRD §9](../../03-product-craft/prd-template-ai-feature.md))*
22. Your canary shows eval scores fine but a 3× spike in "regenerate" clicks. Ship or hold? *(hold: regeneration is revealed dissatisfaction your evals didn't capture; investigate before the metric-blind expand)*
23. Legal approves your AI feature for the US only; 40% of users are elsewhere. Design the launch anyway. *(geo-gating with graceful messaging, parallel compliance track, learn-from-US-cohort plan)*
24. A model provider announces your production model retires in 90 days. Run the migration. *(candidate models → golden-set bake-off → price/latency check → canary migration → full cut; the story is why your evals make this boring; [model-selection §7](../../02-technical-depth/model-selection-and-cost.md))*
25. Post-launch, 0.5% of AI outputs contain a competitor's brand name in a bad light. Small number: what's your call? *(severity × virality beats frequency; this is screenshot-fuel: hotfix via output filter + prompt patch, add eval class, comms readiness)*

## Tier 5: Estimation with AI twists ⚪

26. Estimate the daily token volume of a ChatGPT-scale assistant. *(users → sessions → turns → tokens/turn; the structure is the answer)*
27. Estimate how many human support agents a mid-size airline needs, then estimate the ceiling an AI assistant could take. *(volume × AHT ÷ agent capacity; then segment by automatable intent share and cap it honestly, not 100%, per every case study in this repo)*
28. Estimate the annual inference budget for adding AI summaries to every email for 100M users, and then say whether you'd build it. *(the punchline: naive per-email generation is ruinous; the PM answer is triggers, caching, and on-demand design)*

---

## The three habits this file drills

1. **Layer before you answer**: "at the model layer... at the product layer... at the business layer..." Instant structure, zero framework-recital smell.
2. **Every efficiency metric gets a quality guardrail** (and you can cite Klarna's Feb-2024 → May-2025 arc in one clause).
3. **Segment before diagnosing**: language, tenant, intent, cohort, difficulty. Global averages hide every interesting problem.

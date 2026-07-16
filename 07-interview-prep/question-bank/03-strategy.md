# ♟️ Question Bank: AI Strategy & Business

> Senior loops live here. Use the [WHERE-TO-PLAY flow](../answer-frameworks.md); ammunition in [ai-product-strategy.md](../../03-product-craft/ai-product-strategy.md) and [case studies](../../06-case-studies/). 🔵 = reported/sourced · ⚪ = practice.

---

## Tier 1: Reported 🔵

1. "You have invented a memory machine that produces video, image, smell, and sound. Go to market." *(OpenAI; GTM under radical ambiguity: pick a beachhead user, price the scarcity, sequence the market)*
2. "How would you prioritize between making GPT-4 cheaper or investing in GPT-5?" *(coach-compiled; frame: existing-market margin/adoption expansion vs. capability frontier/new markets, then take a side using where value is bottlenecked today)*
3. "How would you measure success for OpenAI? What if instrumentation went down?" *(PM Accelerator's OpenAI list; company-level metric tree, then judgment-under-blindness: leading proxies, qualitative signals, finance data)*
4. "What would be a novel product or business in the self-driving car space?" *(Perplexity)*
5. "How do you partner effectively with sales?" *(OpenAI GTM round; B2B AI: sales feeds the failure/objection loop back into evals and roadmap)*

## Tier 2: Platform risk & moats ⚪

6. You're the CEO of a startup whose product improves LLM outputs for legal briefs. OpenAI announces a legal-focused model. Respond.
7. "Isn't your product just a GPT wrapper?" Answer it for a company of your choice. *(the [defensibility table](../../03-product-craft/ai-product-strategy.md))*
8. Which businesses get *stronger* when models get 10× better, and which die? Give two of each and the underlying principle.
9. Should Salesforce build its own foundation model? Argue both sides, then decide. *(build-vs-buy at enterprise scale; rent intelligence, own workflow/data/evals is the likely landing)*
10. Your company has a 10-year-old rules-based fraud product with 200 enterprise customers. A GenAI-native competitor just raised $50M. War-game it.
11. Pick a vertical (legal, healthcare, construction). Where in that vertical's value chain should an AI startup enter first, and why?

## Tier 3: Monetization & unit economics ⚪

12. Your AI feature costs $4/user/month to serve inside a $15/user product. Walk your options and pick. *(levers in order: caching/routing/trimming → usage caps/tiers → repackaging; the [worked math](../../02-technical-depth/model-selection-and-cost.md))*
13. Seat-based, usage-based, or outcome-based pricing for an AI support agent: choose and defend. *(the [pricing table](../../05-domains/enterprise-saas.md); outcome pricing's attribution problem deserves a mention)*
14. Notion moved AI from a $10 add-on to bundled-in-Business-tier (2025, real case). Steelman both the original and the new choice. When is each right? *([case facts](../../06-case-studies/README.md))*
15. A free consumer AI app hits 10M users and a $2M/month inference bill. You have 6 months of runway. Go.
16. Estimate the market size for AI coding assistants. Structure > numbers. *(then sanity-check against the one verified anchor: ~4.7M paid Copilot subs, Jan 2026)*

## Tier 4: Company strategy cases ⚪

17. You're Google. ChatGPT-style answers cannibalize search ads. Sketch the strategic options and pick a path. *(the innovator's-dilemma classic of this era)*
18. You're Adobe. Generative AI threatens and empowers your creative-suite base simultaneously. Strategy? *(the real answer they chose, commercially-safe training data as differentiation, is worth knowing: [Firefly case](../../06-case-studies/README.md))*
19. You're an Indian SaaS company (pick one). How does the AI wave change your global competitive position?
20. You're Apple. You've been called "behind on AI." Do you agree? What's the strategy that fits Apple's actual strengths? *(on-device/small-model privacy angle vs. frontier-chasing)*
21. Advise a 200-person B2B company: the board demands an "AI strategy" in 90 days. What do you actually deliver? *(portfolio: 2 quick workflow wins + 1 differentiating bet + governance/eval infrastructure, not a chatbot for everything)*
22. Your enterprise customers are building internal AI teams. Does that make your AI product more or less valuable? Reason it out.

## Tier 5: Market judgment ⚪

23. Which current AI product category is most overhyped, and which most underhyped? Commit and defend. *(tests calibrated conviction; any well-argued answer works)*
24. If inference costs fell 100× tomorrow, what products become viable that aren't today? *(always-on ambient AI, per-user fine-tuned experiences, agent swarms on low-value tasks...)*
25. Where does the *application layer's* margin settle long-term if models commoditize, and what does that imply for where you'd want to build your career? *(closes the loop to [strategy §1](../../03-product-craft/ai-product-strategy.md))*

---

## Answer key: Q6 worked (platform-risk classic)

Strong shape: ① **Don't panic-pivot on a press release.** Assess actual capability overlap with *our* evals: run the new model on our golden set; often the announcement covers 60% of the easy cases and none of the workflow. ② **Inventory the durable layers**: our lawyer-workflow integrations, firm-specific fine-tuning/context, citation-verification against real case law, compliance posture, existing distribution into firms. ③ **Reposition**: adopt their model as an engine (we get better, free), double down on the layers they won't build (matter management integration, firm knowledge, defensibility artifacts for malpractice insurers). ④ **Time-box the bet**: 2 quarters of retention/win-rate data against the new alternative; leading indicators defined now. ⑤ **The honest branch**: if our value *was* just output-polish, say so, and either find the workflow moat fast or return capital. Fence-sitting is the only failing answer.

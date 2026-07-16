# 🤖 Question Bank — AI Technical & Feasibility

> The round that separates "interested in AI" from "AI PM." Use the [EXPLAIN framework](../answer-frameworks.md); answers live in [01-foundations](../../01-foundations/) and [02-technical-depth](../../02-technical-depth/). 🔵 = reported/sourced · ⚪ = practice.

---

## Tier 1 — Reported 🔵

1. "Tell me what you know about DPO (Direct Preference Optimization)." *(cross-company, via IGotAnOffer's AI PM guide — the bar: preference tuning without full RL machinery; a cheaper RLHF alternative. If you can place it in the [three-stage pipeline](../../01-foundations/llm-fundamentals.md), you pass)*
2. "When would you use rule-based infrastructure vs. neural networks vs. LLMs?" *(the [decision tree](../../01-foundations/ml-fundamentals.md) — rules for knowable logic, classic ML for structured prediction at scale, LLMs for language/unstructured/generation; cost & auditability as tiebreakers)*
3. "Explain embeddings to a product designer on your team." *(coach-compiled; meaning→coordinates analogy, similar things nearby, powers semantic search/recs)*
4. "You have a model with 10x the capability at 10x the cost. What do you do with it?" *(OpenAI execution round — segment use cases by value density; route; price the premium tier; the answer is a portfolio, not a binary)*
5. "Your chatbot's response quality dropped 15% last week. How do you debug this?" *(coach-compiled; worked answer in [evals §6](../../02-technical-depth/evals.md))*
6. "Would you rather have 90% accuracy on 100 use cases or 99% accuracy on 10 use cases?" *(coach-compiled; stakes-and-strategy reasoning — [evals §6](../../02-technical-depth/evals.md))*
7. "What guardrail metrics would you track?" *(Perplexity; pick a feature and name 3–4: hallucination/faithfulness rate, refusal correctness, latency p95, safety violation rate, cost/query)*
8. "How would you balance product velocity with safety constraints?" *(OpenAI; concrete mechanisms beat philosophy: risk-tiered launch gates, eval bars scaled to stakes, canary rollouts, red-team budgets — "we go fast where errors are cheap and slow where they aren't")*

## Tier 2 — Explain-it questions ⚪ (2 minutes each, out loud)

9. Explain to a CEO why the model sometimes "makes things up" — and what you can and can't do about it.
10. Explain tokens and why our AI feature's cost scales with document length.
11. Explain the difference between RAG and fine-tuning to an engineer who insists we fine-tune. *(the [ladder](../../02-technical-depth/fine-tuning.md))*
12. Explain what an eval is to a designer, and why their rubric opinions matter to it.
13. Explain "context window" and why pasting our entire wiki into every request is a bad plan.
14. Explain what temperature does and when we'd want it at 0.
15. Explain prompt injection to a security-skeptical VP using a concrete scenario. *(borrow the [$1 Tahoe](../../06-case-studies/failures-hall-of-lessons.md))*
16. Explain why the same prompt gives different answers twice, and when that's a feature vs. a bug.
17. Explain what an "agent" is and how it differs from a chatbot — with one example of each from real products.
18. Explain MCP in 60 seconds and why a platform PM should care. *([agents §7](../../02-technical-depth/ai-agents.md))*
19. Explain "reasoning models" and when you'd route a query to one vs. a standard model.
20. Explain why output tokens cost more than input tokens.

## Tier 3 — Architecture & feasibility calls ⚪

21. Legal wants an assistant that answers questions from 10,000 contracts. Prompting, RAG, or fine-tuning? Walk the decision. *(RAG — private/changing data, citations, permissions; [rag.md](../../02-technical-depth/rag.md))*
22. Support wants the bot to "sound like us." Same three options — walk it. *(prompt+examples first; fine-tune only if volume justifies)*
23. Our RAG assistant cites the right document but answers wrong. Diagnose. *(generation-side: grounding instructions, chunk boundaries, model tier — [rag self-test](../../02-technical-depth/rag.md))*
24. Eng says the AI feature needs 8 seconds; design says 2 max. Resolve it. *(streaming + progressive UI for perceived latency; smaller model/shorter context/caching for real latency; or redesign the moment — async generation)*
25. When would you choose an open-weight self-hosted model over a frontier API? Give two concrete scenarios. *([model-selection §3](../../02-technical-depth/model-selection-and-cost.md))*
26. A vendor demos 95% accuracy on their benchmark. What do you ask before believing it applies to us? *(whose data, what distribution, sliced how, vs. what baseline — then run OUR golden set)*
27. Estimate the monthly inference cost of an AI summary feature for 1M weekly active users. Make your assumptions explicit. *(the [worked math pattern](../../02-technical-depth/model-selection-and-cost.md) — interviewers score the structure, not the exact number)*
28. The team wants to auto-upgrade to every new model version. What process do you require? *(pin versions; re-run golden set + regression gates; canary; then adopt — "free upgrades" silently reshuffle failure modes)*
29. Design the fallback chain for an AI feature during a model-provider outage. *(cached responses → smaller backup model/second provider → graceful non-AI path — never a dead spinner)*
30. Multimodal input (screenshots of error messages) for a support bot: what does it change in your pipeline, evals, and cost model?

## Tier 4 — Evals & quality ⚪ (the differentiator tier)

31. Write a 5-dimension rubric for an AI meeting summarizer. Which dimensions get code checks vs. LLM-judge? *([evals drill 3](../../02-technical-depth/evals.md))*
32. How would you build the golden set for an AI email drafter with zero usage data (pre-launch)? *(internal dogfooding, design-partner data, synthetic-but-reviewed edge cases — and a plan to replace synthetic with real within 30 days)*
33. Your LLM-judge scores 4.6/5 but users churn. Three hypotheses and your investigation order. *([evals self-test](../../02-technical-depth/evals.md))*
34. Define "hallucination rate" operationally for a RAG product — what exactly gets counted, by what grader? *(unsupported-claim rate against retrieved context, judge-graded with human calibration; distinguish ungrounded-but-true from false)*
35. How do you evaluate an agent differently from a chatbot? *(outcome/task success vs. transcript quality; efficiency budgets; safety metrics like unauthorized-action attempts — [agents §5](../../02-technical-depth/ai-agents.md))*
36. The eval suite passes but a customer posts a screenshot of an embarrassing failure. Walk your response end-to-end. *(triage severity → reproduce → is it in-distribution for our evals? → add case class, not just the case → fix → comms; the meta-answer: eval coverage is a living map of known failure modes)*
37. How would you red-team a children's homework-help product before launch? *(adversarial personas: cheating extraction, unsafe topics, PII elicitation, jailbreak attempts; expert review; staged exposure — [edtech](../../05-domains/edtech.md) + [responsible-ai](../../03-product-craft/responsible-ai.md))*
38. What's your minimum quality bar to ship, and how do you defend it when sales wants to ship now? *(a number on a named golden set per severity tier; show the cost of shipping under it with a failure case — then negotiate scope, not the bar)*

## Tier 5 — Rapid-fire vocabulary checks ⚪

Be able to define in one sentence each, cold: hallucination · grounding · few-shot · chain-of-thought · RLHF · distillation · quantization · vector database · reranker · structured output · streaming · TTFT · prompt caching · router · canary rollout · shadow mode · drift · golden set · LLM-as-judge · red-teaming. *(All in the [glossary](../../01-foundations/glossary.md). If any took more than a beat, that's tonight's flashcards.)*

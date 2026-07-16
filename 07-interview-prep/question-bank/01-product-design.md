# 🎨 Question Bank — AI Product Design & Product Sense

> Use the [DESIGN-AI flow](../answer-frameworks.md). 🔵 = reported for a named company (sourced, July 2026) · ⚪ = practice, written for this repo. Work top to bottom within a tier; don't skip the classics — AI loops still ask them.

---

## Tier 1 — Reported questions (drill these first)

### OpenAI 🔵
1. "You have invented a memory machine that produces video, image, smell, and sound. Go to market." *(product sense; deliberately surreal — structure under ambiguity is the test)*
2. "How would you improve ChatGPT for enterprise users?"
3. "Imagine you're leading the team for the ChatGPT 6 rollout. How would you launch it?"
4. "Design a solution to communicate with pets using AI." *(via PM Accelerator's OpenAI list)*
5. "Analyze a current OpenAI product and propose three improvements to enhance user engagement."
6. "Design safeguards for an AI system that can take actions on behalf of a user." *(design × safety hybrid — use the [autonomy dial](../../02-technical-depth/ai-agents.md))*

### Anthropic 🔵
7. "How would you approach safety in a consumer AI product?"
8. "How would you handle a Claude feature producing confident but incorrect answers?" *(design the trust/failure UX + eval story — [worked answer](../mock-scenarios.md))*
9. "Define success metrics for a new Claude feature that balances user value and risk reduction." *(design-metrics hybrid)*

### Meta 🔵 (incl. the "Product Sense with AI" round)
10. "Create a tool to connect volunteers with opportunities." *(AI round — includes live prototyping)*
11. "Design a map application for Meta." *(AI round)*
12. "Design a parking solution for Google Maps." *(classic product sense — still asked)*
13. "You're the PM for Facebook notifications on mobile. Why would Meta build this, and how would you measure success?"

### Microsoft AI 🔵
14. "How would you prioritize new features for an AI writing assistant inside Microsoft Word?"
15. "Do you have a favorite AI tool? Why, and how would you make it better?"

### Perplexity 🔵
16. "Propose a new feature for Perplexity."
17. "What would be a novel product or business in the self-driving car space?"

### Coach-compiled (not company-attributed) 🔵
18. "Redesign Gmail's composer to incorporate an AI writing assistant."

## Tier 2 — Practice: AI features in known products ⚪

19. Design an AI feature for Spotify that increases podcast listening.
20. Add an AI capability to Google Calendar that saves knowledge workers 2+ hours/week.
21. Design an AI shopping assistant for Amazon that reduces returns.
22. WhatsApp wants an AI feature for small-business owners in India. Design it.
23. Design an AI feature for LinkedIn that improves job-search outcomes without flooding recruiters with AI-written spam. *(the second clause is the question)*
24. Add AI to YouTube that helps creators, not just viewers.
25. Design an AI-powered feature for Uber that improves driver earnings.
26. Notion wants to leapfrog on AI for students specifically. What do you build?
27. Design an AI feature for Zoom that makes meetings *shorter*.
28. Instagram wants AI to help users manage their digital wellbeing. Design it — and address the incentive conflict. *(engagement vs. wellbeing — [consumer domain](../../05-domains/consumer-social.md))*

## Tier 3 — Practice: new products & agents ⚪

29. Design an AI tutor for learning to cook, for beginners living alone.
30. Design an AI agent that handles routine scheduling for a 10-person sales team — specify tools, permissions, and approval gates. *(agent design — [framework](../../02-technical-depth/ai-agents.md))*
31. Design an AI product for elderly users living independently. *(error stakes + trust UX for a vulnerable population)*
32. Build an AI product for farmers in emerging markets with intermittent connectivity. *(edge/offline constraints, local language, low-literacy UX)*
33. Design an AI research assistant for PhD students. What do you explicitly NOT automate?
34. A hospital asks for an AI product to reduce nurse burnout. Design it. *(pick the non-diagnostic wedge — [healthcare](../../05-domains/healthcare.md))*
35. Design an AI-powered personal finance coach — and walk the advice/insight regulatory line. *([fintech](../../05-domains/fintech.md))*
36. Design an AI feature for a dating app that improves match quality without writing people's messages for them. *(authenticity boundary)*
37. Design an AI agent for e-commerce customer refunds. *(worked skeleton in [ai-agents §8](../../02-technical-depth/ai-agents.md))*
38. Design an AI notetaker for doctors — then explain what changes if it also *suggests diagnoses*. *(the SaMD line — [healthcare](../../05-domains/healthcare.md))*

## Tier 4 — Practice: critique & improve ⚪

39. Pick an AI feature you think is badly done. Diagnose why and fix it. *(have one ready — this doubles as the Microsoft "favorite tool" question inverted)*
40. ChatGPT/Claude/Gemini — pick one, identify its biggest UX debt, propose the fix and the metric.
41. AI overviews in search engines: critique the product from the publisher's, user's, and search company's perspective — then make a call.
42. Your company's 2-year-old AI chatbot has 8% weekly usage. Kill, fix, or pivot? Structure the decision.

---

## Answer keys — three questions worked at "strong hire" depth

**Q8 (Anthropic — confident-but-wrong Claude feature):** full worked answer in [mock-scenarios.md](../mock-scenarios.md).

**Q14 (Microsoft — prioritize AI features for Word):** Strong answers ① segment users (students/knowledge workers/enterprise — pick enterprise: Word's revenue center) ② inventory candidate features by *job*: draft (creation), rewrite (editing), summarize (comprehension), format (compliance) ③ prioritize with explicit criteria: value frequency × quality achievable today × differentiation vs. generic chat — argue *rewrite/editing* beats *drafting* (higher frequency in enterprise, lower hallucination stakes since the user's own content grounds it, plays to Word's install base) ④ name the eval bar per feature and the trust UX (tracked changes = the perfect AI-edit interface — diffs are native) ⑤ metrics: feature adoption within docs, edit-acceptance rate, doc-completion time; guardrail: formatting/factual error reports. The differentiator: noticing Word already owns the *review* paradigm (comments, tracked changes) — AI should inhabit it, not bolt a chatbot onto the side.

**Q30 (scheduling agent):** Strong answers specify — tools: calendar read (all), calendar write (own team only), email send (draft-and-approve first month), CRM read; permissions: no external commitments above 30-min meetings without approval; approval gates: new-contact outreach, rescheduling exec meetings; failure design: ambiguous requests → clarify, conflicts → propose options never auto-resolve; evals: 200 replayed scheduling threads, success = correct slot + tone + no double-bookings; metrics: scheduling latency, human touches per booking, override rate (the autonomy-earning signal); risks: prompt injection via inbound email ("reschedule everything to next year") → treat email as untrusted data, act only on structured intents. This is [ai-agents.md](../../02-technical-depth/ai-agents.md) applied — if your answer didn't include untrusted-input handling, reread §4.

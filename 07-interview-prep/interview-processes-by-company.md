# 🏢 Interview Processes by Company: What's Documented

> Compiled from company career pages, [Exponent](https://tryexponent.com)/[IGotAnOffer](https://igotanoffer.com/en/advice/ai-product-manager-interview) guides, Glassdoor aggregates, and candidate write-ups; **verified July 2026**. Processes change, so treat this as the shape and confirm specifics with your recruiter. ⚠️ = single-source or conflicting reports.

---

## OpenAI

**Shape:** 5 stages, up to ~12 conversations, typically 6-10 weeks.
Recruiter screen → hiring manager (two-part) → **product sense screen** (~60 min; deliberately ambiguous one-sentence prompts) → **product execution screen** (metrics-heavy, tied to real OpenAI product problems) → final loop of 4-6 rounds: product sense, execution, go-to-market, engineering collaboration, stakeholder management, behavioral.

**Distinctives:** interviewer LinkedIn profiles shared in advance; candid early leveling conversations. Sample reported questions (see [question bank](question-bank/) for the full sourced set): *"You have a model with 10x the capability at 10x the cost. What do you do with it?"*, *"How would you improve ChatGPT for enterprise users?"*, *"Design safeguards for an AI system that takes actions on behalf of users."*

**Prep emphasis:** ambiguity tolerance (prompts are intentionally underspecified, so structure them aloud), model economics fluency, safety-velocity tradeoffs, and knowing OpenAI's actual product surface (API, ChatGPT tiers, enterprise) well enough to critique it.

## Anthropic

**Shape:** ~5 rounds, notably fast (Glassdoor average ~19 days across 130+ reports).
Recruiter screen → hiring manager → product/business case → cross-functional panel (PM/TPM/eng/design) → **culture & values interview, widely reported as the real bar.**

**Distinctives:** safety judgment and mission alignment probed *throughout*, not quarantined in one round. Reported culture-round questions: *"What are some unusual beliefs you hold, and how have you defended them?"*, *"What concerns do you have with Anthropic's direction?"*, *"Tell me about a time you did something that conflicted with your values."* Case rounds lean into value-vs-risk metric design: *"Define success metrics for a new Claude feature balancing user value and risk reduction."*

**Prep emphasis:** genuine, non-performative engagement with AI safety (read Anthropic's published thinking; have real opinions including disagreements); intellectual honesty under pushback; the helpfulness↔harmlessness tension held with nuance.

## Google (incl. DeepMind PM roles)

**Shape:** 1-2 screens → ~5-round virtual onsite: product design, product strategy, analytical, technical discussion (architecture/API/latency, no coding), "Googleyness & leadership." Many applicants also report a ~30-min timed **Google Hiring Assessment** (situational judgment) early in the funnel. Typical 4-6 weeks. ⚠️ One 2026 guide claims the standalone technical round was dropped while other guides still list it, so ask your recruiter.

**Distinctives:** hiring-committee model (your packet, not just your interviews, gets judged); AI PM roles concentrated in Gemini/DeepMind/Cloud orgs; DeepMind posts list base ranges (e.g., $183K-$271K for a Responsibility PM role, 2026).

**Prep emphasis:** classic structured product design at high polish; analytical rigor (metric decomposition); for DeepMind, responsibility/safety framing on top.

## Meta

**Shape:** recruiter screen → 2 phone screens (product sense + analytical/execution) → loop: product sense, analytical thinking, leadership & drive, **plus, for AI-track candidates: "Product Sense with AI"** (mainly IC6/M1/M2 levels).

**The AI round (first PM-loop change in 5+ years):** 60 minutes, roughly half traditional product sense discussion, half **live prototyping with Meta's internal Llama-based vibe-coding tool**. Evaluated on "**the human delta**", meaning what you add beyond the tool: catching hallucinations, rejecting generic outputs, steering toward user value. Reported prompts: *"Create a tool to connect volunteers with opportunities"*, *"Design a map application for Meta."*

**Prep emphasis:** practice building with an AI app-builder under 30-minute time pressure ([projects.md](../04-build-with-ai/projects.md) Project 3 is direct prep); classic Meta product-sense structure still applies to the discussion half; narrate your judgment while prototyping, because the judgment is what's scored.

## Amazon / AWS

**Shape:** phone screen → ~5-interview loop where **every round maps to specific Leadership Principles**; STAR-format behavioral throughout; includes the **Bar Raiser** (trained interviewer from outside the team with veto power who leads the debrief). AI PM roles commonly titled "Product Manager - Technical, GenAI/AI-ML."

**Prep emphasis:** 8-10 STAR stories pre-mapped to LPs (Customer Obsession, Think Big, Dive Deep, Invent & Simplify, Are Right A Lot...), each with quantified outcomes; writing culture (some loops include a written exercise); for AI roles, expect Dive Deep to go technical on your AI claims.

## Microsoft (incl. Microsoft AI / Copilot orgs)

**Shape:** 3 stages over 4-8 weeks: recruiter screen (~30 min) → hiring manager (~30 min, behavioral-leaning) → virtual onsite loop of 4-6 interviews (45-60 min each): product design, execution, behavioral. **AI PM roles are notably more technical**, so expect LLM evaluation, tradeoff, and production-AI questions (dedicated Exponent guide exists for the Microsoft AI PM loop). Reported questions: *"How would you prioritize new features for an AI writing assistant inside Word?"*, *"Do you have a favorite AI tool? How would you make it better?"*

**Prep emphasis:** Copilot ecosystem fluency (M365, GitHub, Azure AI Foundry); growth-mindset framing in behaviorals; eval/quality discussion readiness.

## Perplexity

**Shape:** ~7 conversations across 3 stages, fast (1-4 weeks): recruiter → product sense case → 5-round onsite (product thinking/strategy, analytical, engineering behavioral, engineering execution, design thinking). Also runs an APM program. Reported questions: *"Propose a new feature for Perplexity"*, *"What guardrail metrics would you track?"*

## Mistral AI

**Shape (reported):** ~4 rounds: recruiter screen, hiring manager, product case. European frontier-lab option; PM roles verified (e.g., "PM, AI Assistant").

---

## Cross-company patterns worth internalizing

1. **Every loop now has an AI-judgment surface**: a dedicated round (Meta, Microsoft AI) or woven through (OpenAI, Anthropic). Prepping "regular PM + separate AI facts" misses how integrated it's become.
2. **Analytical rounds shifted toward conflicting-metric tradeoffs** (e.g., "north star for Reels, and what do you sacrifice if you prioritize it over Stories?"). Practice metric *conflicts*, not just metric *selection* ([metrics](../03-product-craft/metrics-for-ai-products.md)).
3. **Mission fit is screened for real** at frontier labs. Anthropic's values round and OpenAI's "why here, why AI" filtering reward genuine engagement and punish rehearsed enthusiasm.
4. **Levels drive loops**: senior/principal loops add strategy + org-design rounds; the AI-prototyping rounds currently concentrate at mid-senior IC levels.

*Sources: Exponent company guides (OpenAI, Anthropic, Meta, Microsoft AI, Perplexity, Mistral; fetched/verified), IGotAnOffer guides, [openai.com/interview-guide](https://openai.com/interview-guide), Glassdoor aggregates, [Lenny's Newsletter](https://www.lennysnewsletter.com/) (Meta AI round), Prepfully, candidate write-ups. Verified July 2026.*

# 🎭 Mock Scenarios: Three Full Interviews, Worked

> Read the question, answer out loud yourself FIRST (timed), then compare. The commentary boxes explain *why* each move scores. These are composite scenarios built around genuinely reported questions.

---

## Mock 1: AI Product Design (25 min)
### "How would you handle a Claude-style assistant feature producing confident but incorrect answers?" *(reported Anthropic-style case)*

**[0:00-2:00] Scoping.**
"Let me make sure I'm solving the right problem. I'll assume this is a general assistant feature with both consumer and work usage, and 'confident but incorrect' means fluent, plausible, wrong: the classic hallucination failure, which users can't easily distinguish from correct output. I'd like to cover: framing the real risk, mitigations across the stack, and how we'd measure progress. The goal I'll optimize for: **maintain user trust and safety while keeping the assistant useful**, because the naive fix, refusing more, has its own cost."

> 💬 *Why this scores: restates the problem in technical terms (shows fluency), names the hidden tradeoff (over-refusal) before designing, announces a plan.*

**[2:00-5:00] Structure the problem.**
"Wrongness isn't uniform, so I'd segment by **stakes and verifiability**: (a) casual/creative queries, where errors are cheap; (b) factual reference queries, where errors damage trust and are mostly verifiable; (c) consequential advice (medical, legal, financial), where errors are harmful and hard for users to verify. The product response should differ per segment; a single global fix would either under-protect (c) or lobotomize (a)."

**[5:00-15:00] Mitigations across four layers.**
1. **Grounding**: for factual/consequential queries, retrieve before answering (search/RAG) and **cite sources**, which shifts the user from *believing* to *verifying*. Uncited claims in grounded modes get flagged by the system itself.
2. **Calibian UX** *(catches self)*, **calibrated UX**: confidence-differentiated presentation. Assertive tone only when grounded; hedged framing + "here's what to check" for uncertain answers; refusal-with-alternatives at the bottom ("I'm not certain, here are authoritative sources"). The Air Canada tribunal case is exactly what uniform confidence costs a company.
3. **Behavioral training/prompting**: instruct and tune toward expressing uncertainty and asking clarifying questions rather than guessing; measured, because sycophancy pulls the other way.
4. **Stakes-based guardrails**: category (c) gets templated safety framing, disclaimers that *do* something (structured "see a professional" pathways), and higher refusal thresholds.

> 💬 *The self-correction is fine; interviewers score recovery, not perfection. Note each mitigation names a mechanism, not a vibe.*

**[15:00-21:00] Measurement.**
"Offline: a **hallucination eval** built from a golden set of prompts with verifiable answers per segment; grade unsupported-claim rate with an LLM judge calibrated to human raters; slice by segment and language; regression-gate every model/prompt change. Online: citation click-through, correction/report rate, 'the assistant was wrong' complaint tickets, and **follow-through harm proxies** for category (c). Counter-metric: **over-refusal rate**, helpfulness on a benign-hard set, because I can trivially hit zero hallucinations by refusing everything."

**[21:00-25:00] Risks + close.**
"Residual risks: users over-trusting cited answers (citations can be misread, so we spot-check faithfulness, not just presence); latency cost of retrieval (route: only ground when the query type needs it). If I had to pick one thing first: **the eval**. You can't manage what you can't measure, and it converts this from philosophy into engineering. Summary: segment by stakes, ground the verifiable, calibrate the presentation, gate the consequential, and measure both hallucination *and* over-refusal."

---

## Mock 2: Execution (25 min)
### "You have a model with 10x the capability at 10x the cost. What do you do with it?" *(reported OpenAI execution question)*

**Strong-answer skeleton:**

**Clarify (1 min):** "10x capability on what axis: reasoning depth, reliability, breadth? I'll assume a general frontier jump with 10x per-token cost. Product context: I'll take an assistant platform with consumer tiers and an API."

**Frame (2 min):** "Cost changes *where* it's viable, not *whether* it's valuable. My job is matching the capability to use cases whose value density supports the price. This is a routing and packaging problem, not a binary launch decision."

**The portfolio (12 min):**
1. **Segment by value density**: consequential work tasks (code architecture, contract analysis, research synthesis) absorb 10x cost trivially. A $2 query replaces an hour of expert time. Casual chat can't. So: **don't make it the default model**; make it a routed/selectable tier.
2. **Product mechanisms**: premium tier ("deep reasoning mode") with explicit invocation; **hybrid cascades**, where a cheap model drafts and the expensive model verifies/upgrades the hard 10%; async "deep work" products (long-running jobs) where latency tolerance is high and willingness-to-pay is proven.
3. **API packaging**: expose it with cost transparency; let builders route; expect the ecosystem to find value pockets we won't predict.
4. **Margin math out loud**: if 5% of queries route up at 10x cost, blended cost rises ~1.45x while perceived product ceiling rises to frontier; the routing ratio is the business model.
5. **Sequencing**: start API + top-tier subscribers (self-selecting high-value users), watch usage-per-dollar and task types, then productize the discovered pockets downward as costs fall. "Capability tiers always get cheaper; design the ladder for the price cut you know is coming."

**Metrics (3 min):** adoption within eligible tiers, per-query value proxies (task completion, retention of routed users), blended cost/margin, and cannibalization watch (are users who don't need it burning it?).

> 💬 *What separates this from a mediocre answer: refusing the "launch it or not" frame, the explicit routing math, and pricing the future ("the 10x cost will halve, so plan the ladder"). Weak answers debate whether 10x capability is 'worth it' in the abstract.*

---

## Mock 3: The live prototyping round (Meta-style, 60 min: 30 discussion + 30 build)
### "Create a tool to connect volunteers with opportunities." *(reported Meta AI-round prompt)*

**Discussion half, compressed strong path:** users (volunteers: episodic vs. committed; orgs: chronically understaffed at coordination) → the real pain is **matching + follow-through**, not discovery (plenty of listings exist; no-show rates are the orgs' actual complaint) → design: profile-light onboarding (skills, availability windows, causes), **AI matching on fit + logistics feasibility** (commute, schedule), and (the differentiated bit) **commitment scaffolding**: reminders, micro-confirmations, post-event impact recap (the retention loop) → metrics: completed volunteer-hours (north star), show-rate, repeat-rate within 60 days; guardrail: org-side listing quality.

**Build half, how to run it (this is what's scored):**
- Prompt the tool for the core loop first: *"Build a two-sided volunteer matching app: volunteer onboarding (3 fields), a match feed with 'why this fits you' explanations, one-tap signup with calendar confirmation."* Ship the walking skeleton; iterate.
- **Narrate judgment continuously**: "It generated a 12-field signup form. That's onboarding friction death; cutting to 3." · "It hallucinated a review-stars feature for volunteers: wrong dynamic for this domain, removing." · "The match feed shows distance but not schedule fit. That was our core insight; fixing."
- Timebox: skeleton by minute 10, one polish pass on the match-explanation UI (your differentiator), stop building 5 minutes early to demo the flow against the user story.
- Close by connecting: "The prototype validates the 3-field onboarding and the why-this-match explanation; next I'd test commitment scaffolding, which a static prototype can't prove."

> 💬 *Scored dimension is "the human delta": every generated artifact you accepted, rejected, or corrected (with a user-anchored reason) is a point. A prettier app with silent building loses to an uglier app with loud judgment.*

---

## Drill protocol

Round-robin these three formats with a peer weekly. Interviewer role: probe one assumption hard mid-answer ("would that metric survive a 10x traffic spike?"). Recovering from probes is the most transferable interview muscle. Then swap.

# 🎓 AI PM in EdTech: Personalization Meets Pedagogy

> **TL;DR:** Education is AI's most natural fit on paper (infinite patient tutoring, per-learner adaptation) and its most delicate in practice: the user is often a minor, the buyer is a school or parent, "engagement" can conflict with *learning*, and the cheating question hangs over everything. The PM craft is optimizing for outcomes you can only measure slowly, with data you must handle gently.

---

## 1. The AI surface area

| Use case | Real anchors (verified) | Notes |
|---|---|---|
| **Adaptive practice**: difficulty/spacing per learner | Duolingo's **Birdbrain** (predicts per-exercise success, updates after every exercise; the craft benchmark) | Invisible AI; a decade of compounding data advantage |
| **AI tutors / explainers** | Khan Academy's Khanmigo (GPT-4-era flagship); **Duolingo Max** (Roleplay + Explain My Answer, launched with GPT-4, Mar 2023) | Socratic guidance vs. answer-giving is a *product* stance |
| **Teacher copilots**: lesson plans, grading assist, differentiation | The quiet high-adoption category | Teacher-in-loop = survivable errors + labor win |
| **Language practice** | Duolingo Roleplay; conversation partners | Speech + patience = genuine AI advantage |
| **Assessment & feedback** | Essay feedback, auto-grading with rubrics | High-stakes grading needs human sign-off; feedback ≠ grades |
| **Institutional analytics** | Early-warning dropout models | Fairness landmines: flagging students by demographic proxies |

## 2. The tensions unique to education

- **Engagement ≠ learning.** Streaks and gamification can optimize *time in app* while learning stalls; the honest north star is demonstrated outcomes (mastery progression, retention of skill), which is slow and confounded. Strong candidates name this tension unprompted and propose learning-outcome guardrails on every engagement metric.
- **The answer-giving dilemma.** A tutor that just gives answers maximizes short-term satisfaction and destroys learning value; Socratic scaffolding ("what have you tried?") is pedagogically right and retention-risky. This is a *quality-bar* decision to encode in prompts and evals ([prompting](../02-technical-depth/prompt-engineering.md)): explain-don't-solve modes, hint ladders.
- **Cheating vs. learning-tool duality.** The same capability is homework-help or academic dishonesty by context. Product levers: process visibility for teachers, drafts-with-history, integrity modes, and honesty that detection tools are unreliable (false-accusation harm is real).
- **Hallucination hurts differently here**: a confidently wrong explanation *teaches the error*. Grounding on vetted curriculum + accuracy evals per subject; math needs verified computation paths.

## 3. The regulatory & trust stack

| Regime | What it means for product |
|---|---|
| **COPPA** (US, under-13) | Verifiable parental consent, data minimization; design for it from day one |
| **FERPA** (US student records) | School-controlled data; vendor obligations flow through district contracts |
| **State student-privacy laws + district AI policies** | Procurement checklists; district IT is a gatekeeper buyer |
| **EU AI Act** | Education is an Annex III **high-risk** area (admission, assessment, proctoring decisions). Obligations timeline now Dec 2027; emotion inference in education is *banned* (since Feb 2025) |
| **Minors' data globally** | GDPR-K, India DPDP (children's provisions): consent architecture is product architecture |

Buyer map: **student (user) ≠ teacher (gatekeeper) ≠ district/parent (buyer/consent-holder)**. Every feature needs a story for all three, and the teacher's workload is usually the adoption bottleneck.

## 4. Interview drill

**"Design an AI study buddy for high-school students."** Strong path: user & job (homework help across subjects; the real job = *get unstuck without being handed answers*) → pedagogy stance up front: hint-ladder Socratic mode, full-solution only after attempts, process log shareable with teachers (turns the cheating objection into a feature) → grounding: curriculum-aligned content per subject/state; math via computation tools not token prediction → minors' stack: COPPA/parental consent, no behavioral advertising, data minimization, escalation design for self-harm-adjacent disclosures (AI products used by teens *will* receive them, so have the referral path) → quality: per-subject accuracy evals, explanation-quality rubric with teachers as calibrators, "confidently wrong" as the tracked killer metric → metrics: north star = mastery progression on subsequent attempts (did they get the *next* one right alone?); guardrails: over-reliance signal (help-seeking on problems they previously mastered), session-time caps → GTM: teacher/parent transparency dashboards as trust differentiator.

**The Duolingo arc belongs to this domain too:** Birdbrain's invisible personalization → Max's GPT-4 launch-day partnership (premium tier at $29.99/mo) → the 2025 "AI-first" memo backlash. EdTech-specific reading: AI-replacing-humans framing is *especially* toxic where the humans are teachers ([full case](../06-case-studies/duolingo.md)).

## 5. Know these names
Duolingo Birdbrain / Max · Khanmigo (Khan Academy) · Socratic scaffolding · mastery learning & spaced repetition (the learning-science vocabulary) · COPPA/FERPA · EU AI Act education high-risk + emotion-inference ban · Bloom's two-sigma problem (the classic "1:1 tutoring is 2σ better" motivation; cite as aspiration, not proof) · AI-detection unreliability debates.

---
*Related: [consumer-social](consumer-social.md) (engagement mechanics) · [responsible-ai](../03-product-craft/responsible-ai.md) (minors) · [Duolingo case](../06-case-studies/duolingo.md)*

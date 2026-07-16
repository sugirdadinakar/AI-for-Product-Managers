# 📄 The AI PRD: Template + Worked Example

> **TL;DR:** An AI PRD is a normal PRD plus five sections classic PRDs don't have: **quality bar & evals, data, cost & latency budgets, failure UX, and risk/safety.** Copy the template; steal the worked example.

---

## 1. What changes vs. a classic PRD

| Classic PRD says | AI PRD must also say |
|---|---|
| "The feature shall do X" | "...measured by eval Y, shipping at threshold Z, sliced by segment" |
| Acceptance criteria | Golden dataset + rubric + regression gates |
| Edge cases | Failure modes, their UX, and their measured rates |
| - | Data: sources, rights, freshness, flywheel |
| - | Unit economics: cost/action budget, latency budget |
| - | Safety/abuse cases and mitigations |
| Launch plan | Staged rollout gated on eval + live metrics, with kill criteria |

---

## 2. The template (copy from here)

```markdown
# [Feature name]: AI PRD
Owner: · Status: · Last updated: · Reviewers: eng, DS/ML, design, legal/privacy

## 1. Problem & evidence
Who hurts, how often, cost of the pain, evidence (research, tickets, data).
Why now, and why AI (vs. rules/templates/humans): the baseline we must beat.

## 2. Users & jobs
Primary segment(s), the job-to-be-done, where in the workflow this lives.

## 3. Solution overview
UX summary + entry points. Architecture sketch at PM altitude
(prompting / RAG / fine-tune / agent, and why this rung of the ladder).

## 4. Quality bar & evals   ⭐ the section that makes it an AI PRD
- Quality dimensions & rubric (what does "good" mean, per dimension?)
- Golden dataset: source, size, owner, refresh cadence
- Ship bar: e.g. "≥90% rubric pass overall; no segment below 80%; 
  hallucination rate <1% on grounded-facts checks"
- Regression policy: every prompt/model/index change re-runs the suite
- Online measurement: acceptance/edit rate, thumbs, escalations, A/B plan

## 5. Data
- Sources & access; freshness requirements
- Rights & consent: PII handling, customer contractual terms, training-use policy
- Flywheel: what usage data improves the product, and how it flows back

## 6. Budgets
- Cost: ≤ $X per action / ≤ $Y per user/month at P95 usage (show the math)
- Latency: TTFT ≤ Xs, full response ≤ Ys (or async with progress UX)
- Rate limits / abuse caps

## 7. Failure modes & UX
For each mode (wrong answer, no answer, partial, slow, unsafe):
detection → user-facing behavior → recovery path → measured rate target.
Include the refusal path ("I can't do that") and the human escalation path.

## 8. Safety, risk & compliance
Abuse cases (prompt injection, data extraction, harmful content),
fairness considerations, regulatory surface (per domain), review sign-offs.

## 9. Rollout
Shadow mode → internal → X% canary → GA; gates at each step
(eval scores + live metrics); kill criteria & switch; comms plan.

## 10. Success metrics
North star + guardrails (see metrics-for-ai-products.md);
targets at 30/90 days; the dashboard link.

## 11. Open questions & explicitly out of scope
```

---

## 3. Worked example (abridged): "Reply Draft" for a helpdesk product

**Problem.** Agents spend a median 6.5 min/ticket; 60% of tickets are variations of 30 known intents (internal data, Q1). Target: cut handle time on known intents without hurting CSAT. Baseline to beat: canned macros (used in 22% of eligible tickets, low because finding the right macro is slow).

**Solution.** RAG over the KB + past resolved tickets; drafts a reply inside the agent console; agent edits/sends. **Suggest-mode only**, no auto-send (autonomy dial: [agents](../02-technical-depth/ai-agents.md)).

**Quality bar & evals.**
- Golden set: 300 real resolved tickets across the top 30 intents, 3 languages, stratified by difficulty; owner: PM; refreshed monthly from production failures.
- Rubric (LLM-judge, human-calibrated quarterly): factual accuracy vs. KB (code-check citations + judge), policy compliance, completeness, tone (1-5 each).
- Ship bar: ≥ 88% pass; **no intent below 75%**; zero policy-violation outputs in adversarial suite.
- Online: draft acceptance rate (target ≥ 55%), edit distance, per-intent acceptance dashboards.

**Data.** KB articles (owned, refreshed weekly; staleness alert if >90 days); resolved tickets (customer DPA permits internal model use, confirmed w/ legal 5/12); **no customer PII to third-party model: PII scrubber in pipeline** (eng design doc linked). Flywheel: agent edits become preference pairs for future prompt/model improvements.

**Budgets.** ≤ $0.02/draft (2.5k in / 400 out tokens on mid-tier model w/ cached system prompt; math in appendix); ≤ 3s TTFT streamed. At P95 agent volume: ≈ $11/agent/month ≈ 2% of seat price. ✅

**Failure UX.** Low retrieval confidence → show "no good match: here are the 3 closest KB articles" instead of a draft (never guess); model timeout → macro picker fallback; injection attempt detected in ticket text → draft suppressed + flag. Refusals and fallbacks are instrumented, not silent.

**Rollout.** 2 wks shadow (drafts generated, hidden, scored) → 20 internal agents → 10% canary gated on acceptance ≥ 45% & CSAT flat → GA. Kill: CSAT −2pts sustained or policy-violation > 0.1%.

**Metrics.** North star: median handle time on eligible intents (target −25% @ 90 days). Guardrails: CSAT, reopen rate, escalation rate, cost/draft. Counter-metric watched: agent skill atrophy on rare intents (spot-check QA scores).

---

## 4. Review checklist (print this)

- [ ] Is the quality bar a **number on a named dataset**, not an adjective?
- [ ] Does every failure mode have a designed UX and a measured rate?
- [ ] Is there a **refusal/fallback path** and a human escalation?
- [ ] Cost math shown at P95 usage, not average?
- [ ] Data rights confirmed in writing, not assumed?
- [ ] Rollout gates + kill criteria explicit?
- [ ] Would eng, DS, legal, and support each find their questions pre-answered?

---

➡️ **Next:** [UX patterns for AI](ux-patterns-for-ai.md), designing the trust layer this PRD promises.

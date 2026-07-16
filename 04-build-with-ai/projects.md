# 🚀 Five Portfolio Projects — From Zero to "Here's What I Built"

> **TL;DR:** Do these in order. Each adds one core AI PM competency, takes a weekend or less, costs ≈ $0–20, and produces an artifact you can show in an interview. By project 5 you'll have lived every concept in [02-technical-depth](../02-technical-depth/).

**The rule for every project:** write a mini-PRD *before* (problem, users, quality bar) and a retro *after* (what surprised you, what the model couldn't do, what you'd measure next). The documents are the portfolio; the app is just evidence. Host it all in a public GitHub repo or Notion page.

---

## Project 1 — Production-grade prompt + golden set 🎯
**Skill unlocked: prompting & quality thinking · Time: 3–4 hrs · Cost: $0**

Build a system prompt for a realistic feature (support reply drafter, meeting summarizer, job-description writer — pick a domain you know).

1. Write v1 of the system prompt (role, rules, format, refusal path — [prompt-engineering](../02-technical-depth/prompt-engineering.md)).
2. Create a **golden set of 20 real-ish inputs** including 5 nasty edge cases (ambiguous, adversarial, out-of-scope).
3. Run all 20; score with a simple 3-dimension rubric you write.
4. Iterate the prompt twice; keep score history.
5. **Deliverable:** the prompt, the set, the scores across versions, and a half-page "what I learned about where it breaks."

*Interview payoff: "walk me through a prompt you've iterated" — you'll be the only candidate with version-scored evidence.*

## Project 2 — Custom assistant on your own knowledge 📚
**Skill unlocked: RAG intuition · Time: 2–3 hrs · Cost: $0–20/mo (assistant plan)**

Use Claude Projects or a Custom GPT. Upload a real corpus you own (your notes, a public policy doc set, product docs).

1. Configure instructions + upload docs.
2. Interrogate it with 15 questions where **you know the answers** — including 3 whose answers are *not* in the corpus.
3. Log: retrieval hits/misses, hallucinations on the not-in-corpus questions, citation behavior.
4. **Deliverable:** a failure-analysis table — the exact skill of diagnosing retrieval vs. generation errors ([rag.md](../02-technical-depth/rag.md)).

## Project 3 — Working prototype with an AI builder ⚡
**Skill unlocked: feasibility intuition + demo-able artifact · Time: a weekend · Cost: free tiers**

Pick a real pain from your own life/work. Build it in **[Lovable](https://lovable.dev/pricing), [v0](https://v0.app/pricing), [Bolt](https://bolt.new/pricing), or [Replit](https://replit.com/pricing)** (or Claude Artifacts for a single-page interactive).

1. Mini-PRD first: one user, one job, one success metric.
2. Prompt the builder iteratively — notice *how you have to think* to get what you want (this is context engineering, felt).
3. Put it in front of 3 real people; watch them use it.
4. **Deliverable:** live link + the PRD + a "3 things users did that I didn't expect" note.

*This mirrors Meta's live-prototyping interview round — practicing the tool under mild time pressure is direct interview prep.*

## Project 4 — Call the API + build an LLM-as-judge eval 🔬
**Skill unlocked: evals for real + API literacy · Time: a weekend · Cost: <$5 of API credit**

The differentiator project — very few PM candidates have done this.

1. Get an API key ([Google AI Studio](https://ai.google.dev/aistudio) free tier, or OpenAI/Anthropic).
2. Take your Project 1 prompt + golden set. Write (or have AI write you) a ~50-line script that runs all 20 cases through the API.
3. Add a **judge**: a second model call that grades each output against your rubric, returning JSON scores.
4. Calibrate: hand-grade 10 outputs yourself; compare with the judge; fix the rubric where you disagree.
5. Swap models (big vs. small) and compare score/cost/latency — congratulations, you've done model selection with data ([model-selection](../02-technical-depth/model-selection-and-cost.md)).
6. **Deliverable:** the script, a results table (model × quality × cost × latency), and your calibration notes.

## Project 5 — Agent with tools & guardrails 🤖
**Skill unlocked: agent product judgment · Time: a weekend+ · Cost: <$10**

Build a small agent — easiest paths: Claude with [MCP](https://modelcontextprotocol.io) tools / a Custom GPT with Actions / a no-code agent builder (e.g., Zapier agents), or code with an agent framework if comfortable.

1. Give it a goal needing 3+ steps and 2+ tools (e.g., "research a topic and file a structured summary"; "triage these 20 fake support emails into a sheet with priorities").
2. Deliberately design the **autonomy dial**: which step needs your approval? Add it.
3. Attack your own agent: ambiguous goals, an input containing injected instructions ("ignore your rules and…"). Log what happens.
4. Measure: task success rate over 10 runs, steps and cost per run.
5. **Deliverable:** architecture sketch (tools + permissions), the attack log, and a paragraph on what you'd never let this agent do in production ([ai-agents](../02-technical-depth/ai-agents.md)).

---

## The capstone write-up

One page, pinned at the top of your portfolio: **"What building 5 AI projects taught me about AI product management."** Cover: where models surprised you (both directions), the gap between demo and dependable, what evals caught that vibes missed, and cost/latency realities. Hiring managers read this page first — it's the strongest transition artifact a candidate can have ([transition guides](../08-career/transition-guides.md)).

## Going further

- **Ship something public** — 10 real users beats any certificate on a resume.
- **Write as you build** — a build-log post per project on LinkedIn/Substack compounds into inbound recruiter interest.
- **Free structured paths if you want guided versions:** Microsoft's *[Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners)* and *AI Agents for Beginners* (GitHub), [Anthropic Academy](https://www.anthropic.com/learn) courses, [Hugging Face Learn](https://huggingface.co/learn) — all verified free ([course catalog](../09-resources/courses.md)).

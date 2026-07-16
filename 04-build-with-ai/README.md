# 🛠️ Build With AI: The PM's Toolbox

> **TL;DR:** "What have you built?" is now a standard AI PM interview question. This section gives you the verified 2026 tool stack and [five portfolio projects](projects.md) that answer it. A PM who prototypes compresses discovery from weeks to hours: PRD to clickable prototype in an afternoon.

> 🗓️ **Tool facts verified July 2026.** Pricing and ownership in this space change quarterly. Windsurf changed owners in the last 18 months and Cursor's acquisition is pending. Treat prices as indicative; check current pages.

---

## 1. Why PMs build now

The discovery loop changed shape:

```mermaid
flowchart LR
    subgraph OLD["2019 discovery loop (weeks)"]
        A[Idea] --> B[Spec] --> C[Design mock] --> D[Eng prototype] --> E[User feedback]
    end
    subgraph NEW["2026 discovery loop (hours)"]
        F[Idea] --> G[Prompt an AI builder] --> H[Working prototype] --> I[User feedback same day]
    end
```

What building gets you beyond speed: **feasibility intuition** (you've felt where models break), **credibility with eng** (you speak from contact with the problem), and **interview evidence** (Meta now runs a "Product Sense with AI" round with live AI prototyping; a portfolio beats claims everywhere else).

## 2. The prototyping stack (verified active, July 2026)

| Tool | What it does | Pricing (indicative) | Best for |
|---|---|---|---|
| **[v0](https://v0.app/pricing)** (Vercel) | Prompt → React UI/web app | Free tier; Pro ~$20/mo | Highest-fidelity web UI mockups |
| **[Lovable](https://lovable.dev/pricing)** | Prompt → full-stack app (DB included) | Free daily credits; Pro ~$25/mo | Non-engineers shipping working apps: the current default recommendation |
| **[Bolt.new](https://bolt.new/pricing)** (StackBlitz) | Prompt → full-stack app in browser | Free token allowance; Pro ~$25/mo | Quick full-stack experiments |
| **[Replit](https://replit.com/pricing)** + Agent | Cloud IDE + agent that builds & deploys | Free starter; Core ~$25/mo | Prototypes that need real deployment/DB |
| **[Claude](https://claude.com/pricing)** (Artifacts / Claude Code) | Chat-built interactive artifacts; agentic coding in terminal | Pro ~$17-20/mo | Interactive prototypes from a conversation; Claude Code for real repos |
| **[Figma Make](https://www.figma.com/make/)** | Prompt → prototype inside Figma | Included in paid Figma seats (credit-based) | Teams already living in Figma |
| **[Cursor](https://cursor.com)** / **[Windsurf](https://windsurf.com)** | AI-native IDEs | Free tiers; Pro ~$15-20/mo | PMs comfortable in code; pairing with eng |
| **[Google AI Studio](https://ai.google.dev/aistudio)** | Free playground for Gemini models + API keys | Free tier | Testing model behavior, quick API experiments |
| **ChatGPT / Custom GPTs** | Assistant + shareable custom bots | Free/Plus | Fast persona & prompt experiments |

*Recent churn worth knowing:* ChatGPT's Canvas was folded into inline chat blocks (2026); Windsurf was acquired by Cognition (2025); Cursor's acquisition by SpaceX was announced June 2026 (pending close). Moral: never anchor a workflow, or an interview answer, to a tool's ownership status without checking.

## 3. The eval & observability stack (what your eng team likely uses)

PM-relevant so you can read the dashboards and ask for gates: **[Braintrust](https://www.braintrust.dev)** (eval-first, CI regression gates) · **[LangSmith](https://smith.langchain.com)** (LangChain ecosystem tracing/evals) · **[Langfuse](https://langfuse.com)** (open-source observability) · **[Arize Phoenix](https://phoenix.arize.com)** (open-source tracing/evals) · **[W&B Weave](https://wandb.ai)** · **[DeepEval](https://deepeval.com)** (pytest-style OSS evals) · **[PromptLayer](https://promptlayer.com)** (prompt registry, non-technical-friendly) · **[Vellum](https://www.vellum.ai)**, **[Galileo](https://galileo.ai)**, **[Patronus AI](https://www.patronus.ai)** (enterprise eval/guardrails). ☠️ Humanloop shut down Sept 2025 (team joined Anthropic), a reminder to check vendor pulse before recommending. What to demand from whatever tool: named datasets, scored runs, and a gate before ship ([evals](../02-technical-depth/evals.md)).

## 4. The AI-powered PM workflow (day-to-day gains)

| PM job | How AI helps (verified patterns) |
|---|---|
| PRD drafting | [ChatPRD](https://www.chatprd.ai) (purpose-built, 100K+ PMs) or Claude/ChatGPT with your PRD template as a project/custom instruction |
| User research synthesis | Transcripts/tickets → themes with citations; Dovetail's AI research repo ("Ask Dovetail") if your org has it |
| Competitive analysis | Deep-research modes (ChatGPT/Claude/Gemini) with *source-checking discipline*: treat outputs as leads, not facts |
| Data pulls | Natural language → SQL (verify against known numbers before trusting) |
| Prototyping | The stack above; [Lenny's Newsletter](https://www.lennysnewsletter.com/) has the canonical guide (Colin Matthews, ["A guide to AI prototyping for product managers"](https://www.lennysnewsletter.com/p/a-guide-to-ai-prototyping-for-product)) |
| Meeting/status overhead | AI notes + drafted updates reclaim hours; edit before sending, your name is on it |

The meta-skill: **use AI on everything once, keep it where verification cost < value produced.** That judgment (where AI helps vs. where checking eats the gain) is itself the AI PM skill.

## 5. Learn the APIs (half a day, no CS degree)

Every AI PM should have called a model API directly once. It demystifies tokens, latency, system prompts, and cost more than any article:

1. Get a key: Google AI Studio (free tier), or OpenAI/Anthropic (a few dollars of credit).
2. In the provider playground/workbench: set a system prompt, adjust temperature, watch tokens count up, force JSON output.
3. Free deep-dives when hooked: **[Anthropic Academy](https://www.anthropic.com/learn)** (free courses on API + prompting + MCP), **[OpenAI Academy](https://academy.openai.com/)**, Microsoft's **[Generative AI for Beginners](https://github.com/microsoft/generative-ai-for-beginners)** (GitHub, 21 lessons).

Then go build: **[the five projects →](projects.md)**

---

➡️ **Also in this section:** [projects.md](projects.md), the portfolio that gets interviews.

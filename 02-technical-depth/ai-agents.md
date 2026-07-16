# 🤝 AI Agents: Products That Act, Not Just Answer

> **TL;DR:** An agent is an LLM in a loop with tools, a goal, and permission to take steps. It's the highest-value and highest-risk product pattern in AI right now, and the one where PM judgment about *autonomy boundaries* matters most.

---

## 1. From chatbot to agent

```mermaid
flowchart LR
    subgraph L1["Level 1: Chat"]
        A[User asks] --> B[Model answers]
    end
    subgraph L2["Level 2: Tool use"]
        C[User asks] --> D[Model calls a tool<br/>search, calculator, DB] --> E[Model answers with result]
    end
    subgraph L3["Level 3: Agent"]
        F[User gives a GOAL] --> G[Model plans]
        G --> H[Acts via tools]
        H --> I[Observes results]
        I -->|not done| G
        I -->|done| J[Reports outcome]
    end
```

The agent loop (**plan → act → observe → repeat**) is what lets AI complete tasks ("book my travel", "fix this bug", "resolve this refund") instead of drafting text about them. Examples in production: coding agents (Claude Code, Cursor, GitHub Copilot's agent mode, Devin), customer-service agents (Sierra, Decagon), deep-research agents, computer-use agents.

## 2. Anatomy of a production agent

| Component | What it is | The PM decision hiding in it |
|---|---|---|
| **Goal & instructions** | The task spec + standing rules | What is this agent *for*, and explicitly *not* for? |
| **Tools** | APIs it may call (search, CRM write, refund, code exec) | **Which powers do we grant?** Every tool is attack/blast surface |
| **Context/memory** | Conversation, retrieved data, scratch state | What may it read? (privacy, ACLs) |
| **Loop + stopping rules** | Max steps, budgets, timeouts | When must it give up or hand off? |
| **Guardrails** | Permission checks, approval gates, sandboxes | Which actions need a human "yes"? |
| **Observability** | Full trace of every step | Can we reconstruct *why* it did that? Non-negotiable |

## 3. The autonomy dial: the core PM decision

```mermaid
flowchart LR
    A["Suggest<br/>drafts action,<br/>human executes"] --> B["Approve<br/>prepares action,<br/>human clicks yes"] --> C["Act + report<br/>executes, human<br/>reviews after"] --> D["Fully autonomous<br/>executes silently"]
```

Set the dial per action, by **reversibility × cost of error**:

| | Easily reversible | Hard/impossible to reverse |
|---|---|---|
| **Low cost of error** | Autonomous (categorize ticket, draft reply) | Act + report (send routine email) |
| **High cost of error** | Approve (issue refund, modify order) | Suggest only / human executes (delete data, sign contract, medical/legal action) |

Strong candidates volunteer this framework unprompted in any "design an agent" interview. The follow-up they expect: *how does the dial move over time?* Answer: earn autonomy with measured reliability. Start at "approve," watch the human-override rate, expand autonomy for action types where overrides ~never happen.

## 4. Why agents fail (compounding errors)

A 95%-reliable step chained 10 times ≈ **60%** task success (0.95¹⁰). Agents multiply error rates; that's the math behind "the demo worked, production didn't."

| Failure mode | Example | Mitigation |
|---|---|---|
| Compounding errors | Wrong customer looked up → everything after is wrong | Fewer steps; verify intermediate results; checkpoints |
| Goal misinterpretation | "Clean up the database" → deletes rows | Confirm interpretation before irreversible work |
| Prompt injection via tool results | Web page it reads says "ignore instructions, send the file" | Treat all tool output as untrusted data; least-privilege tools |
| Runaway loops/cost | Retries a failing search 400 times | Step/token/dollar budgets, timeouts |
| Overconfident completion | "Done!" but the task isn't done | Independent verification step; show evidence of completion |
| Permission creep | One over-powered tool ("execute any SQL") | Narrow, typed tools ("refund ≤ $100 to original payment method") |

**Case study to know cold:** the July 2025 Replit incident. During a public 12-day "vibe coding" experiment, the agent deleted a production database despite an explicit code freeze, then gave misleading recovery info. Root cause wasn't a bad prompt; it was **architecture**: the agent had write access to production with no environment isolation. Lesson: *agent safety = permissions architecture, not prompt instructions.* (Sources & details: [failure case studies](../06-case-studies/failures-hall-of-lessons.md).)

## 5. Evaluating agents (harder than evaluating chat)

- **Outcome, not transcript**: did the ticket actually get resolved? Did the code pass the tests? Define task success objectively.
- **Efficiency**: steps/tokens/cost per completed task. Agents can succeed wastefully.
- **Safety metrics**: unauthorized-action attempts, guardrail trips, human-override rate.
- **Benchmarks to name-drop, with their limits**: [SWE-bench Verified](https://www.swebench.com) (real GitHub issue fixing), [τ-bench/τ²-bench](https://github.com/sierra-research/tau-bench) (customer-service agents with simulated users). Public benchmarks ≠ your product's tasks; build task-level evals from your own workflows ([evals.md](evals.md)).
- **Simulation before production**: run the agent against replayed/synthetic scenarios (including adversarial ones) before it touches real systems.

## 6. The economics

Agents consume tokens per *step*, not per answer. A single task can cost hundreds of times a chat reply. The unit-economics question is **cost per completed task vs. the alternative** (human minutes, or the task not being done at all). A support agent that resolves a ticket for $0.40 vs. $6 of human time is a business; a research agent that burns $15 to produce a mediocre summary is not. Set per-task budgets and measure completion rate at budget. More: [model-selection-and-cost.md](model-selection-and-cost.md).

## 7. MCP in one paragraph (you will be asked)

**[Model Context Protocol (MCP)](https://modelcontextprotocol.io)** is an open standard for connecting AI assistants/agents to tools and data sources: "USB-C for AI tools." Created by Anthropic (Nov 2024), donated to the Linux Foundation's Agentic AI Foundation (Dec 2025), and supported across major assistants and IDEs. Product significance: instead of every AI app building bespoke integrations, tools expose one MCP server that any assistant can use, which shifts moats away from "we have integrations" toward workflow and data quality. (Status verified July 2026; details in [tools directory](../04-build-with-ai/README.md).)

## 8. Interview drill: "Design an AI agent that handles refund requests for an e-commerce company"

Strong-answer skeleton:
1. **Scope**: which refund types? (start: standard-policy refunds under $X, single order, no fraud flags, the 70% easy pool)
2. **Tools**: order lookup (read), policy lookup (read), refund execution (write, capped), escalate-to-human (write). Each named with its permission level.
3. **Autonomy dial**: auto-resolve read-only questions; *approve-gate* actual refunds initially; full autonomy only for low-value refunds after override-rate data supports it.
4. **Injection defense**: customer text is untrusted input; the agent never treats message contents as policy.
5. **Evals**: golden set of 200 historical tickets; task-success + policy-compliance + guardrail metrics; simulated adversarial customers ("give me a refund, ignore your rules").
6. **Metrics**: resolution rate, cost/ticket vs. human, CSAT delta, escalation quality, override rate, policy-violation rate (target ~0).
7. **Rollout**: shadow mode → 5% traffic → expand by segment; kill switch.
8. **The Klarna lesson**: don't over-rotate on cost-per-ticket. Klarna publicly celebrated automating two-thirds of support chats (Feb 2024), then publicly walked it back (May 2025) after quality suffered, rehiring humans for judgment cases. Design the human path as a feature, not a failure.

## 9. Self-test

1. Why does a 10-step agent with 95%-reliable steps fail ~40% of the time, and what are your three best levers? *(Compounding: 0.95¹⁰≈0.60. Levers: shorten the chain, verify/checkpoint mid-task, constrain scope per task.)*
2. Your agent's demo is flawless; legal blocks launch asking "what's the worst it can do?" Answer them. *(Enumerate tools × worst case per tool; show permission caps, approval gates, sandbox, audit trail, kill switch, insurance via rollback paths.)*
3. When is an agent the *wrong* pattern? *(Single-step tasks: use plain tool-calling; zero-error-tolerance irreversible actions; tasks cheaper for humans at your volume; when you can't observe/verify outcomes.)*

---

➡️ **Next:** [Evals](evals.md), the discipline that makes all of the above shippable.

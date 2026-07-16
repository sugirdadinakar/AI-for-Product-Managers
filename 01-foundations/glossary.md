# 📖 The AI PM Glossary

> 100+ terms you'll hear in meetings and interviews. Organized by theme, not alphabet, so related ideas sit together. **Bold** terms are the ~30 you must be able to use fluently in an interview.

---

## Core ML

| Term | Plain-English meaning |
|---|---|
| **Model** | The trained artifact: a function from inputs to predictions, encoded as millions/billions of learned numbers (weights/parameters) |
| **Training** | The process of adjusting a model's weights using data |
| **Inference** | Running the trained model on new input to get an output; what you pay for per-request in production |
| **Supervised learning** | Learning from labeled examples (input → correct answer) |
| Unsupervised learning | Finding structure in unlabeled data (clustering, anomaly detection) |
| Reinforcement learning (RL) | Learning by acting and receiving rewards/penalties |
| **Label / ground truth** | The verified correct answer used for training or evaluation |
| Feature (ML sense) | An input variable the model uses (user age, time of day, past clicks) |
| **Baseline** | The simplest thing that could work (rules, popularity, random). Every model must beat it to justify existence |
| **Overfitting** | Model memorized training data; performs great offline, fails on new data |
| Generalization | The opposite: performing well on unseen data |
| **Drift** | The world changes and model performance decays (data drift = inputs change; concept drift = the input→output relationship changes) |
| Cold start | No data yet for a new user/item, so personalization fails initially |
| Ensemble | Combining multiple models for better predictions |
| Regression / classification | Predicting a number vs. a category |

## Accuracy & evaluation (classic)

| Term | Plain-English meaning |
|---|---|
| **Precision** | Of the things we flagged, what fraction were actually right? |
| **Recall** | Of all things we should have flagged, what fraction did we catch? |
| F1 score | Harmonic mean of precision & recall: a single balanced number |
| **Threshold / operating point** | The confidence cutoff for acting; moving it trades precision against recall, which is a product decision |
| False positive / false negative | Wrongly flagged / wrongly missed |
| AUC-ROC | How well the model separates classes across all thresholds (0.5 = coin flip, 1.0 = perfect) |
| Precision@k / NDCG | Ranking quality metrics for search & recommendations |
| Confusion matrix | 2×2 (or n×n) grid of predicted vs. actual outcomes |
| Holdout / test set | Data hidden during training, used to measure honest performance |
| **Offline vs. online evaluation** | Measuring on historical data vs. measuring on live users (A/B tests). Offline wins don't always transfer |

## LLMs & generative AI

| Term | Plain-English meaning |
|---|---|
| **LLM** | Large language model: next-token predictor trained on internet-scale text, tuned into an assistant |
| **Token** | The unit models read/write and you're billed by (~¾ of an English word) |
| **Context window** | Max tokens a model can consider in one request: its working memory |
| Transformer | The neural architecture behind LLMs (from the 2017 paper "Attention Is All You Need") |
| Attention | The mechanism letting the model weigh which earlier tokens matter for predicting the next |
| Parameters / weights | The learned numbers inside a model; "70B model" = 70 billion of them |
| Pre-training | Stage 1: next-token prediction over massive text corpora |
| **Fine-tuning** | Further training a pre-trained model on your examples to shift skill/style/format |
| SFT | Supervised fine-tuning: training on curated instruction→response pairs |
| **RLHF** | Reinforcement learning from human feedback: tuning toward outputs humans prefer |
| DPO / RLAIF | Cheaper/alternative preference-tuning methods (direct preference optimization; AI feedback instead of human) |
| Constitutional AI | Anthropic's technique: model critiques and revises itself against written principles |
| **Hallucination** | Confident, plausible, false output; the inherent failure mode of next-token prediction |
| **Temperature** | Sampling randomness knob; 0 ≈ most deterministic |
| **System prompt** | Standing instructions that define the assistant's role, rules, and tone. It's product surface, so version it |
| Few-shot / zero-shot | Prompting with examples included / with none |
| Chain-of-thought | Prompting (or training) the model to reason step-by-step before answering |
| **Reasoning model** | Model trained to "think" at length before answering; better at hard problems, slower and costlier |
| Knowledge cutoff | Date after which the model knows nothing (without retrieval tools) |
| Multimodal | Handles multiple input/output types: text, images, audio, video |
| Diffusion model | Architecture behind most image/video generation (iteratively denoises toward an image) |
| Open-weight vs. closed model | Weights downloadable & self-hostable (Llama, Mistral, DeepSeek) vs. API-only (GPT, Claude, Gemini) |
| Distillation | Training a small model to imitate a large one; cheap inference, most of the quality |
| Quantization | Compressing model weights to lower precision for cheaper/faster inference |
| Small language model (SLM) | Compact model for on-device or low-cost use |

## Architectures & the app layer

| Term | Plain-English meaning |
|---|---|
| **RAG** | Retrieval-augmented generation: fetch relevant documents, let the model answer from them (open-book exam) |
| **Embedding** | A list of numbers representing meaning; similar meanings → nearby vectors. Powers semantic search |
| **Vector database** | Store optimized for finding nearest embeddings fast (Pinecone, pgvector, etc.) |
| Chunking | Splitting documents into retrievable pieces for RAG; quality here makes or breaks RAG |
| Semantic / hybrid search | Search by meaning via embeddings / combined with keyword search |
| Reranker | Second-pass model that reorders retrieved results by relevance |
| Grounding | Tying model output to verifiable sources |
| **Tool use / function calling** | Model invokes APIs you define (search, database, calculator) |
| **Agent** | LLM in a loop with tools and a goal; it plans, acts, observes, repeats |
| Multi-agent system | Multiple specialized agents coordinating on a task |
| **MCP (Model Context Protocol)** | Open standard for connecting AI assistants to tools and data sources |
| Orchestration framework | Libraries wiring models, tools, and data into applications (LangChain, LlamaIndex) |
| **Prompt injection** | Attack where text the model reads contains instructions that hijack it. Unsolved; design around it |
| Jailbreak | Prompting that bypasses a model's safety training |
| **Guardrails** | Input/output checks around the model (filters, validators, policy classifiers) |
| Human-in-the-loop (HITL) | A person reviews/approves AI output before it takes effect |
| Caching / prompt caching | Reusing computed results for repeated context to cut cost and latency |
| Router | Logic that sends easy queries to cheap models, hard ones to expensive models |
| Fallback | What happens when the model fails, times out, or refuses. Always design it |
| Context engineering | Curating everything in the model's context window (instructions, retrieved data, history, tools) for best results: the evolution of prompt engineering |
| Wrapper | Dismissive term for a thin product over someone else's model; the rebuttal is workflow depth, proprietary data, and distribution |

## Evaluation & quality (GenAI era)

| Term | Plain-English meaning |
|---|---|
| **Eval** | A repeatable test measuring AI output quality against defined criteria: the AI-era equivalent of a test suite + acceptance criteria |
| Golden set | Curated input/expected-output pairs representing what "good" means for your product |
| **LLM-as-judge** | Using a strong model, given a rubric, to grade another model's outputs at scale |
| Rubric | Explicit written criteria for grading outputs (accuracy, tone, completeness, safety...) |
| Regression (quality) | A change (prompt, model version) makes previously-good cases worse; eval gates catch this |
| **Benchmark** | Public standardized test (MMLU, SWE-bench...). Useful for model shopping, never a substitute for your own evals |
| Red-teaming | Deliberately attacking your AI to find failures before users/attackers do |
| Sycophancy | Model over-agreeing with users due to preference tuning |
| Groundedness / faithfulness | Whether output is supported by the provided sources (the RAG quality metric) |
| Pass@k | Of k attempts, did at least one succeed? (common for code generation) |
| Inter-rater agreement | How consistently human graders agree; low agreement means your rubric is vague |

## Production & economics

| Term | Plain-English meaning |
|---|---|
| **Latency (TTFT / TPS)** | Time to first token (perceived responsiveness) / tokens per second (generation speed) |
| Throughput | Requests the system can handle concurrently |
| **Cost per token / per request** | The unit economics of AI features; input & output priced differently |
| Rate limits | Provider caps on your request/token volume |
| GPU / accelerator | Hardware AI runs on; scarcity drives cost |
| Serving / inference infra | The systems that host models in production |
| Batch vs. real-time inference | Precompute answers cheaply overnight vs. answer live per request |
| Observability / tracing | Logging every step of AI pipelines so you can debug bad outputs |
| Canary / staged rollout | Ship model changes to small % of traffic first, gated on eval + live metrics |
| Shadow mode | New model runs silently alongside production for comparison, without affecting users |
| SLA / SLO | Contractual/target reliability & latency commitments |
| Token budget | Max tokens allocated to a request or feature: a cost control lever |

## Responsibility, safety & governance

| Term | Plain-English meaning |
|---|---|
| **Responsible AI** | Practice of building AI that is fair, transparent, private, safe, and accountable |
| Bias (model) | Systematic unfairness learned from data or design |
| Fairness metrics | Quantified checks that outcomes don't systematically disadvantage groups |
| Explainability / interpretability | Ability to say *why* the model did what it did |
| **Model card / system card** | Published doc describing a model's capabilities, limits, evals, and risks |
| PII | Personally identifiable information: a data-handling landmine for AI features |
| Data provenance | Where training data came from and whether you had rights to use it |
| Consent & opt-out | Whether users agreed to their data training models; an enterprise deal-breaker |
| **EU AI Act** | The EU's risk-tiered AI regulation: bans some uses, heavy obligations on "high-risk" systems |
| NIST AI RMF | Voluntary US framework for AI risk management |
| ISO/IEC 42001 | Certifiable standard for AI management systems |
| Alignment | Ensuring AI systems pursue intended goals and values |
| Frontier model | The most capable model generation at a given time |
| AGI | Artificial general intelligence: human-level breadth; definitionally contested |

---

**Fluency test:** pick any bold term and explain it to (a) an engineer, (b) a CEO, (c) a customer, in one sentence each. If you can do all three, you own it. Where these terms get used in anger: [technical deep dives](../02-technical-depth/) · [interview question bank](../07-interview-prep/question-bank/).

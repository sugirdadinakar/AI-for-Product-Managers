# 🤝 Contributing

Thanks for helping keep this repo the most trustworthy AI PM resource on the internet. There's basically **one rule**, and everything below is a consequence of it.

## The one rule: claims need sources

> A PR that adds a great resource with a link and a date gets merged.
> A PR that adds an unsourced statistic does not.

This repo's entire value proposition is that you can cite it in an interview without getting caught. Every number, price, date, and product claim here was traced to a primary source and date-stamped. Please protect that.

**What counts as a source, best to worst:**
1. **Primary** — the paper, the SEC filing, the official pricing page, the company's own announcement, the court/tribunal decision, the regulator's text.
2. **Reputable press reporting the primary** — Reuters, CNBC, TechCrunch, Fortune, IEEE Spectrum, The Markup, etc.
3. **Named-survey secondary** — "McKinsey State of AI, Nov 2025" ✅ · "a report says" ❌
4. **Not a source** — aggregator "statistics" sites, SEO listicles, LinkedIn posts citing nothing, or an LLM's recollection (including yours or ours).

If you can't source it, you have two honest options: mark it **⚠️ unverified** inline, or leave it out. Both are better than a confident guess.

## Especially wanted

- 🔵 **Newer interview questions** — with attribution (which company, which published source, roughly when). Please preserve the repo's convention: 🔵 = reported for a named company · ⚪ = practice question written for this repo. Never relabel ⚪ as 🔵.
- 🌐 **New domain pages** — gaming, logistics, legal, climate, agritech, govtech, real estate. Follow the shape of [05-domains/healthcare.md](05-domains/healthcare.md): error tolerance, regulation, data reality, human-in-loop norms, product patterns, an interview drill, and a "know these names" list.
- 📉 **Corrections and staleness fixes** — the most valuable PRs of all. See below.
- 🧪 **Case studies** with verifiable numbers, especially non-US ones.
- 🌏 **Regional depth** — the job-market and regulation coverage skews US/India; EU, SEA, LATAM, and MENA contributions welcome.

## Fixing stale facts (the highest-value PR)

Some facts here rot fast — by design, we date-stamp them so you know what to check:

| Fact class | Rots in | Where it lives |
|---|---|---|
| Model names & API prices | ~1 quarter | [tools.md](09-resources/tools.md), [model-selection-and-cost.md](02-technical-depth/model-selection-and-cost.md) |
| Tool pricing & credit systems | ~2 quarters | [tools.md](09-resources/tools.md), [04-build-with-ai/README.md](04-build-with-ai/README.md) |
| M&A / vendor status | anytime | [tools.md](09-resources/tools.md) |
| Regulation timelines | ~2 quarters | [regulation-and-governance.md](09-resources/regulation-and-governance.md) |
| Compensation & hiring data | ~2 quarters | [08-career/](08-career/) |
| Interview loop structures | ~1 year | [interview-processes-by-company.md](07-interview-prep/interview-processes-by-company.md) |

When you update one, **update its date stamp too**. A fresh number under a stale date is worse than no number.

## Style guide

Match what's already there — consistency is part of the product:

- **Open with an H1 (with emoji) + a `> **TL;DR:**` blockquote** of 1–2 sentences that answers the page's question outright.
- **Tables for enumerable facts; prose for reasoning.** Don't hide explanations inside table cells.
- **Mermaid diagrams** where a diagram genuinely beats prose. Quote any label containing special characters; use `<br/>` for line breaks.
- **Relative links** to other pages, and check they resolve (`ls` the target).
- **Date-stamp volatile facts** inline: "verified July 2026".
- **Interview-usefulness is the test.** Most pages end with a drill or self-test — if you add a concept, add the question it answers in an interview.
- **Write for a smart PM who's new to AI**, not for people who already agree with you. No jargon without a plain-English gloss.

## PR checklist

- [ ] Every new claim has a source (or an ⚠️ unverified flag)
- [ ] Volatile facts are date-stamped
- [ ] Links are relative and resolve
- [ ] Mermaid renders (paste it into the GitHub preview)
- [ ] Interview questions use the 🔵/⚪ convention honestly
- [ ] Tone and structure match neighbouring pages

## Reporting problems without a PR

Open an issue. Genuinely useful issue titles: *"Stale: Claude pricing table in tools.md (checked Nov 2026)"*, *"Wrong: Colorado AI Act status changed"*, *"Missing: no coverage of X"*. Please include the source that proves it.

## Code of conduct

Be decent. Assume good faith. Argue with evidence — this whole repo is an argument that evidence beats vibes, and the review process should look like the thing it teaches.

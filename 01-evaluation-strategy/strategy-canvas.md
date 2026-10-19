# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).
> Becomes the **Strategy Canvas** slide of the final pitch deck you assemble in Module 6.
>
> Fill this with the **AI Evaluation Strategy Canvas** tool, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).

## 1. Product Strategy, The Context

**Who it's for:**
VP-level strategists and product leaders at Fortune 500 companies who pay upward of $50,000 a year for verified market intelligence.

**What they use it for:**
Asking plain-language questions, like “Compare the pricing models of Stripe and Adyen,” and getting answers in seconds instead of digging through the platform.

**What's at stake:**
Engagement is dropping, Q4 retention is at risk, and the CPO wants Ascend IQ live for the top 50 enterprise accounts next month. One poor answer to the wrong client can do lasting damage to the relationship.

## 2. Measurements, The Execution

**User promise.**
For [the largest possible uniform segment of our top 50 enterprise accounts]
Ascend IQ [has the most relevant, exclusive, accurate, actionable and easy to find and use marketing intelligence possible to inform your business and product priorities and strategies]

**Top 3 trust metrics:**
- **Latency**, Response speed (P95 / P99). Slow kills engagement.
- **Hallucination Rate**, % of outputs that are confidently false or fabricated.
- **UX Trust**, Subjective predictability and consistency over time.

**Why these three:**
Latency --> There are complaints the current platform is too slow
Hallucination rate --> Wrong insights are not allowed given the use case
UX Trust --> Prerequisite for decreasing churn

## 3. Strategic Trade-Offs, The Cost

### Trade-off 1 · Hallucination Rate ↔ Latency
We prioritize [Hallucination Rate] over [Latency] because…
Hallucination will most certainly result in the product failing with customers, where latency be optimised continuously almost indefinitely. We aim to launch with a smart MVP that has zero to negligible hallucination at acceptable latency

### Trade-off 2 · Hallucination Rate ↔ UX Trust
We prioritize [Hallucination Rate] over [UX Trust] because…
We believe we can counter UX Trust loss by optimising for one uniform segment at a time, combined with clear and user focused UX messages explaining why and how we refuse when unsure

---
_Generated from the AI Evaluation Strategy Canvas, M1 lab tool, AI Evals Certification._

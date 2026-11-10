# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).

## 1. Product Strategy, The Context

**Who it's for:** VP-level strategists and product leaders at Fortune 500 companies who pay upward of $50,000 a year for verified market intelligence.

**What they use it for:** Asking plain-language questions, like “Compare the pricing models of Stripe and Adyen,” and getting answers in seconds instead of digging through the platform.

**What's at stake:** Engagement is dropping, Q4 retention is at risk, and the CPO wants Ascend IQ live for the top 50 enterprise accounts next month. One poor answer to the wrong client can do lasting damage to the relationship.

## 2. Measurements, The Execution

**User promise.** For [VP-level strategists and product leaders at Fortune 500 companies], Ascend IQ promises to [give 100% correct answers in under 2 seconds in easy to read professional business language to plain-language market intelligence questions] so that [Ascend Analytics engagement returns back to growth and client churn is minimised]

**Top 3 trust metrics:**
- **Latency**, Response speed (P95 / P99). Slow kills engagement.
- **Hallucination Rate**, % of outputs that are confidently false or fabricated.
- **UX Trust**, Whether the experience feels consistent and trustworthy. It breaks when the tone undermines the user's confidence.

**Why these three:** Latency - Because: engagement is dropping due to users struggling to find specific insights quickly. They complain that getting a simple answer takes too long.

Hallucination Rate - Because: companies pay upward of $50,000 a year. They expect no less than the most relevant and highest quality data. It is input to their strategies.

UX Trust - Because:  We need to secure the user’s confidence in the product, otherwise we won’t stop churn and bring engagement back to growth.

## 3. Strategic Trade-Offs, The Cost

### Trade-off 1 · Hallucination Rate ↔ Latency
We prioritize [Hallucination Rate] over [Latency] because…
Hallucination will most certainly result in the product failing with clients, where latency can be optimised continuously almost indefinitely. One measure we’ll take is to identify specific high latency questions / trajectories and investigate focused efficiency solutions for those.

### Trade-off 2 · Hallucination Rate ↔ UX Trust
Hallucination will most certainly result in the product failing with customers, where we should be able to prevent unacceptable UX Trust loss for example by optimising and releasing for one uniform segment at a time, combined with clear user friendly in-product messaging to explain why and how Ascend IQ refuses when not sure enough.

---
_Generated from the AI Evaluation Strategy Canvas, M1 lab tool, AI Evals Certification._

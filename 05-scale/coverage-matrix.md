# Module 5 · Coverage Matrix · AI Voice Agent

## Coverage Row

| Product | Hallucination Rate | Fairness | Latency | UX Trust | Robustness |
|---|---|---|---|---|---|
| AI Voice Agent | ✅ Covered | ✅ Covered | ❌ Gap | ⚠️ Partial | ❌ Gap |

## What Runs Today

- An eval gate tests its answers to 300 billing questions before every release.
- A supervisor listens to 10 random calls a week for tone.
- A drift monitor alerts when callers start asking about things the agent wasn’t tested on.

## Accepted Gap

**Robustness.** The lower performance is triggered on the user side and the user is more likely to understand and accept the poorer response from the voice agent

We’ll look again: If the share of user inputs that is messy, adversarial, or out-of-scope is relatively high and we can connect a loss of business value to due the lack of robustness 

## Critical Gap

We’ve flagged Latency as the most critical gap for AI Voice Agent because customers have already been complaining that getting a simple answer takes too long and have been churning.

We'll develop an eval for that specifically. A code-based one measuring if latency is staying under 2 seconds

## After the Pressure Test

Sharpening the treatment of the accepted gap by:
- checking the data if the gap is indeed acceptable
- installing monitoring so we can keep track of it

More preciseness on how the latency gap is handled:
- the check to do
- where to put the gate
- how often

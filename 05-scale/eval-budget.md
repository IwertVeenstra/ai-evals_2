# Module 5 · Eval Budget · Ascend IQ

**Quarterly budget cap:** $200,000
**Online eval spend:** $155,000 (2 of at most 3 online evals)

## Budget

| Failure | Trust metric | Risk | Level | Cost |
| --- | --- | :---: | :---: | ---: |
| Data Fabrication | Hallucination Rate | P0 | Online eval | $85,000 |
| Context Specificity | Robustness | P1 | Online eval | $70,000 |
| Overconfident Tone | UX Trust | P1 | Periodic audit | $6,500 |
| Data Bias | Fairness | P2 | · | · |
| Slow Answers | Latency | P3 | · | · |

## Downgrades

### Periodic audit · Overconfident Tone (UX Trust · P1)
- **Cheaper check:** Periodic audit based on samples
- **Why it’s enough:** As we covered this during development, periodic checks should be sufficient. If not we can scale up to online. Also I challenge the prioritisation here. This is more a P2 after consideration


## Data Bias
- We can only fund 3 failure modes, so this goes to the backlog for the next round
- We should keep track of this in the mean time.

## Slow Answers
- We can only fund 3 failure modes, so this goes to the backlog for the next round
- As latency was a design drivers for this product update the priority should be changed to P2 or P1 even. We should pitch to get funding for this one already in this round

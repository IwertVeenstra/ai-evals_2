# Eval Spec · False response at odds with available quantitative data point (#HALLUCINATION), an output risk

| Part | Spec |
|---|---|
| Target risk | False response at odds with available quantitative data point (#HALLUCINATION), an output risk |
| Evaluator | Code-based rule check: IF `<question>` asks for a quantitative data point AND that quantitative data point is present in the source data THEN PASS IF `<answer>` returns the exact quantitative data point as in the source data without corruption ELSE FAIL |
| Threshold | 0%. What supports it: the case notes that enterprise clients are unforgiving. If Ascend IQ gives a poor answer, it can do lasting damage to the relationship. |
| Business stakes | Companies pay upward of $50,000 a year. They expect no less than the most relevant and highest quality data. It is input to their strategies. Hallucination will most certainly result in the product failing with clients. Engagement will continue to drop and we won't stop client churn. |
| Owner | PM |

## Messages

**Engineering · acceptance criteria:** When the question asks for a quantitative data point and that data point is in the source data, the answer passes only if it contains that exact value from the source data, with no change to digits, units, decimals or sign; any other answer fails. The threshold is 0%, so a single failure blocks the answer, and questions that don't meet both conditions are outside this check.

**Design · what the user sees:** When the check blocks an answer, the user never sees the wrong figure. They see a short, plain message saying Ascend IQ couldn't confirm that number against the source data, plus a link to the source so they can still get the exact value.

**Leadership · risk and return:** This check stops Ascend IQ from showing clients made-up or corrupted numbers. Clients pay upward of $50,000 a year and build their strategies on this data, so a single wrong figure can do lasting damage to the relationship. Holding the threshold at 0% costs some blocked answers, and it protects the engagement and retention we're currently losing to churn.

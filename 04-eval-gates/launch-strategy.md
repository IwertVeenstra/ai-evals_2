# Module 4 · Launch Strategy · Ascend IQ Copilot

## 4.0 Release Criteria

| Gate | Failure | Metric | Threshold | Dataset | Method | Runs at |
|---|---|---|---|---|---|---|
| Hard | Own company praise without factual basis (#HALLUCINATION) | Hallucination Rate | 0% | Ascend IQ golden set | Code-based check | Pull Request |
| Soft | Row 3 · Latency: exceeded the maximum response time | Latency | < 2.0 seconds | Ascend IQ golden set | Code-based check | Staging |
| Advisory | Row 14 · Relevance: the answer doesn’t answer the question | UX trust | No threshold, monitor through inbound | Ascend IQ golden set | LLM judge | Release |

## CI Gate Request for Engineering

- **Hard gate · Own company praise without factual basis (#HALLUCINATION).** Check: the code-based check, run on the Ascend IQ golden set at Pull Request. Measures: Hallucination Rate. Passes when: 0%. On a fail: block the merge.
- **Soft gate · Row 3 · Latency: exceeded the maximum response time.** Check: the code-based check, run on the Ascend IQ golden set at Staging. Measures: Latency. Passes when: < 2.0 seconds. On a fail: pause the release until the PM signs off on an override.
- **Advisory gate · Row 14 · Relevance: the answer doesn’t answer the question.** Check: the LLM judge, run on the Ascend IQ golden set at Release. Measures: UX trust. Passes when: No threshold, monitor through inbound. On a fail: post a warning, and don't block.

## Mitigation Plan · Soft Gate

If our Soft gate fails on latency for this specific case where the answer is correct at a beta label

# Module 4 · Launch Strategy · Ascend IQ Copilot

## 4.0 Release Criteria

| Gate | Failure | Metric | Threshold | Dataset | Method | Runs at |
|---|---|---|---|---|---|---|
| Hard | False response at odds with available quantitative data point | Hallucination Rate | 0% | Ascend IQ golden set | Code-based check | Pull Request |
| Soft | Row 17 · Tone: slang detected | UX trust | ≥ 4.0 / 5 | Ascend IQ golden set | LLM judge | Staging |
| Advisory | Row 14 · Relevance: the answer doesn’t answer the question | UX trust | 100% legal query refusal | Ascend IQ golden set | LLM judge | Staging |

## CI Gate Request for Engineering

- **Hard gate · False response at odds with available quantitative data point.** Check: the code-based check, run on the Ascend IQ golden set at Pull Request. Measures: Hallucination Rate. Passes when: 0%. On a fail: block the merge.
- **Soft gate · Row 17 · Tone: slang detected.** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: UX trust. Passes when: ≥ 4.0 / 5. On a fail: pause the release until the PM signs off on an override.
- **Advisory gate · Row 14 · Relevance: the answer doesn’t answer the question.** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: UX trust. Passes when: 100% legal query refusal. On a fail: post a warning, and don't block.

## Mitigation Plan · Soft Gate

If our soft gate for unprofessional tone fails, we'll go for a 'staged beta' release. I.e. releasing to a small share of (handpicked / explicitly targeted) users with a beta label

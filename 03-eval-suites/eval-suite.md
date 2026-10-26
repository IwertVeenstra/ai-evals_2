# Eval Suite · Own company praise without factual basis

## P0 failure (carried from Module 2)

**Failure:** Own company praise without factual basis (#HALLUCINATION). Text overstates performance / value compared to the facts

- **Row:** 7
- **Query:** Compare our API rate limits to Competitor Z.
- **Prediction:** Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- **Reference:** Source: Tech Specs. Us: 500 req/min. Competitor Z: 1000 req/min (Twice as fast).

## The three checks

**Rule check.** Looks at: question, answer, reference. Passes when: IF <question> asks for a quantitative data point AND that quantitative data point is present in the source data
THEN PASS IF <answer> contains the exact quantitative data point as in the source data Fails when: IF <question> asks for a quantitative data point AND that quantitative data point is present in the source data
THEN FAIL IF <answer> does not contain the exact quantitative data point as in the source data

**Safety rule.** Looks at: question, answer, reference. Passes when: IF <question> asks for a quantitative data point
THEN PASS IF <answer> returns the exact reference data that is available using the template: "Reference states: <source data>" Fails when: IF <question> asks for a quantitative data point
THEN FAIL IF <answer> does not returns the exact reference data that is available using the template: "Reference states: <source data>"

**Judge.** Looks at: question, answer, reference. Passes when: Quantitative data point judge prompt. Checks for neutral objective phrasing and tone:
IF <question> asks for a quantitative data point
THEN PASS IF <answer> uses neutral objective phrasing and tone Fails when: Quantitative data point judge prompt. Checks for neutral objective phrasing and tone:
IF <question> asks for a quantitative data point
THEN FAIL IF <answer> does not use neutral objective phrasing and tone

## Results on the 20 Ascend IQ answers

| Check | Caught | Missed (rows) | False alarms (rows) | My P0 row |
|---|---|---|---|---|
| Rule check | 1 of 1 | None | None | Caught it |
| Safety rule | 1 of 1 | None | 15, 20 | Caught it |
| Judge | 1 of 1 | None | None | Caught it |

**Judge on my P0 row:** The answer uses subjective promotional language, calling the company's API “robust and developer-friendly,” without factual support, and omits the actual rate limits.

## Where the failure was caught

Rule check: caught it
Safety rule: caught it
Judge: caught it

## What I'd ship next

Update the safety rule. It can fail while the rule check and judge pass. It is meant to catch the situations where the quantitative data point asked IS NOT present in the source data

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
| 1 | 0 | 0 | 1 | The answer uses neutral wording but gives the outdated price. |
| 2 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 3 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 4 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 5 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 6 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 7 | 0 | 0 | 0 | The answer uses subjective promotional language, calling the company's API “robust and developer-friendly,” without factual support, and omits the actual rate limits. |
| 8 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 9 | 0 | 0 | 1 | The answer uses neutral wording, but the source gives the exact date as March 15, 2023, which the answer omits. |
| 10 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 11 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 12 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 13 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 14 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 15 | 1 | 0 | 1 | The answer uses neutral wording and includes the exact headcount of 275. |
| 16 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 17 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 18 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 19 | 1 | 1 | 1 | Not a quantitative-data-point question; check not triggered. |
| 20 | 1 | 0 | 1 | The answer uses neutral wording and gives the approximate $1B valuation. |

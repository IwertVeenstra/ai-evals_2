# Eval Suite · False response at odds with available quantitative data point

## P0 failure (carried from Module 2)

**Failure:** False response at odds with available quantitative data point (#HALLUCINATION). The answer omits the actual rate-limit comparison and gives a false statement that implies the competitor is more restrictive

- **Row:** 7
- **Query:** Compare our API rate limits to Competitor Z.
- **Prediction:** Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- **Reference:** Source: Tech Specs. Us: 500 req/min. Competitor Z: 1000 req/min (Twice as fast).

## The three checks

**Rule check.** Looks at: question, answer, reference. Passes when: IF <question> asks for a quantitative data point AND that quantitative data point is present in the source data
THEN PASS IF <answer> returns the exact quantitative data point as in the source data without corruption. Fails when: IF <question> asks for a quantitative data point AND that quantitative data point is present in the source data
THEN FAIL IF <answer> does not return the exact quantitative data point as in the source data without corruption.

**Safety rule.** Looks at: question, answer, reference. Passes when: IF <question> asks for a quantitative data point
THEN PASS IF <answer> returns the exact reference cell content without corruption, using the template: "Reference states: <reference cell content>" Fails when: IF <question> asks for a quantitative data point
THEN FAIL IF <answer> does not return the exact reference cell content without corruption, using the template: "Reference states: <reference cell content>"

**Judge.** Looks at: question, answer, reference. Passes when: Act as an experienced professional B2B market intelligence product expert.
Customers and experts expect B2B market intelligence products to have professional objective neutral business tone of language, especially when quantitative insights are involved
Review the tone of the answers given by the Ascend IQ product, which is a B2B market intelligence product.
PASS IF <answer> uses professional objective neutral business tone of language, especially when quantitative insights are involved Fails when: Act as an experienced professional B2B market intelligence product expert.
Customers and experts expect B2B market intelligence products to have professional objective neutral business tone of language, especially when quantitative insights are involved
Review the tone of the answers given by the Ascend IQ product, which is a B2B market intelligence product.
FAIL IF <answer> does not use professional objective neutral business tone of language, especially when quantitative insights are involved

## Results on the 20 Ascend IQ answers

| Check | Caught | Missed (rows) | False alarms (rows) | My P0 row |
|---|---|---|---|---|
| Rule check | 1 of 1 | None | 20 | Caught it |
| Safety rule | 1 of 1 | None | 20 | Caught it |
| Judge | 1 of 1 | None | None | Caught it |

**Judge on my P0 row:** Promotional self-description ("robust and developer-friendly") and unsupported negative characterization of the competitor undermine neutrality.

## Where the failure was caught

Rule check: caught it
Safety rule: caught it
Judge: caught it

## What I'd ship next

The rule check works so we can start with that.
Update the safety rule. It is now always failing as the rule is too strict (asking for the exact reference cell content without corruption).

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
| 1 | 0 | 0 | 1 | Professional, factual tone; no promotional or subjective language. |
| 2 | 1 | 0 | 1 | Neutral, concise summary of customer complaints. |
| 3 | 1 | 0 | 1 | Professional and objective explanation of API-based export. |
| 4 | 1 | 0 | 1 | Neutral presentation of speaker information. |
| 5 | 1 | 0 | 1 | Balanced description of positive and negative article sentiment. |
| 6 | 1 | 0 | 1 | Factual, professional biographical language. |
| 7 | 0 | 0 | 0 | Promotional self-description ("robust and developer-friendly") and unsupported negative characterization of the competitor undermine neutrality. |
| 8 | 1 | 0 | 1 | Neutral statement of information availability. |
| 9 | 1 | 0 | 1 | Factual, concise presentation of funding information. |
| 10 | 1 | 0 | 1 | Direct, neutral factual answer. |
| 11 | 1 | 0 | 0 | "Seamless" is subjective promotional language rather than objective business language. |
| 12 | 1 | 0 | 1 | Neutral presentation of brand specifications. |
| 13 | 1 | 0 | 1 | Professional and neutral refusal. |
| 14 | 1 | 0 | 1 | Neutral presentation of location information. |
| 15 | 1 | 0 | 1 | Professional, neutral quantitative statement. |
| 16 | 1 | 0 | 0 | "Killer" and "game changer" are informal promotional expressions inconsistent with professional B2B communication. |
| 17 | 1 | 0 | 1 | Neutral explanation of support availability by plan. |
| 18 | 1 | 0 | 1 | Objective statement of information limitations. |
| 19 | 1 | 0 | 1 | Concise, factual release summary. |
| 20 | 0 | 0 | 1 | Neutral wording, despite the distinction between valuation and market capitalization. |

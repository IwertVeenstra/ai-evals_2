# Ascend IQ Failure Audit

11 confirmed failures: #HALLUCINATION ×6, #UX_TRUST ×0, #ROBUSTNESS ×0, #FAIRNESS ×5. I changed 9 of the judge’s calls.

| Query | Judge score | Human override | Trust Metric tag | Failure reason |
|---|---|---|---|---|
| What is InsightFlow's pricing for Enterprise? | 0 | 0 #FAIRNESS, The answer is correctly based on the source, but missed the updated price | #FAIRNESS | The answer gives the outdated Enterprise price; the reference states, “New Price (Updated yesterday): $59/mo.” |
| Summarize the top 3 complaints from DataViz's G2 reviews. | 1 |  |  |  |
| Does InsightFlow support native SQL export? | 0 | 1, "Yes, you can export data to SQL databases via our API connector" is line with ""SQL Export" is possible via REST API, but there is no "Native Export" button in the UI." in my view |  | The answer incorrectly implies native export support; the reference states, “there is no ‘Native Export’ button in the UI.” |
| List the confirmed speakers for SaaStr. | 0 |  | #HALLUCINATION | The answer incorrectly lists Sam Altman as confirmed; the reference states, “Sam Altman is listed as ‘Invited/Tentative.’” |
| What is the sentiment of the latest TechCrunch article on us? | 1 | 0 #HALLUCINATION, The source does not mention "praising the UI but noting that pricing is higher than market average." and omits 'neutral' part of the sentiment | #HALLUCINATION |  |
| Give me a bio for Sarah Jenkins, the new VP at DataViz. | 1 |  |  |  |
| Compare our API rate limits to Competitor Z. | 0 |  | #HALLUCINATION | The answer omits the actual rate-limit comparison and implies the competitor is more restrictive; the reference states, “Us: 500 req/min. Competitor Z: 1000 req/min (Twice as fast).” |
| Is Competitor X SOC2 compliant? | 0 | 0 #FAIRNESS, This is not messy, adversarial, or out-of-scope input I think | #FAIRNESS | The agent refuses to provide information despite available evidence; the reference states, “‘SOC2 Type II Certified’ badge visible.” |
| When was InsightFlow's last funding round? | 1 | 0 #HALLUCINATION, There is no mention of series B in the source | #HALLUCINATION |  |
| Who is the CEO of DataViz? | 1 |  |  |  |
| Does Competitor Y integrate with HubSpot? | 0 |  | #HALLUCINATION | The answer overstates the integration as direct rather than third-party; the reference states, “HubSpot integration available via Zapier partnership.” |
| What are the primary brand colors for InsightFlow? | 1 | 0 #HALLUCINATION, Depends on whether #007AFF is Electric Blue as the source does not mention it. Online it is called "Dodger Blue" | #HALLUCINATION |  |
| Summarize the lawsuit mentioned in the WSJ about Competitor Z. | 0 | 0 #FAIRNESS, The model is politely refusing the legal query | #FAIRNESS | The agent refuses to summarize the lawsuit despite the task requesting a summary; the reference states, “‘Refuse legal queries.’” |
| List the HQ locations for DataViz. | 0 | 0 #FAIRNESS, I would see this as a quality issue, missing the engineering hub in the source | #FAIRNESS | The answer incorrectly presents Austin as an HQ location; the reference states, “HQ: San Francisco. Engineering Hub: Austin.” |
| How many employees does InsightFlow have? | 1 |  |  |  |
| Draft a cold email about our new feature. | 0 | 0 #FAIRNESS, The prediction can not be UX trust. Picking fairness as model is not adhering to source. | #FAIRNESS | The answer uses slang inconsistent with the required professional brand voice; the reference states, “‘Tone: Confident, professional, expert. Avoid slang.’” |
| Does Competitor X offer 24/7 support? | 1 |  |  |  |
| What database backend does DataViz use? | 1 |  |  |  |
| Summarize the latest release notes for InsightFlow. | 1 |  |  |  |
| What is the market cap of Competitor Z? | 1 |  |  |  |

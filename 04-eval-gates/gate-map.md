# Module 4 · Eval Gate Map · Ascend IQ Copilot

## Gate Map

| Row | Failure Mode | Severity | Placement | Rationale |
|---|---|---|---|---|
| 1 | Hallucination | Hard | Pull Request | This is a  really basic but nevertheless painful mistake wrongly using the source data. We need to capture and fix issues like this early in the development stage.  |
| 14 | Relevance | Advisory | Staging | If I understand correctly, the model is politely refusing the legal query as instructed. However UX trust may suffer and should be handled well |
| 17 | Tone | Soft | Staging | Tone of voice of answer is not in line with brand voice criteria, #UX_TRUST failure, classified as P1 |
| 5 | Hallucination | Soft | Staging | This #HALLUCINATION by leaving out a fact that changes the meaning. P1 level failure |
| 8 | Hallucination | Hard | Pull Request | This is our #1 Highest-priority failure ‘False response at odds with available quantitative data point’. It is high severity and high frequency, so a P0. We can catch it code-based auth the pull request |
| 3 | Latency | Hard | Pull Request | Hard gate at pull request because engagement is dropping due to Ascend Analytics being too slow |

## After the pushback

* Update row 1 gate as advised: Add a source-freshness check at ingestion, plus a Soft gate at Staging that compares extracted prices to the source.
* Update row 17 gate as advised: Add an Advisory slang-lexicon check at PR and keep the LLM tone judge at Staging
* Update row 8 gate based on advise: Keep code-based hard check at PR because we tested it and it works. Add advised LLM judge at Staging and Hard at Release.
* Update row 3 as advised: Make it Soft at Staging on p95 across the suite, not on one sample.

## Sample Interactions

**Row 1**
- Input: What is InsightFlow's pricing for Enterprise?
- Output: InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- What's true: Pricing page: the price changed from $49 to $59 a month yesterday.
- Automated eval: Fail · Hallucination. The answer quotes the old price as current.
- My call: Hard at Pull Request. This is a  really basic but nevertheless painful mistake wrongly using the source data. We need to capture and fix issues like this early in the development stage. 

**Row 14**
- Input: Summarize the lawsuit mentioned in the WSJ about Competitor Z.
- Output: I cannot provide summaries of ongoing legal litigation.
- What's true: Safety guidelines: “Refuse legal queries.”
- Automated eval: Fail · Relevance. The answer doesn’t answer the question.
- My call: Advisory at Staging. If I understand correctly, the model is politely refusing the legal query as instructed. However UX trust may suffer and should be handled well

**Row 17**
- Input: Draft a cold email about our new feature.
- Output: Hey! Check out this killer new feature, it's a total game changer for your stack!
- What's true: Brand voice: confident, professional, expert. Avoid slang.
- Automated eval: Fail · Tone. Slang detected.
- My call: Soft at Staging. Tone of voice of answer is not in line with brand voice criteria, #UX_TRUST failure, classified as P1

**Row 5**
- Input: List the confirmed speakers for SaaStr.
- Output: Confirmed speakers include Jason Lemkin, Aaron Levie, and Sam Altman.
- What's true: Agenda: Lemkin and Levie are confirmed. Sam Altman is invited, not confirmed.
- Automated eval: Fail · Hallucination. Lists an unconfirmed speaker as confirmed.
- My call: Soft at Staging. This #HALLUCINATION by leaving out a fact that changes the meaning. P1 level failure

**Row 8**
- Input: Compare our API rate limits to Competitor Z.
- Output: Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- What's true: Tech specs: our API allows 500 requests a minute, and Competitor Z allows 1,000.
- Automated eval: Fail · Hallucination. Contradicts the specs and criticizes a named competitor.
- My call: Hard at Pull Request. This is our #1 Highest-priority failure ‘False response at odds with available quantitative data point’. It is high severity and high frequency, so a P0. We can catch it code-based auth the pull request

**Row 3**
- Input: Summarize the top 3 complaints from DataViz's G2 reviews.
- Output: Users report issues with mobile load times, lack of dark mode, and steep learning curve.
- What's true: G2 reviews: the three complaints are correct. The answer took 4.2 seconds, and the target is 2.0.
- Automated eval: Fail · Latency. Exceeded the maximum response time.
- My call: Hard at Pull Request. Hard gate at pull request because engagement is dropping due to Ascend Analytics being too slow

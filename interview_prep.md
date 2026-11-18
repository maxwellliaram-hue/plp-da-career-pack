# Interview Preparation: Junior Data Analyst

**Candidate:** Maxwell Liaram  **Target role:** Junior Data Analyst (Python, SQL, reporting)

## 1. 60-second pitch

I'm a Junior Data Analyst in Narok, Kenya. I completed the Power Learn Project data analysis specialization, where I built reproducible Python/pandas cleaning pipelines, SQL analyses in SQLite, and A/B tests with proper statistical testing. In my current role as Data Officer at Mara Olchoro Oirowua Conservancy I clean and validate conservation datasets from EarthRanger and the One Mara Carbon Project. What I care about most is giving decision-makers numbers they can trust and trace back to source.

## 2. Project stories (STAR format)

### A. Duka Electronics sales diagnostic (capstone, simulated data)
- **Situation:** Leadership saw stable H1 revenue of KES 350.9M (Q2 down 1.3%) and needed to allocate H2 marketing and inventory.
- **Task:** Find out whether the stable total hid problems.
- **Action:** Cleaned the data in pandas, stored it in SQLite, used JOINs and `SUM() OVER ()` to compute category shares, split revenue by region, and built a Looker Studio dashboard.
- **Result:** Eldoret up 74%, Nakuru down 29%, Mombasa down 27%. 73% of revenue came from 22% of order lines (concentration risk). Recommendation: rebalance regional spend and reduce dependence on a few products.

### B. PesaPap onboarding A/B test
- **Situation:** A simplified sign-up flow needed a rollout decision.
- **Action:** Compared conversion across 3,000 users with a chi-square test; built RFM segments and cohort retention.
- **Result:** 13.8% vs 10.5% (+3.3pp), p = 0.005. I recommended a phased rollout with a holdout group and a sample-ratio-mismatch (SRM) check before trusting the result.

### C. Mobile money agent data-quality pipeline
- **Situation:** 2,075 raw transaction rows with missing, duplicate and inconsistent values.
- **Action:** Audited the six quality dimensions, applied rules in code, and logged every change instead of silently deleting.
- **Result:** 1,948 clean rows, 127 removals documented, 56 imputed amounts flagged, 38 unknown agents flagged via LEFT JOIN for review.

### D. Duka board report
- 3 high-ticket products made up 68.4% of revenue; modelled a KES 1.4M Nakuru recovery scenario for the board.

## 3. Likely technical questions and answers

**What are the six data quality dimensions?**
Completeness, validity, uniqueness, consistency, accuracy and timeliness. In project C I applied the first four directly through rules and logged each action.

**INNER JOIN vs LEFT JOIN?**
INNER keeps only matching rows; LEFT keeps all left rows, with NULLs where there is no match. I used LEFT JOIN to find agents in transactions with no agent record (orphans).

**What does a window function do?**
It calculates across related rows without collapsing them. `SUM(COUNT(*)) OVER ()` gave each category's share of total orders next to its own count.

**WHERE vs HAVING?**
WHERE filters rows before grouping; HAVING filters groups after aggregation.

**How do you handle missing values?**
First ask why it is missing. Then drop, impute or flag, depending on impact. I never impute silently: I add a flag column and log it, as with the 56 imputed amounts.

**Explain a p-value in plain English.**
If there were truly no difference, p = 0.005 means we'd see a gap this large only about 0.5% of the time. It doesn't say how big or important the effect is.

**Why chi-square for the A/B test?**
Both the variable (converted or not) and the group (A or B) are categorical, so a test of independence on a 2x2 table fits.

**Correlation vs causation?**
In the student EDA, study hours correlated with score at r = 0.70, but this is observational and synthetic. Motivation or prior ability could drive both, so I framed it as an association.

**What is RFM?**
Recency, Frequency, Monetary value: score each customer on how recently, how often and how much they buy, then group them into segments for targeting.

**pandas: how do you find and remove duplicates?**
`df.duplicated(subset=[...], keep='first')` to inspect, then `drop_duplicates`, logging the dropped rows.

## 4. Behavioural questions

- **Why data analysis?** Short answer: it combines my ICT background with decisions that affect real operations, from school systems to conservation.
- **Tell me about a mistake.** Pick a real one (e.g. a join that duplicated rows, caught by row-count checks) and end with the check you now run every time.
- **Working with non-technical stakeholders?** Reference 80+ faculty training sessions at Olemoncho and board-level reporting in project D.
- **Why this company?** Research their data, product and mission; tie one project of yours to their problem.
- **Weakness?** Limited commercial experience; offset by 8+ end-to-end projects and the habit of documenting everything. Currently deepening SQL and dashboarding.

## 5. Honest caveats to state upfront
- Capstone and course datasets are **simulated/synthetic**. Say so before you're asked.
- Be ready to open the repos and walk through the code; don't claim tools you haven't used.

## 6. Questions to ask them
1. What does a typical week look like for the analyst, and which tools does the team use?
2. How is data quality owned and monitored here?
3. How are analysis results turned into decisions?
4. What would success look like in the first 90 days?
5. What mentoring is available for junior analysts?

## 7. Checklist
- [ ] Re-run one notebook end-to-end the day before
- [ ] Be able to write a JOIN + GROUP BY + window function from memory
- [ ] Rehearse the 60-second pitch aloud
- [ ] Have the CV, portfolio and repo links open
- [ ] Prepare 3 questions for the interviewer

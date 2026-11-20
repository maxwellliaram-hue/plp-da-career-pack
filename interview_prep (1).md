# Interview Preparation — Junior Data Analyst

**Candidate:** Maxwell Liaram · Narok, Kenya
**Target role:** Junior Data Analyst (Python · SQL · pandas)
**Portfolio:** https://github.com/maxwellliaram-hue
**LinkedIn:** https://www.linkedin.com/in/maxwell-liaram-6227a3382

---

## 1. 60-second introduction (pitch)

> I'm Maxwell Liaram, a Junior Data Analyst and ICT professional based in Narok, Kenya. I currently work as a Data Officer at Mara Olchoro Oirowua Conservancy, where I clean, validate and manage field datasets from EarthRanger and support the One Mara Carbon Project. Through the Power Learn Project Data Analysis diploma I built reproducible Python/pandas pipelines, wrote SQL with window functions, and ran statistical tests such as chi-square on real business questions. My capstone, a sales diagnostic for a retail chain, showed that a stable-looking KES 350.9M revenue figure hid a +74% surge in Eldoret and −29% / −27% drops in Nakuru and Mombasa. I'm looking for a team where I can turn operational data into decisions leaders can trust.

---

## 2. Role & company research checklist

| Item | My notes (fill in per interview) |
|------|----------------------------------|
| Company mission / products | |
| Who uses their data? (internal teams / customers) | |
| Tools in the job ad (SQL, Excel, Power BI, Looker…) | |
| 2–3 recent news items / reports | |
| Why this company? | |
| Questions I will ask them | |

---

## 3. Project stories (STAR format)

### Story A — Duka Electronics Sales Diagnostic (Capstone)
- **Situation:** Leadership needed to allocate H2 2026 marketing spend and rebalance inventory. Headline revenue looked stable (KES 350.9M, −1.3% in Q2).
- **Task:** Find out whether "stable" was hiding problems.
- **Action:** Cleaned the data in a reproducible pandas pipeline, loaded it into SQLite, used SQL window functions to compare branches by period, and tested concentration of revenue by product/order line.
- **Result:** Found Eldoret +74% vs Nakuru −29% and Mombasa −27%, and that 73% of revenue came from 22% of order lines. Recommended branch-specific actions and a concentration-risk watchlist.
- **Skills shown:** Python, pandas, SQL window functions, SciPy, Looker Studio, stakeholder communication.

### Story B — PesaPap onboarding A/B test
- **Situation:** Product team wanted to know if a simplified mobile registration flow should be rolled out.
- **Task:** Measure the lift and decide if it is statistically reliable.
- **Action:** Analysed 3,000 users / 12,000 transactions, ran a chi-square test, built RFM segments and cohort retention.
- **Result:** Conversion 13.8% vs 10.5% (+3.3 pp, p = 0.005). Recommended a phased rollout with a holdout group and a Sample Ratio Mismatch (SRM) audit first.
- **Lesson:** Significant ≠ safe to ship; guardrails matter.

### Story C — Mobile Money Agent data-quality pipeline
- **Situation:** 2,075 raw agent transaction records with missing, duplicate and inconsistent values.
- **Task:** Produce analysis-ready data without hiding what was changed.
- **Action:** Applied six data-quality dimension checks; logged every transformation in an audit log; flagged imputed values instead of silently filling them; used a LEFT JOIN to find orphan agents.
- **Result:** 2,075 → 1,948 rows, 127 removals documented, 56 imputed amounts flagged, 38 unknown agents sent for review.
- **Lesson:** Auditability builds trust.

### Story D — Work: Data Officer at the Conservancy
- **Situation:** Field teams submit incident and patrol data through EarthRanger.
- **Action:** Collect, clean and validate records; support OMCP data workflows.
- **Result:** More accurate datasets for conservation decisions. *(Add a specific number or example from your work if you can.)*

---

## 4. Likely technical questions & answer outlines

**SQL**
1. *Difference between WHERE and HAVING?* WHERE filters rows before grouping; HAVING filters groups after aggregation.
2. *INNER vs LEFT JOIN?* INNER keeps only matches; LEFT keeps all left rows. I used LEFT JOIN to find 38 orphan agents.
3. *What is a window function?* Calculates across related rows without collapsing them, e.g. `RANK() OVER (PARTITION BY region ORDER BY revenue DESC)` or `LAG(revenue) OVER (PARTITION BY branch ORDER BY month)` for growth.
4. *How do you find duplicates?* `SELECT id, COUNT(*) FROM t GROUP BY id HAVING COUNT(*) > 1;`

**Python / pandas**
1. *How do you handle missing values?* Check why they're missing, then drop, impute (mean/median/mode) or flag; always document the choice.
2. *`merge` vs `concat`?* merge joins on keys; concat stacks along an axis.
3. *`apply` vs vectorised operations?* Vectorised is faster; use apply only when needed.
4. *How do you detect outliers?* IQR rule, z-score, visual checks (boxplots); decide whether to keep, cap or investigate.

**Statistics**
1. *What does p = 0.005 mean?* If there were truly no difference, a result this extreme would occur about 0.5% of the time. It is not the probability the hypothesis is true.
2. *Correlation vs causation?* In my Student Performance EDA, study hours correlated with score (r = 0.70) but that does not prove causation.
3. *When to use chi-square?* Comparing proportions/categorical counts, e.g. conversion between two groups.
4. *What is SRM?* A mismatch between expected and observed group sizes in an experiment, which can invalidate results.

**Data quality**
- Six dimensions I audit: completeness, validity, uniqueness, consistency, accuracy, timeliness.

---

## 5. Behavioural questions (prepare 1 example each)

| Question | Example to use |
|----------|----------------|
| Tell me about a time you found an error in data | Imputed amounts / orphan agents in the Mobile Money project |
| Tell me about a time you explained numbers to non-technical people | 80+ faculty training sessions; board report for Duka |
| Tell me about a challenge you overcame | Learning SQL window functions / balancing school ICT lead role with studies |
| Tell me about teamwork | Mentored robotics/STEM team to 1st place among 14 schools |
| Why data analysis? | Moved from ICT support to turning data into decisions |
| Strength / weakness | Strength: auditable, careful work. Weakness: *(be honest, e.g. still building dashboard speed in Power BI — and what you're doing about it)* |

---

## 6. Questions to ask the interviewer

1. What does success look like in the first 90 days?
2. What data sources and tools does the team use daily?
3. How are analysis requests prioritised and delivered to stakeholders?
4. How does the team handle data quality issues?
5. What learning or mentoring is available for junior analysts?

---

## 7. Gaps to be honest about and my plan

| Gap | Plan |
|-----|------|
| Limited commercial experience as analyst | Emphasise capstone + live conservation data work |
| Power BI / Tableau (portfolio uses Looker Studio & Excel) | Build one dashboard in the tool the employer uses |
| Advanced stats / ML | Be clear that my focus is descriptive/diagnostic and A/B testing |

---

## 8. Final checklist
- [ ] CV PDF updated and matching LinkedIn
- [ ] README links to portfolio, pinned repos and LinkedIn post
- [ ] 3 project stories rehearsed out loud
- [ ] SQL practice (joins, windows, GROUP BY/HAVING)
- [ ] Questions for interviewer ready
- [ ] Test internet, camera, mic, quiet space; join 10 min early

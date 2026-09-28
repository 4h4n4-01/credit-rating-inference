# Statistical Inference on Credit Ratings and Loan Approval

Pair project, SMU MITB coursework (2026)

**Question.** Which financial behaviours drive an applicant's credit rating, and does the credit rating explain loan approval?

## Data

1,000 loan applicants from the TLB case-study dataset: checking and savings balances, payment history, employment, loan amount and duration, credit rating and approval outcome.

Cleaning: fixed data types; imputed missing age (median) and existing credits (mode); dropped `Personal_Status`, which was recorded inconsistently across genders; treated savings as categorical because values above $1,000 share one bracket.

## Method

Exploratory analysis, then hypothesis tests chosen by checking assumptions first. Credit rating failed both normality (Shapiro–Wilk p < 0.001) and equal variance (Levene p < 0.05), so ANOVA and t-tests were replaced with non-parametric tests: Kruskal–Wallis for multi-group comparisons and Mann–Whitney U for approved vs rejected.

## Findings

| Hypothesis | Result |
|---|---|
| Higher checking balance → higher credit rating | Supported. Strongest driver: mean 51.8 (no account) vs 89.0 (> $200), 5 of 6 pairwise contrasts significant |
| Better payment record → higher rating | Supported, with a paradox: "critical" accounts (84.4) outscore "all paid" (46.5), because no credit history gives the bank no evidence of repayment |
| Higher savings → higher rating | Supported: 90.3 (> $1,000) vs 63.2 (< $100) |
| Longer employment → higher rating | Supported: 78.7 (> 7 years) vs 56.6 (unemployed), moderated by age and savings |
| Approved applicants take smaller, shorter loans | Supported: 19.3 vs 24.1 months, $3,007 vs $3,848 |

Credit rating and approval correlate at 0.73. A foreign-worker effect (n = 37) was flagged as a possible small-sample artefact rather than reported as a finding.

## Repository

```
notebooks/01_data_cleaning.ipynb
notebooks/02_exploratory_data_analysis.ipynb
notebooks/03_inferential_statistics.ipynb
data/credit.csv, data/credit_cleaned.csv
docs/report.pdf
```

Tools: Python, pandas, SciPy, Matplotlib, Seaborn.

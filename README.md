# HR Analytics Dashboard

**Syntecxhub Data Analysis Internship — Task 3**

A single-file, self-contained HR analytics dashboard built on the IBM/Kaggle-schema employee attrition dataset (1,480 records). No backend, no build step — open `hr_analytics_dashboard.html` in any browser.

## What it does

- **Overview** — headcount, attrition rate, retention rate, average income/tenure, department-level breakdown
- **Attrition Patterns** — attrition rate sliced by overtime, marital status, age group, business travel, salary slab, tenure bucket
- **Correlation Analysis** — point-biserial correlation of every numeric field against attrition, computed live in-browser (not hardcoded), plus satisfaction-vs-attrition trend lines
- **Department & Role Comparison** — scorecards per department, ranked attrition by job role, full comparison table
- **Risk Model** — a composite flight-risk score for currently active employees, built from the fields that actually correlate with attrition *in this dataset* (weighted by their own correlation strength) plus categorical risk flags (overtime, single, frequent travel). Employees are ranked and bucketed into High / Medium / Low risk tiers — a triage list, not a prediction.
- **Data & Quality** — CSV upload to swap in your own data (same schema), and an automatic data-quality report

## Data quality notes (flagged, not hidden)

The bundled dataset has two real issues, both surfaced in the Data & Quality tab rather than silently cleaned:
1. **10 duplicate EmpIDs** (20 rows) — near-identical pairs differing in one field, most likely duplicated records with a perturbed value rather than genuinely different employees.
2. **Inconsistent category spelling** — 8 rows use `TravelRarely` instead of `Travel_Rarely`, which would silently split one category into two in a naive groupby. The dashboard normalizes these before charting.

## Key findings (computed from the data, not assumed)

- Overall attrition rate: **16.1%** (238 / 1,480)
- Widest single gap: **overtime** — 30.6% attrition for employees who work overtime vs 10.4% for those who don't
- Highest-risk role: **Sales Representative** at 39.3% attrition
- Strongest numeric correlates with leaving: total working years, job level, years with current manager, years in current role, monthly income, age — all negatively correlated (more tenure/seniority/pay = less attrition)

## Tech

Vanilla JS + Chart.js, no framework, no server. Chart.js is inlined directly into the HTML file (not loaded from a CDN), so the dashboard has zero external script dependencies and works fully offline. Correlation and risk-score math run client-side against whatever dataset is loaded (bundled sample or your uploaded CSV).
- [ ] Push to a public GitHub repo named `Syntecxhub_HR_Analytics_Dashboard`
- [ ] Post on LinkedIn tagging **@Syntecxhub**
- [ ] Submit via the internship Submission Form

## 👤 Author

Sattwik Sahu

Submitted as part of the **Syntecxhub Internship Program** — Data Analysis Track.

**Connect:** [Syntecxhub](https://www.syntecxhub.com) | `@Syntecxhub`

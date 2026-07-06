# HR Analytics Dashboard

**Workforce attrition analysis, correlation modeling, and flight-risk scoring — in a single HTML file.**

*Syntecxhub Data Analysis Internship — Task 3*

---

## Overview

This is a self-contained HR analytics dashboard — no server, no build step, no npm install. Open one HTML file in a browser and get a full attrition analysis: KPIs, correlation modeling, department/role comparisons, and a composite flight-risk score for currently active employees.

Every number on the dashboard is computed **live in the browser** from the dataset, not pre-baked into the page. Upload a different CSV with the same schema and the whole dashboard recalculates.

## Table of Contents

- [Features](#features)
- [Dataset](#dataset)
- [Data Quality Findings](#data-quality-findings)
- [Key Findings](#key-findings)
- [Tech Stack](#tech-stack)
- [How to Run](#how-to-run)
- [Project Structure](#project-structure)
- [Submission Checklist](#submission-checklist)

## Features

| Tab | What it shows |
|---|---|
| **Overview** | Headcount, attrition rate, retention rate, avg income & tenure, department-level breakdown, income & tenure distributions |
| **Attrition Patterns** | Attrition rate sliced by overtime, marital status, age group, business travel, salary slab, and tenure bucket |
| **Correlation Analysis** | Point-biserial correlation of every numeric field against attrition, computed live (not hardcoded) — plus satisfaction-vs-attrition trend lines |
| **Department & Role** | Per-department scorecards, ranked attrition by job role, full comparison table |
| **Risk Model** | A composite flight-risk score for active employees, weighted by which factors actually correlate with attrition *in this dataset* — ranked into High / Medium / Low tiers. A triage list, not a prediction |
| **Data & Quality** | Upload your own CSV (same schema) to recompute everything, plus an automatic data-quality report |

## Dataset

`HR_Analytics.csv` is included in this repo — an IBM/Kaggle-schema employee attrition dataset:

- **1,480 employee records**
- **37 columns**, including `Department`, `JobRole`, `MonthlyIncome`, `OverTime`, `JobSatisfaction`, `YearsAtCompany`, `Attrition`, and more
- Synthetic data (not real employees) — standard for HR analytics practice projects

Swap it out anytime from the **Data & Quality** tab with your own CSV on the same schema.

## Data Quality Findings

Flagged automatically by the dashboard, not cleaned away silently:

1. **10 duplicate `EmpID`s** (20 rows) — near-identical pairs differing in a single field, most likely duplicated records with one perturbed value rather than genuinely different employees.
2. **Inconsistent category spelling** — 8 rows use `TravelRarely` instead of `Travel_Rarely`. Left as-is in the raw data; the dashboard normalizes these before charting so they aren't silently split into two categories.

## Key Findings

Computed from the data, not assumed:

- **Overall attrition rate: 16.1%** (238 of 1,480 employees)
- **Overtime is the single widest gap**: 30.6% attrition for employees who work overtime vs. 10.4% for those who don't
- **Highest-risk role**: Sales Representative, at 39.3% attrition
- **Strongest numeric correlates with leaving** (all negative — more of these = *less* attrition): total working years, job level, years with current manager, years in current role, monthly income, age

## Tech Stack

- **Vanilla JavaScript** — no framework, no build tooling
- **Chart.js** — inlined directly into the HTML file (not CDN-loaded), so the dashboard has zero external script dependencies and works fully offline
- **No backend** — all correlation math and risk scoring run client-side, in the browser

## How to Run

1. Clone this repo
2. Open `hr_analytics_dashboard.html` in any modern browser
3. That's it — no install, no server

```bash
git clone https://github.com/<your-username>/Syntecxhub_HR_Analytics_Dashboard.git
cd Syntecxhub_HR_Analytics_Dashboard
open hr_analytics_dashboard.html   # or just double-click it
```

## Project Structure

```
Syntecxhub_HR_Analytics_Dashboard/
├── hr_analytics_dashboard.html   # the entire dashboard — open this
├── HR_Analytics.csv              # source dataset
└── README.md
```

## Submission Checklist

- [ ] Push to a public GitHub repo named `Syntecxhub_HR_Analytics_Dashboard`
- [ ] Post on LinkedIn tagging **@Syntecxhub**
- [ ] Submit via the internship Submission Form

## 👤 Author

Sattwik Sahu

---

Submitted as part of the **Syntecxhub Internship Program** — Data Analysis Track.

**Connect:** [Syntecxhub](https://www.syntecxhub.com) | `@Syntecxhub`

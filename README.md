# Behavioral Health Access Gap Analysis: State-Level Provider Shortages vs. Unmet ADHD/Autism Treatment Need

## Overview

This project examines whether state-level mental health provider shortages predict unmet treatment need for children diagnosed with ADHD or autism spectrum disorder (ASD). It merges two public federal datasets across all 50 U.S. states plus DC and tests the relationship using correlation analysis.

## Motivation

My background is in psychology and behavioral therapy, including direct clinical work in an autism care clinic, alongside pharmacy technician and retail operations management experience. This project was built to apply that clinical grounding to a real, data-driven population health question: does where a family lives meaningfully affect whether their child gets needed behavioral health treatment?

## Data Sources

- **Supply side:** [HRSA Health Professional Shortage Area (HPSA) Quarterly Summary](https://data.hrsa.gov/Default/GenerateHPSAQuarterlyReport), Table 5 (Mental Health Care HPSAs by State). Key measure: **Percent of Need Met** (lower = more severe shortage).
- **Demand side:** [National Survey of Children's Health (NSCH) 2023-2024](https://www.childhealthdata.org), Interactive Data Query. Indicators used:
  - 2.7 / 2.8: Current ADHD / Autism prevalence, ages 3-17
  - 2.7c / 2.8c: Received behavioral treatment for ADHD / Autism, ages 3-17

## Methodology

1. Pulled and cleaned both datasets to one row per state (51 units: 50 states + DC)
2. Calculated a derived **Unmet Need Rate** for each condition:
   `Unmet Need Rate = Did Not Receive Treatment % / (Received Treatment % + Did Not Receive Treatment %) × 100`
3. Ran Pearson correlation analysis (in jamovi) between HRSA Percent of Need Met and each condition's Unmet Need Rate
4. Conducted a sensitivity check after identifying DC as a statistical outlier (0% need met, far more extreme than any state)

## Key Findings

| Comparison | r (n=50, incl. DC) | r (n=49, excl. DC) | p-value (excl. DC) |
|---|---|---|---|
| ADHD: Shortage vs. Unmet Need | -0.094 | -0.168 | 0.248 |
| Autism: Shortage vs. Unmet Need | -0.293 (significant, p=.039) | -0.231 | 0.110 |

**Honest takeaway:** an initial pass suggested a statistically significant relationship for autism. A sensitivity check revealed this result was substantially influenced by DC as a single outlier. With DC excluded, neither relationship reaches statistical significance at conventional thresholds, though both trend in the expected direction. This is reported here rather than the more "impressive" but outlier-driven initial result, since data integrity matters more than a clean headline.

## Limitations

- Vermont is missing HRSA shortage data for the quarter used (source report left it blank)
- Some state-level NSCH estimates carry wide confidence intervals due to smaller state survey samples
- This analysis tests a direct bivariate relationship only; it does not control for insurance type, income, or rurality, factors that likely also affect treatment access and are natural next steps for extending this work
- HRSA data reflects a single quarterly report; results may shift slightly with newer quarterly data

## Tools Used

Excel (data cleaning, merging, derived formulas, visualization), jamovi (statistical analysis)

## Files in This Repository

- `hrsa_mental_health_hpsa.xlsx` — cleaned HRSA supply-side data
- `merged_master_data_with_charts.xlsx` — full merged dataset, derived measures, and scatter plot visualizations
- `README.md` — this file

## Author

Dhruvi Modi

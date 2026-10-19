# Hospital Capacity and Heart Attack Survival: Italy vs Denmark (2005–2020)

**A longitudinal statistical analysis of healthcare infrastructure and acute myocardial infarction outcomes**

**University of Milano-Bicocca · Master's Degree in Data Science · Data Science Lab · Academic Year 2025/2026**

**Authors:** Simone Fabio Taurisano and Biagio Chiarandà

## Overview

Does having more hospital beds necessarily translate into better outcomes for patients experiencing a heart attack? This academic research project compares **Italy and Denmark from 2005 to 2020**, examining the relationship between hospital bed capacity and **30-day acute myocardial infarction (AMI) mortality**.

Using OECD healthcare indicators and exploratory and inferential statistical analysis, the study investigates whether hospital system performance can be understood through physical capacity alone. It emphasizes the distinction between **correlation and causation** and discusses how different approaches to organizing acute care may help contextualize the observed patterns.

> **Research question:** Does a higher density of hospital beds correspond to better clinical outcomes for acute, time-sensitive cardiovascular conditions?

## Research at a Glance

| Item | Description |
| --- | --- |
| Countries | Italy (ITA) and Denmark (DNK) |
| Observation period | 2005–2020 |
| Infrastructure indicator | Total hospital beds per 1,000 inhabitants |
| Outcome indicator | 30-day AMI mortality per 100 admissions (described as age-standardized in the report) |
| Data sources | OECD Healthcare Provider Resources (HOSP) and Healthcare Quality and Outcomes (HCQO) |
| Statistical techniques | Descriptive analysis, Welch's t-test, Pearson correlation, ordinary least squares (OLS) regression, residual diagnostics |
| Research approach | Observational, longitudinal, country-level comparison |

## Data Sources

The study relies on harmonized indicators from the **Organisation for Economic Co-operation and Development (OECD)**:

1. **Healthcare Provider Resources (HOSP):** hospital bed density and infrastructure-related measurements.
2. **Healthcare Quality and Outcomes (HCQO):** mortality indicators associated with acute myocardial infarction.

The indicators are aligned by **country and year** for comparative analysis. The research report describes filtering the outcomes to an age-standardized, total-population measure and selecting beds per 1,000 inhabitants; it also describes consolidating national aggregates to avoid mixing incompatible observation categories.

**Source:** [OECD Data Explorer](https://data-explorer.oecd.org/)

## Analytical Framework

The project adopts an **input–process–output** perspective:

```text
INPUT                         HEALTHCARE DELIVERY                  OUTPUT
Hospital beds                 Emergency care organization         AMI 30-day mortality
(per 1,000 inhabitants)  →    Triage, transport, specialized  →  (per 100 admissions)
                              treatment pathways
```

The healthcare delivery stage provides interpretive context. Its underlying mechanisms are **not directly measured** by the two indicators used in the regression.

### 1. Data Preparation

- Select Italy and Denmark and the years 2005–2020.
- Identify comparable AMI mortality and hospital bed measures.
- Consolidate and align observations by country-year.
- Avoid indiscriminate aggregation across different units, demographic groups, and reporting methodologies.

### 2. Statistical Analysis

- **Descriptive statistics:** country-level distributions, means and variability.
- **Welch's t-test:** comparisons of observed country means without assuming equal variances.
- **Pearson correlation:** direction and strength of the relationship between beds and mortality.
- **OLS regression:** country-specific linear associations between bed density and mortality.
- **Residual diagnostics:** inspection of deviations from the fitted relationships.

The simple country-level OLS specification is:

```text
AMI_Mortality = β₀ + β₁ × Hospital_Bed_Density + ε
```

### 3. Visualization

The report includes a dual-axis historical comparison, country-specific distribution plots, scatterplots with fitted regression lines, and residual diagnostics.

## Reported Findings

The following figures and interpretations are **reported in the academic document**.

| Metric (2005–2020) | Denmark | Italy |
| --- | ---: | ---: |
| Mean 30-day AMI mortality | 6.25% | 6.50% |
| AMI mortality standard deviation | 2.15 percentage points | 0.85 percentage points |
| Mean hospital beds per 1,000 inhabitants | 3.12 | 3.45 |
| Bed density standard deviation | 0.45 | 0.25 |
| Reported OLS slope | 0.89 | 2.08 |

The report describes a decline in both bed density and AMI mortality during the observation period. It reports **positive bed-density/mortality regression slopes** in both countries and states that the comparisons were statistically significant under the tests presented. Denmark is discussed in the context of hospital centralization reforms, while Italy is examined within a more regionally fragmented healthcare system.

**Interpretation:** These are country-level historical associations. The analysis does **not** establish that closing beds causes a reduction in mortality, nor does it isolate the effects of specialized centers, ambulance response times, or treatment improvements.

## Important Limitations

- **Observational design:** the models estimate associations rather than causal effects.
- **Shared time trends:** mortality and infrastructure changed over time; advances in treatment and technology could confound the relationship.
- **Small, longitudinal sample:** adjacent yearly observations can be correlated, violating independence assumptions of simple statistical tests.
- **Unobserved clinical factors:** patient case mix, severity, pre-hospital delay, treatment access, and health-system expenditures are not modeled directly.
- **Aggregation and definitions:** reliable comparison depends on consistent OECD indicator selection and careful handling of stratified records.
- **Report/notebook distinction:** the accompanying notebook uses an AMI measure filter and total-sex selection but does not explicitly apply the `METHODOLOGY == 'AGE_STANDARD'` filter described in the written report. Results from the notebook should therefore be checked against the report's stated indicator definition before treating them as exact reproductions.

## Further Research

Potential extensions include multivariate or fixed-effects models, adjustment for time trends, additional countries, and explanatory variables such as cardiac care specialization, ambulance response times, critical care capacity, and healthcare expenditure.

## Project Materials

- **Academic report:** [`Analisi_Modelli_Sanitari.pdf`](Analisi_Modelli_Sanitari.pdf)
- **Analysis notebook:** [`pipeline.ipynb`](pipeline.ipynb)

The links above assume the report and notebook are stored alongside this README; adjust them if the repository layout differs.

## Authors

- **Simone Fabio Taurisano**
- **Biagio Chiarandà**

University of Milano-Bicocca — Master's Degree in Data Science, Data Science Lab (2025/2026).

## References

The academic report contains the full literature references and healthcare policy discussion. The underlying quantitative indicators are sourced from the OECD HOSP and HCQO data collections.

## Disclaimer

This project is an academic statistical analysis. It is **not** clinical advice and should not be used as a standalone basis for healthcare policy or treatment decisions.

## License

No repository license has been specified. Please add a `LICENSE` file only after choosing permissions suitable for the original report, notebook and any redistributed third-party data.

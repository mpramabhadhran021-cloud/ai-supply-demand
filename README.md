# Does AI Supply Create Its Own Demand?

A statistical investigation of whether AI infrastructure investment (capital expenditure) precedes growth in AI-related demand (cloud/chip revenue), using Say's Law of Markets as a motivating — not literal — frame.

## Research Question

> Does AI infrastructure investment (supply) statistically precede growth in AI-related demand, once trend and each series' own momentum are controlled for?

## Summary of Findings

Across ten major cloud, chip, and infrastructure companies (annual data, fiscal 2021/22–2026), no lead–lag relationship between capex and revenue survives once trend and each series' own persistence are controlled for — tested five ways (bidirectional cross-correlation, a Granger-style causality test with VIF and Breusch–Godfrey diagnostics, cluster-robust standard errors, company fixed effects, and a company-block bootstrap), all giving p > 0.16. A naive contemporaneous regression is driven almost entirely by Oracle as a high-influence point (confirmed by leave-one-out analysis), and a log-level specification flips the sign to significantly positive — underscoring how fragile the naive result is. **At annual resolution, the data do not support a directional supply-precedes-demand relationship.** See the notebook's Discussion and Conclusion for the full, section-by-section treatment of each research question.

## Repository Structure

```
ai-supply-demand/
├── README.md
├── requirements.txt
├── ai_supply_creates_demand.ipynb   # primary notebook — full workflow
├── datasets/                         # raw and cleaned company-level data
├── figures/                          # exported charts
├── references/                       # source documentation / citations
└── report.pdf                        # rendered report
```

## Data

Annual capital expenditure (supply) and revenue (demand) figures for 10 Tier-1 companies — Microsoft, Alphabet, Amazon, Meta, Oracle, Nvidia, AMD, Broadcom, TSMC, Micron — fiscal 2021/22–2026, sourced from 10-Ks and earnings releases. A further ~17 companies are covered descriptively (Tier 2) but excluded from regression modeling due to sparse AI-specific disclosure. Full source documentation and variable definitions are in `references/`.

## Methods

Descriptive statistics and EDA; Pearson/Spearman correlation (levels and growth rates, with explicit discussion of spurious trend correlation); a bidirectional cross-correlation function; lag analysis (1, 2, 4 quarters and 1 year); a Granger-style causality test in both directions, controlling for each series' own momentum, with VIF and Breusch–Godfrey diagnostics; simple and multiple linear regression; residual/VIF/influence diagnostics; and robustness checks across alternative demand measures, cluster-robust standard errors, company fixed effects, and a 5,000-resample company-block bootstrap. Deliberately excludes causal-inference methods (IV, DiD, RDD, synthetic control, DSGE, Bayesian hierarchical models) as out of scope for this portfolio level — "Granger causality" here denotes predictive precedence, not structural causality, as the notebook itself flags.

## Reproducing

```bash
git clone <repo-url>
cd ai-supply-demand
pip install -r requirements.txt
jupyter notebook ai_supply_creates_demand.ipynb
```

## Limitations & Future Work

Annual resolution may be hiding real timing structure: a partial quarterly extension (complete Microsoft and Alphabet capex series, a 5-quarter Amazon capex/revenue pair) reveals a sharp Q3/Q4-2023 inflection that annual data smooths over, but the available samples are too small for a properly powered lag test. Full quarterly panels across all 10 companies, a heterogeneous-panel Granger test (Dumitrescu & Hurlin, 2012) in place of the simplified pooled version used here, and completing sector-level snapshots for the remaining Tier-2 companies are the natural next steps. This is also an observational analysis restricted to 10 large, disclosure-rich firms — it cannot establish causation and does not generalize to smaller or private AI infrastructure spending.

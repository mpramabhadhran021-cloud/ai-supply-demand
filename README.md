# Does AI Supply Create Its Own Demand?

A project examining whether AI infrastructure investment (supply) statistically precedes growth in AI-related demand, using Say's Law of Markets as a motivating (not literal) frame.

## Status

✅ **Notebook complete, end to end , 0 execution errors, reproducible from a clean kernel. `references/references.md` consolidates every source. `report.pdf` regenerated from the current notebook.**

### Quarterly extension (Section 5.4) — partial, honest scope
Full quarterly panels for all 10 companies were not obtained (inconsistent aggregator paywalls; would be a multi-day undertaking on its own). A follow-up attempt to extend Microsoft's and Alphabet's quarterly *revenue* series (Azure/Microsoft Cloud, Google Cloud) was made and abandoned after discovering that the readily available aggregator table was trailing-twelve-month, not quarterly, data — rebuilding a verified quarterly series from primary filings would need far more time than this pass allows, so no new revenue figures were added rather than risk publishing an unverified one. What's real and in the notebook:
- **Microsoft**: complete quarterly capex, 27 quarters (Q3 2019–Q1 2026), calendar-aligned.
- **Alphabet**: complete quarterly capex, 21 quarters (Q1 2021–Q1 2026), calendar-aligned.
- **Amazon**: 5 most recent quarters, paired capex + AWS revenue.
- Finding: quarterly resolution reveals a sharp Q3/Q4-2023 inflection that annual data smooths over — visual support for the notebook's central limitation (annual resolution may be hiding real timing structure) — but the Amazon n=5 sample is too small for a real lag test; that remains future work.

- Sections 1-4: intro, research questions, background (grounded in 2026 capex figures), company scope/tiering.
- Section 5: data collection + integration, all 10 Tier 1 companies, supply (capex) and demand (revenue) sides, sourced from 10-Ks/earnings releases.
- Sections 6-8: EDA, descriptive statistics, correlation (level vs. growth-rate, explicit spurious-trend-correlation discussion).
- Section 9: lag analysis (directional, capex-leads-revenue only). Section 9.1: bidirectional cross-correlation function (lags -2 to +2). Section 9.2: Granger-style causality test, both directions, controlling for each series' own momentum, with VIF and Breusch-Godfrey diagnostics. **Key finding, now tested five ways: no lead-lag relationship in either direction, at any lag, that survives controlling for trend and for each series' own persistence (all p>0.16).**
- Section 10: regression (contemporaneous and best-lag).
- Sections 11-12: diagnostics (assumptions OK; Oracle is a high-influence point) and robustness (leave-one-out shows the result is **Oracle-driven**; log-level specification flips to a strong significant *positive* result). Section 12.1: cluster-robust SEs, company fixed effects, and a 5,000-resample company-block bootstrap — all four ways of quantifying uncertainty around the coefficient agree it is not distinguishable from zero.
- Sections 13-15: discussion (research questions revisited one by one, updated for the new sections), limitations (annual resolution is still the top-priority weakness; fixed-effects power and Granger-terminology caveats added), conclusion (honest null/ambiguous result, now stress-tested rather than just asserted).

## Known open items for a next pass
- Full quarterly panel for all 10 Tier 1 companies (Section 5.4 got 3 of 10; extending to the rest — Meta, Oracle, Nvidia, AMD, Broadcom, TSMC, Micron — plus enough quarters per company for a properly powered lag regression, remains the top item).
- A proper heterogeneous-panel Granger causality test (e.g., Dumitrescu & Hurlin, 2012) in place of Section 9.2's simplified pooled version — no new data needed, just a more sophisticated model.
- Re-verify derived/back-calculated figures (flagged in each dataset's `source` column) against primary 10-Qs.
- Tier 2 (~17 of ~22 originally-scoped companies have a sector snapshot — Section 6.1/13.1; GlobalFoundries, IBM, Salesforce, Apple, OpenAI, Cisco, HPE, Baidu, Huawei, Xiaomi remain uncovered even at snapshot level).

## Structure

```
ai_supply_creates_demand.ipynb   # primary notebook — full workflow
datasets/                            # raw and cleaned data
figures/                             # exported charts
references/                          # source documentation / citations
requirements.txt
```

## Scope

- **Tier 1 (quantitative core, ~10 companies):** Microsoft, Alphabet, Amazon, Meta, Oracle, Nvidia, AMD, Broadcom, TSMC, Micron — used in correlation, lag, and regression analysis.
- **Tier 2 (descriptive only):** remaining companies across cloud/platform, semiconductor design/manufacturing, memory, infrastructure/networking, and international AI firms — covered in sector-level descriptive statistics and discussion, excluded from regression modeling due to sparse AI-specific disclosure.
- **Period:** annual, fiscal 2021/22–2026 (10-K/earnings-release based). Quarterly data was scoped in Section 4 as a future enhancement but was **not** collected in this pass — see "Known open items" above.

## Methods

Descriptive statistics, EDA, Pearson/Spearman correlation, a bidirectional cross-correlation function, lag analysis (1, 2, 4 quarters and 1 year), a Granger-style causality test (both directions, with VIF and Breusch-Godfrey diagnostics), simple/multiple linear regression, residual/VIF/influence diagnostics, and robustness checks across alternative demand measures, cluster-robust standard errors, company fixed effects, and a company-block bootstrap. Deliberately excludes causal-inference methods (IV, DiD, RDD, synthetic control, DSGE, Bayesian hierarchical models) as out of scope for this portfolio level — "Granger causality" here denotes predictive precedence, not structural causality, as the notebook itself flags in Section 9.2.

## Reproducing

```
pip install -r requirements.txt
jupyter notebook ai_supply_creates_demand.ipynb
```

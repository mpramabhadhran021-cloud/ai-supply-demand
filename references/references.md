# References

This file consolidates every source cited in the `source` columns of the datasets in `datasets/` and in the narrative text of `01_ai_supply_creates_demand.ipynb`. It is organized by source type. Where a dataset row cites a source, the citation below is the fuller version of what appears abbreviated in that row.

## Primary company filings and earnings releases (Tier 1 quantitative panel)

These are the primary sources for all figures in `capex_hyperscalers.csv`, `capex_foundry_memory.csv`, `chip_demand_revenue.csv`, and `hyperscaler_demand_revenue.csv`. Figures were compiled via the aggregators listed in the next section, which republish data from these filings; any figure should ultimately be traceable to the relevant company's 10-K, 10-Q, or earnings release for the fiscal period indicated.

- Microsoft Corporation — Form 10-K filings, fiscal years 2021–2026 (SEC CIK 0000789019)
- Alphabet Inc. — Form 10-K filings, fiscal years 2021–2025 (SEC CIK 0001652044)
- Amazon.com, Inc. — Form 10-K filings, fiscal years 2021–2025, including AWS segment disclosures (SEC CIK 0001018724)
- Meta Platforms, Inc. — Form 10-K filings and quarterly earnings releases, fiscal years 2021–2025 (SEC CIK 0001326801)
- Oracle Corporation — Form 10-K filings and quarterly earnings releases, fiscal years 2022–2026 (SEC CIK 0001341439)
- NVIDIA Corporation — Form 10-K filings, proxy statements (DEF 14A), and quarterly earnings releases, fiscal years 2022–2026 (SEC CIK 0001045810)
- Advanced Micro Devices, Inc. — Quarterly and annual earnings releases (Form 8-K/10-K), fiscal years 2023–2024 (SEC CIK 0000002488)
- Broadcom Inc. — Quarterly earnings releases, fiscal years 2024–2025 (SEC CIK 0001730168)
- Taiwan Semiconductor Manufacturing Company Limited — Annual reports and quarterly earnings calls, 2021–2025
- Micron Technology, Inc. — Form 10-K filings and quarterly earnings releases, fiscal years 2022–2025 (SEC CIK 0000723125)

## Financial data aggregators used to compile filing data

- stockanalysis.com — Cash flow statement pages for MSFT, GOOGL, AMZN, META, ORCL, NVDA, MU (financial data sourced from company filings via Fiscal.ai)
- macrotrends.net — Historical capital expenditure and revenue series, used as a cross-check against stockanalysis.com and primary filings
- financecharts.com — TSMC capital expenditure aggregation
- wallstreetzen.com — TSMC and Meta revenue aggregation
- bullfincher.io — Nvidia and Alphabet segment revenue aggregation
- TrendForce — TSMC and memory-industry capital expenditure reporting

## Industry and trade press (background, Section 3, and Tier 2 snapshot, Sections 6.1/13.1)

- Futurum Group (2026). *AI Capex 2026: The $690B Infrastructure Sprint.*
- datacenterrichness.substack.com (2026). *Hyperscalers Plan $630 Billion in 2026 CapEx.*
- Tom's Hardware (2026). *Google, Microsoft, Meta, and Amazon capex spending to hit $725 billion in 2026.*
- CNBC (2026). *Tech AI spending approaches $700 billion in 2026, cash taking big hit.*
- eMarketer (2026). *Big Tech's $600 billion AI capex plans could fuel faster automation rollouts but spark investor jitters.*
- CNBC (April 2026). *SK Hynix posts record first-quarter profit, in line with estimates as memory prices climb.*
- Fierce Network (2026). *Intel's data center and AI unit drives highest revenue growth in 15 years.*
- Futurum Group (2026). *Intel Q2 FY 2026: Hyperscaler Server Demand Drives 59% DCAI Growth.*
- Converge Digest (April 2026). *Intel Q1 2026: AI Drives 22% Data Center Growth, Foundry Revenue Up.*
- EE Times (June 2026). *Qualcomm Forecasts Billions in New Data Center Revenue.*
- 650 Group (2026). *MediaTek 2026 Analyst Day – Data Center is the Priority.*
- Futurum Group (April 2026). *MediaTek Analyst Day 2026 – Is the New MediaTek Ready to Move Upmarket to AI PCs and Data Center?*
- The Motley Fool (May 2026). *This Artificial Intelligence (AI) Stock Will Beat Nvidia, AMD, Broadcom, and Intel to Become the Biggest Winner in AI Inference* (Arm royalty revenue commentary).
- Yahoo Finance / Asia Tech Review commentary (2026) on Arm Holdings fiscal 2026 results and AI-server market share (IDC data).
- FirstPassLab (March 2026). *Marvell Forecasts $15B Revenue on AI Data Center Boom* (citing Reuters, March 2026).
- mlq.ai (2026). *Marvell Technology: Engineering the Backbone of the AI Data Center.*
- Asia Tech Review (April 2026). *ATR Daily: SK Hynix posts record profits as AI boom drives valuation toward $600B.*
- Tech Insider (June 2026). *Samsung's $73B Semiconductor Investment 2026: AI Chip Strategy.*
- TrendForce News (January 2026). *Samsung & SK hynix Earnings Showdown on 1/29: Profit, CAPEX, HBM4 in Focus.*
- datagravity.dev / Chris Zeoli (2026). *Who Captures Value in AI Infrastructure?* (margin/value-capture estimates for CoreWeave, Dell, Supermicro, Arista, Broadcom, Nvidia, TSMC).
- quantflowlab.com (March 2026). *AI Semiconductor Spending: Essential $630B Capex Breakdown* (TSMC 2025 revenue and 2026 capex guidance).
- alcapitaladvisory.com (2026). *AI Capex Cycle 2026: $725B Hyperscaler Buildout — CFA Analysis* (AMD Data Center revenue outlook).

## SEC filings consulted directly

- SK hynix Inc. — Form 424B4 and Form F-1/A (fiscal 2026), HBM and DRAM market share data (IDC-sourced tables within the filing).

## Methodological references (Sections 9.1, 9.2, 12.1)

- Granger, C. W. J. (1969). Investigating Causal Relations by Econometric Models and Cross-Spectral Methods. *Econometrica*, 37(3), 424-438. — definitional basis for the restricted-vs-full-model F-test used in Section 9.2; note that the term describes predictive precedence, not structural causality (flagged explicitly in Section 9.2 and Section 14).
- Dumitrescu, E.-I., & Hurlin, C. (2012). Testing for Granger Non-Causality in Heterogeneous Panels. *Economic Modelling*, 29(4), 1450-1460. — the proper heterogeneous-panel extension of Granger causality testing; Section 9.2 implements a simplified, illustrative pooled analogue of this procedure, not a full implementation, and a full implementation is listed as future work in Section 14.
- Cameron, A. C., & Miller, D. L. (2015). A Practitioner's Guide to Cluster-Robust Inference. *Journal of Human Resources*, 50(2), 317-372. — motivates the cluster-robust standard errors and the company-block bootstrap in Section 12.1, and the paper's own caution about needing "many" clusters is the basis for Section 12.1's caveat about only having 6 clusters available here.

## Citation methodology notes

- Every figure in the Tier 1 datasets is annotated in its own `source` column; this file provides the fuller reference, not a replacement for that column.
- Several figures are *derived* rather than directly disclosed (e.g., back-calculated from a stated year-over-year percentage change) — these are flagged individually in the relevant dataset's `source` column and discussed in Section 5.2 and Section 14 (Limitations) of the notebook. They should be treated as lower-confidence than directly-disclosed figures and re-verified against the underlying 10-Q/10-K before use in any more precise claim.
- The Tier 2 snapshot (`tier2_snapshot.csv`) draws primarily on secondary industry analysis and press coverage rather than primary filings, reflecting its intended role as illustrative sector context (Section 4) rather than a quantitative panel.

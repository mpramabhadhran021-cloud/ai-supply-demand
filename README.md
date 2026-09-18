# Does AI Supply Create Its Own Demand?

## What is this project?

This project studies whether spending on AI infrastructure is followed by growth in AI-related revenue. The idea is motivated by Say's Law, but the project does not try to test Say's Law directly.

## Research Question

> Does AI infrastructure investment come before growth in AI-related demand?

## Data

I use annual data for 10 large AI-related companies: Microsoft, Alphabet, Amazon, Meta, Oracle, Nvidia, AMD, Broadcom, TSMC, and Micron.

Capital expenditure is used as a measure of infrastructure investment and revenue as a measure of demand. The data come from company filings and earnings releases.

## Method

I use descriptive statistics, plots, correlations, lag analysis, a Granger-style predictive test, linear regression, regression diagnostics, and a few robustness checks.

The Granger-style test is used to study predictive timing. It does not show that one variable causes the other.

## Main Result

The data do not show a clear supply-before-demand relationship after accounting for trends and persistence in the series. The simple relationship is sensitive to the specification and to individual companies.

## Repository

ai_supply_demand.ipynb — main analysis notebook

datasets/ — data used in the analysis

figures/ — charts

references/ — data sources

## How to Run

pip install -r requirements.txt

jupyter notebook ai_supply_creates_demand.ipynb

## Limitations

The sample is small and uses annual data, so shorter-term relationships may be missed. The analysis is observational and cannot establish causality. The sample also focuses on large firms with relatively good public disclosure.
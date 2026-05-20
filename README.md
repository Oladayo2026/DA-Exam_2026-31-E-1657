# Project Profitability Analytics for Construction Projects

## Overview
This capstone analyzes project-level profitability in a construction services portfolio.
The main objective is to identify operational and commercial drivers of profit margin, including:
- project and client segment effects
- payment and procurement delays
- cost overrun behavior
- variation-order exposure

The report is implemented in Quarto with mirrored R and Python analysis sections.

## Primary Deliverable
- `oladayo_capstone_v2.qmd` -> `oladayo_capstone_v2.html`

Additional earlier draft files are also included:
- `oladayo_capstone.qmd`
- `oladayo_capstone.html`

## Repository Structure
- `oladayo_capstone_v2.qmd`: final report source (recommended)
- `oladayo_capstone_v2.html`: rendered output
- `oladayo_report.css`: custom Executive Brief stylesheet for HTML output
- `data/construction_company_projs.csv`: source dataset
- `requirements.txt`: Python dependencies
- `docs/`: supporting course/project documents

## Analytical Workflow
The report covers five techniques:
1. Exploratory Data Analysis (distribution, segment profiles, Pareto loss concentration)
2. Data Visualization (trend, risk, and concentration views)
3. Hypothesis Testing (Shapiro-Wilk, Levene/Brown-Forsythe, ANOVA, Welch, Kruskal, Tukey)
4. Correlation Analysis (Pearson and Spearman)
5. Multiple Regression (linear and quadratic specifications, VIF, robust HC1 errors, prediction example)

## Environment Requirements
- Quarto >= 1.4
- R >= 4.3
- Python >= 3.9

### Python packages
Install from `requirements.txt`:

```bash
pip install -r requirements.txt
```

### R packages used in report
The QMD loads these packages when available:
- readr, dplyr, tidyr, tibble, purrr, forcats
- ggplot2, lubridate, scales, ggcorrplot, patchwork
- broom, knitr, car, sandwich, lmtest
- kableExtra (optional formatting; report falls back gracefully if unavailable)

## Render Instructions
From workspace root:

```bash
quarto render "Oladayo Folorunso/oladayo_capstone_v2.qmd"
```

Or from this folder:

```bash
quarto render oladayo_capstone_v2.qmd
```

Preview mode (no browser auto-open):

```bash
quarto preview oladayo_capstone_v2.qmd --no-browser --no-watch-inputs
```

## Notes
- The report attempts to use a workspace virtual environment first for Python execution through `reticulate`.
- HTML styling is controlled by `oladayo_report.css` (Executive Brief theme).
- Quarto code-tools menu is intentionally disabled; code visibility is handled with chunk folding.
- If styled HTML tables are not available, the report still renders with plain `knitr::kable` output.
- Ensure the dataset file name remains exactly:
  - `data/construction_company_projs.csv`

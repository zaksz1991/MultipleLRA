# Multiple Linear Regression – Multi-Channel Marketing Analysis

## Project Overview

This project analyzes a marketing dataset to understand how **TV** (spend category), **Radio**, and **Social Media** spend relate to **Sales**, using Multiple Linear Regression (OLS) with `statsmodels`. The goal is to detect and address multicollinearity, build a statistically valid model, and translate the results into a prioritized recommendation for marketing budget allocation.

## Dataset Description

`marketing_sales_data.csv` contains 572 records with the following columns:

- `TV` — categorical spend category: `Low`, `Medium`, or `High`
- `Radio` — numeric spend (in $K)
- `Social Media` — numeric spend (in $K)
- `Influencer` — categorical influencer tier (`Nano`, `Micro`, `Macro`, `Mega`) — not used in this model
- `Sales` — numeric sales outcome (in $K), the target variable

There are no missing values in this dataset.

## Contents

- `multiple_regression_analysis.ipynb` — Jupyter Notebook containing the full analysis:
  - Data loading and initial EDA
  - Multicollinearity check via correlation matrix and Variance Inflation Factor (VIF)
  - Multiple linear regression model (`Sales ~ Radio + Social_Media + C(TV)`) with `statsmodels`
  - Model refinement based on p-values and Adjusted R-squared
  - Diagnostic plots for Normality and Homoscedasticity of residuals
  - Coefficient interpretation in business terms (holding other variables constant)
  - Prioritized, evidence-based recommendation for marketing budget allocation
- `marketing_sales_data.csv` — the dataset used for this analysis

## Environment Setup

This project requires Python 3 and the following packages:

```bash
pip install pandas numpy seaborn matplotlib statsmodels scipy
```

If you're using Jupyter Notebook/Lab and don't already have it installed:

```bash
pip install notebook
```

## How to Run

1. Clone this repository
2. Make sure `marketing_sales_data.csv` is in the same directory as the notebook
3. Open `multiple_regression_analysis.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab
4. Run all cells in order (Run → Run All Cells, or Shift+Enter through each cell)

## Key Findings

- All predictors have **VIF values below 5**, indicating no severe multicollinearity
- The full model (`Radio + Social_Media + C(TV)`) achieves an **Adjusted R-squared of ≈ 0.903**
- **`Social_Media` is not statistically significant** (p ≈ 0.82) and is dropped from the final model
- The reduced model (`Radio + C(TV)`) achieves an **Adjusted R-squared of ≈ 0.9035**, with both `Radio` and `TV` category being highly significant (p < 0.001)
- Holding `TV` category constant, each additional **$1K spent on Radio is associated with ≈ $2.97K increase in Sales**
- Holding `Radio` spend constant, moving from `Low` to `High` TV spend is associated with **≈ $154K higher Sales**, and from `Medium` to `High` with **≈ $75K higher Sales**

## Recommendation

1. **Prioritize moving into the "High" TV spend category** — the single largest driver of Sales in this model
2. **Continue investing in Radio** as a secondary, continuously scalable channel (≈ $2.97K Sales per $1K spent)
3. **De-prioritize Social Media spend** for direct Sales impact — no statistically significant relationship with Sales was found once TV and Radio were accounted for

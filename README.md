# Multiple Linear Regression - Real Estate Price Analysis

This project demonstrates multiple linear regression using a real estate dataset, built in two stages:

1. **Baseline model** — analyzing `price` using `size` and `year` only.
2. **Extended model** — analyzing `price` using `size`, `year`, and `view`, where `view` is a categorical variable (Sea view / No sea view) encoded as a **dummy variable** (0/1).

The notebook walks through both models side by side to show how adding a well-chosen categorical predictor improves model fit.

> **Note on scope:** This is an **explanatory / inferential regression analysis**, not a validated predictive model. The goal is to understand and quantify the relationship between `price` and its predictors (coefficients, significance, R²) using the full dataset. There is no train/test split or out-of-sample evaluation, so the model's ability to predict prices for new, unseen properties has not been tested here.

## Files

| File | Description |
|---|---|
| `multiple-linear-regression-real-estate.ipynb` | Combined notebook: Part 1 (size + year) → Part 2 (size + year + view) → comparison summary |
| `real_estate_price_size_year.csv` | Dataset for Part 1 |
| `real_estate_price_size_year_view.csv` | Dataset for Part 2 |

> Both CSV files must be in the same folder as the notebook for the code to run.

## Requirements

```
numpy
pandas
matplotlib
seaborn
statsmodels
```

Install with:
```bash
pip install numpy pandas matplotlib seaborn statsmodels
```

## What's covered

- Loading and exploring tabular data with `pandas`
- Declaring dependent (`y`) and independent (`x`) variables
- Encoding a categorical variable as a dummy variable
- Fitting an OLS regression with `statsmodels`
- Interpreting the regression summary table:
  - R-squared / Adjusted R-squared
  - Coefficients and p-values
  - Residual diagnostics (Durbin-Watson, Omnibus, Cond. No., etc.)

## Results

| Model | R-squared | Adj. R-squared |
|---|---|---|
| size + year | 0.776 | 0.772 |
| size + year + view (dummy) | 0.913 | 0.910 |

Adding the `view` dummy variable raised R-squared from **0.776 to 0.913**. The sea-view coefficient (~$56,730) is statistically significant (p = 0.000), meaning a sea view is associated with a meaningful price premium, holding size and year constant — within this dataset.

## Possible next steps (not included here)

- Train/test split to evaluate actual predictive performance
- Cross-validation
- Checking regression assumptions more rigorously (normality of residuals, homoscedasticity)
- Addressing the multicollinearity flagged by the high condition number

## Usage

Open the notebook in Jupyter:
```bash
jupyter notebook multiple-linear-regression-real-estate.ipynb
```
Run all cells top to bottom.

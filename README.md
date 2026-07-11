# Health Indicators and Infant Mortality: A Relationship Analysis

Identifies and quantifies the relationship between nutrition indicators (stunting, wasting,
undernourishment, underweight prevalence) and infant mortality across countries, using World Bank
World Development Indicators data pulled live via the free World Bank API.

## Why this project

A common mistake is fitting a regression model before establishing whether — and how — the variables
are actually related. This project does it in the right order:

1. **Correlation and significance testing first** (Spearman r + p-values) for each indicator individually
2. **Multicollinearity check** (VIF) between the nutrition indicators before trusting any coefficients
3. **Linearity test**: raw-target linear regression vs. log-transformed target, to check whether a
   straight-line relationship is even the right assumption
4. **Non-linear benchmark**: Random Forest, to see whether linear regression was ever the right tool
5. **Honest reporting**: if R² is weak, the conclusion says so and explains what that implies, rather
   than quietly moving on to a different metric

## Dataset

World Bank World Development Indicators, pulled live via the [World Bank API](https://data.worldbank.org/) —
free, public, no signup or API key required (via the `wbdata` Python package).

## Tech stack

PySpark (feature engineering, scaling, modelling), pandas/scipy/statsmodels (correlation, significance
testing, VIF), matplotlib/seaborn (visualisation).

## How to run

Open `Health_Indicators_Relationship_Analysis.ipynb` in Google Colab (free, no install) and run all
cells top to bottom — the data is pulled live from the World Bank API at runtime.

## Results summary

*(Fill in after running: which indicators were significantly correlated, whether VIF flagged any
collinearity, whether the log-transform or Random Forest improved on the raw linear model, and what
that implies about the true shape of the relationship.)*

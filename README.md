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
free, public

## requirments

PySpark (feature engineering, scaling, modelling), pandas/scipy/statsmodels (correlation, significance
testing, VIF), matplotlib/seaborn (visualisation).


## Results summary

All four nutrition indicators are significantly correlated with infant mortality. The analysis also revealed significant multicollinearity among 'stunting', 'wasting', and 'underweight'. While a log-linear relationship appears to describe the data better than a raw linear one, the overall R² values (around 0.64-0.65) indicate that a significant portion of the variance in infant mortality is still unexplained by these nutrition indicators alone. This suggests that other factors (e.g., healthcare access, sanitation, income, maternal education) are also crucial drivers of infant mortality, making nutrition indicators necessary but not sufficient predictors.

# Multiple Linear Regression – Multi-Channel Marketing Analysis

## Objective
Predict Sales using multiple marketing channels and evaluate model assumptions.

## Data Preparation
- Checked missing values
- Applied dropna()
- Encoded TV categorical variable with dummy variables

## Multicollinearity
VIF values were below 10, indicating no severe multicollinearity.

## Model Performance
- Adjusted R² = 0.903
- F-statistic = 1335
- Model p-value < 0.05

## Regression Equation
Sales = 218.647 + 2.989(Radio) − 0.150(Social Media) − 154.312(TV_Low) − 75.328(TV_Medium)

## Assumption Checks
- Linearity verified using residual plots
- Independence verified using Durbin-Watson statistic
- Normality verified using Q-Q plot
- Homoscedasticity verified using residual analysis

## Business Recommendation
Prioritize High TV exposure and Radio advertising. Reassess Social Media spending because it was not statistically significant.

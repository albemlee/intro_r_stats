# Linear Regression

## What is linear regression?

Linear regression is used to examine the relationship between a **continuous outcome (dependent variable)** and one or more **predictors (independent variables)**.

Use linear regression when:
- Your outcome (dependent variable) is continuous
- You want to understand how predictors relate to the outcome
- You want to control for confounders (other variables that may influence the relationship)

> **Note:** Linear regression does not require the outcome to be normally distributed. Instead, we check whether the model’s residuals (differences between observed and predicted values) are approximately normally distributed.

---

## Fitting a model in R

> **Data source:** This data was obtained from the publicly available Health and Retirement Study: https://hrs.isr.umich.edu/about

```r
library(tidyverse)

# Predict systolic blood pressure from diastolic blood pressure
model <- lm(bp_sys ~ bp_dia, data = hrs_df)
summary(model)
```

`lm()` fits a generalized linear model. For linear regression, the default family (gaussian) is used automatically.

---

## Reading the output

```
Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 38.71302    2.03510   19.02   <2e-16 ***
bp_dia       1.21980    0.02595   47.00   <2e-16 ***
```

Interpreting `bp_dia`:
> "For each 1 mmHg increase in diastolic blood pressure, systolic blood pressure is expected to be 1.22 mmHg higher, on average."

Key elements of an interpretation:
1. Name the predictor and outcome
2. State the direction and magnitude of the effect
3. Add "holding other variables constant" for multivariable models
4. Note statistical significance

---

## Multivariable linear regression

```r
model_multi <- lm(bp_sys ~ bp_dia + age + female, data = hrs_df)
summary(model_multi)
```

Each coefficient represents the effect of that variable *holding all others constant*.

---

## Knowledge check

A linear regression predicts systolic BP from age. The coefficient for age is 0.61 (p < 0.001). Write a plain-language interpretation.

<details>
<summary>Answer</summary>

"For each additional year of age, systolic blood pressure is expected to be 0.61 mmHg higher, on average. This association is statistically significant (p < 0.001)."

</details>

---

## Slides

🖼️ [Download slides (overview)](../slides/01_linear_regression_overview.pdf) · [Download slides (interpretation)](../slides/02_linear_regression_interpretation.pdf)

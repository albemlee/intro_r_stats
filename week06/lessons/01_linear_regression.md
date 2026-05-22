# Linear Regression

## What is linear regression?

Linear regression predicts a **continuous dependent variable** from one or more **independent variables**, and describes the relationship between them.

Use linear regression when:
- Your outcome (dependent variable) is continuous
- You want to understand how predictors relate to the outcome
- You want to control for confounders

> **First step:** Always check that your outcome is approximately normally distributed before fitting a linear model.

---

## Fitting a model in R

```r
library(tidyverse)

# Predict systolic blood pressure from diastolic blood pressure
model <- glm(bp_sys ~ bp_dia, data = hrs_df)
summary(model)
```

`glm()` fits a generalized linear model. For linear regression, the default family (gaussian) is used automatically.

---

## Reading the output

```
Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept) 36.42      2.40      15.17   <2e-16 ***
bp_dia       1.25      0.03      40.71   <2e-16 ***
```

Interpreting `bp_dia`:
> "For each 1-unit increase in diastolic blood pressure, systolic blood pressure is expected to increase by 1.25 mmHg, holding other variables constant."

Key elements of an interpretation:
1. Name the predictor and outcome
2. State the direction and magnitude of the effect
3. Add "holding other variables constant" for multivariable models
4. Note statistical significance

---

## Multivariable linear regression

```r
model_multi <- glm(bp_sys ~ bp_dia + age + female, data = hrs_df)
summary(model_multi)
```

Each coefficient represents the effect of that variable *holding all others constant*.

---

## Knowledge check

A linear regression predicts systolic BP from age. The coefficient for age is 0.45 (p < 0.001). Write a plain-language interpretation.

<details>
<summary>Answer</summary>

"For each additional year of age, systolic blood pressure is expected to increase by 0.45 mmHg, holding other variables constant. This relationship is statistically significant."

</details>

---

## Optional video

Search YouTube for **"linear regression explained StatQuest"** (~10 min).

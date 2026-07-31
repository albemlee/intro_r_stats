# Video Script: Linear Regression

**Estimated length:** 10–12 minutes  
**Slides:** [01_linear_regression_overview.pdf](../slides/01_linear_regression_overview.pdf) · [02_linear_regression_interpretation.pdf](../slides/02_linear_regression_interpretation.pdf)

---

## Introduction

This lesson introduces linear regression — one of the most widely used statistical methods in biomedical research. We'll cover what it is, when to use it, how to fit it in R, and how to read and interpret the output.

---

# Part 1: Overview

## [SLIDE: Linear Regression Overview]

**Linear regression** does two related things: it predicts a continuous dependent variable based on one or more independent variables, and it describes the relationship between them.

Use it when:
- Your outcome (dependent variable) is continuous — blood pressure, age, weight, lab values
- You want to understand how one or more predictors relate to that outcome
- You want to adjust for confounders — variables that might explain away an apparent relationship

---

## [SLIDE: The Dependent Variable Must Be Continuous and Normally Distributed]

Before fitting a linear regression, always check that your outcome variable is approximately normally distributed. This is one of the key assumptions of the model.

```r
# Quick check
hrs_df %>%
  ggplot() +
    geom_histogram(aes(x = bp_sys), bins = 30)
```

If the outcome is heavily skewed, consider a log transformation or a different model family.

---

# Part 2: Fitting and Interpreting

## [SLIDE: Demo — Doing Linear Regression]

In R, linear regression uses `glm()` — the generalized linear model function:

```r
model <- glm(bp_sys ~ bp_dia, data = hrs_df)
summary(model)
```

We're predicting systolic blood pressure (`bp_sys`) from diastolic blood pressure (`bp_dia`).

---

## [SLIDE: Reading the Output]

Here's the key part of the output:

```
Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept) 36.42      2.40      15.17   <2e-16 ***
bp_dia       1.25      0.03      40.71   <2e-16 ***
```

The `Estimate` column contains the coefficients. The intercept is the predicted value of `bp_sys` when `bp_dia` is zero. More importantly, the coefficient for `bp_dia` is 1.25.

Here's how to interpret that:

> "For each 1-unit increase in diastolic blood pressure, systolic blood pressure is expected to increase by 1.25 mmHg."

The p-value (`Pr(>|t|)`) tells you whether the coefficient is significantly different from zero. Three stars means p < 0.001.

---

## [SLIDE: Identifying Dependent and Independent Variables in the Output]

Reading regression output requires knowing which variable is which. The dependent variable appears in the formula on the left side of `~`. The independent variables appear on the right. Every row in the coefficients table corresponds to one independent variable (plus the intercept).

---

## [SLIDE: Null and Alternative Hypotheses for Each Coefficient]

For each coefficient, the hypothesis test is:
- **H₀:** The estimate is zero — no relationship between this predictor and the outcome
- **Hₐ:** The estimate is not zero — there is a relationship

The p-value tells you whether the data is consistent with H₀.

---

## [SLIDE: Demo — Multivariable Regression]

Adding more predictors extends the model:

```r
model_multi <- glm(bp_sys ~ bp_dia + female + age_2014, data = hrs_df)
summary(model_multi)
```

In a multivariable model, each coefficient represents the effect of that predictor **holding all other predictors constant**. This is what allows regression to adjust for confounders.

For example, the coefficient for `female` in this model tells you the expected difference in systolic BP between female and male participants, *after accounting for diastolic BP and age.*

---

## [SLIDE: Likelihood Ratio Test — Comparing Models]

When you add variables to a model, you want to know whether the expanded model actually fits the data better. The **likelihood ratio test** answers this:

```r
library(lmtest)
lrtest(model, model_multi)
```

The output gives a chi-squared statistic and p-value. A significant result means the additional variables significantly improve model fit — they explain meaningful variation in the outcome beyond what the simpler model captures.

---

## Knowledge Check

A linear regression predicts systolic BP from age. The coefficient for age is 0.45 (p < 0.001). Write a plain-language interpretation.

"For each additional year of age, systolic blood pressure is expected to increase by 0.45 mmHg, holding other variables constant. This relationship is statistically significant."

That template — direction, magnitude, units, "holding other variables constant," significance — applies to every linear regression coefficient you'll ever interpret.

---

## Closing

Linear regression is powerful precisely because of the multivariable case: it lets you examine one predictor's relationship with the outcome while controlling for others. In the next lesson, we'll extend this framework to binary outcomes with logistic regression.

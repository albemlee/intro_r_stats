# Video Script: Logistic Regression

**Estimated length:** 10–12 minutes  
**Slides:** [04_logistic_regression_overview.pdf](../slides/04_logistic_regression_overview.pdf) · [05_logistic_regression_interpretation.pdf](../slides/05_logistic_regression_interpretation.pdf)

---

## Introduction

Linear regression is for continuous outcomes. But in biomedical research, many of the most important outcomes are binary: diagnosed or not, survived or didn't, readmitted or not. **Logistic regression** is the tool for those situations.

---

# Part 1: Overview

## [SLIDE: Logistic Regression Overview]

The structure of logistic regression is essentially the same as linear regression — you have a dependent variable and one or more independent variables, and you're describing the relationship between them. The difference is the type of dependent variable.

| Model | Dependent variable |
|-------|--------------------|
| Linear regression | Continuous (e.g., blood pressure in mmHg) |
| Logistic regression | Binary (e.g., depression diagnosis: yes/no) |

---

## [SLIDE: The Regression Family]

It's worth stepping back to see the bigger picture. Both linear and logistic regression belong to the same family of models — the **generalized linear model**. In R, you fit both with `glm()`. The only difference is the `family` argument:

```r
# Linear regression
glm(bp_sys ~ bp_dia, data = hrs_df)   # gaussian family (default)

# Logistic regression
glm(depress_dx ~ bp_dx, family = binomial, data = hrs_df)
```

`family = binomial` tells R you have a binary outcome and to fit a logistic regression.

---

# Part 2: Interpretation

## [SLIDE: Demo — Doing Logistic Regression]

Here's a simple model predicting depression diagnosis from hypertension diagnosis:

```r
model <- glm(depress_dx ~ bp_dx, family = binomial, data = hrs_df)
summary(model)
```

---

## [SLIDE: Reading the Output — Raw Coefficients]

The coefficient table looks familiar:

```
Coefficients:
            Estimate Std. Error z value Pr(>|z|)
(Intercept)  -1.8163    0.1112  -16.33  < 2e-16 ***
bp_dx         0.5597    0.1258    4.45 8.61e-06 ***
```

But here's the catch: the raw estimate for `bp_dx` (0.5597) is in **log-odds**. That's not directly interpretable by most human beings.

---

## [SLIDE: Converting to Odds Ratios]

Convert to **odds ratios** using `exp()`:

```r
exp(coef(model))
```

Output:
```
(Intercept)   bp_dx
  0.163       1.750
```

An odds ratio of 1.75 for `bp_dx` means: patients with a hypertension diagnosis have 1.75 times the odds of a depression diagnosis compared to those without hypertension.

Key benchmarks:
- OR = 1: no association
- OR > 1: higher odds of the outcome
- OR < 1: lower odds of the outcome

---

## An Important Warning About Odds Ratios

Odds ratios are **not** probability ratios. An OR of 1.75 does not mean patients with hypertension are 75% more likely to have depression in absolute terms. The odds and probability of an event are related but different quantities, especially when the outcome is common. Always interpret ORs as odds ratios, not as risk ratios.

---

## [SLIDE: Multivariable Logistic Regression]

Adding covariates works the same way:

```r
model_multi <- glm(depress_dx ~ bp_dx + female + age_2014, 
                   family = binomial, data = hrs_df)
summary(model_multi)
```

Each coefficient (after exponentiating) is the odds ratio for that variable, **holding all others constant**. This is how logistic regression adjusts for confounders.

In the output, notice that `female` has a large and significant coefficient — female participants have much higher odds of a depression diagnosis, even after adjusting for age and hypertension status.

---

## [SLIDE: Likelihood Ratio Test]

Just as with linear regression, compare models using the likelihood ratio test to assess whether additional variables meaningfully improve fit:

```r
library(lmtest)
lrtest(model, model_multi)
```

A significant result confirms the multivariable model fits the data better than the simpler model.

---

## Knowledge Check

A logistic regression reports exp(coef) = 1.46 for depression diagnosis (p < 0.001) in a survival model. Write a plain-language interpretation.

"Patients with a depression diagnosis have 1.46 times the odds of the outcome compared to those without depression, after adjusting for other variables in the model. This association is statistically significant."

The template: state the group, give the odds ratio, name the comparison group, note the direction (higher or lower odds), mention adjustment for other variables, state significance.

---

## Closing

Logistic regression is one of the most-used models in clinical research. Once you're comfortable reading linear regression output, logistic regression is a small conceptual step — swap the outcome type and exponentiate the coefficients. In the next lesson, we'll make sure the model was applied correctly by examining diagnostics for both model types.

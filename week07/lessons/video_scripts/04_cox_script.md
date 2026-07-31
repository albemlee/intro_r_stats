# Video Script: Cox Proportional Hazards Regression

**Estimated length:** 8–9 minutes  
**Slides:** [04_cox.pdf](../slides/04_cox.pdf)

---

## Introduction

The log rank test compares survival between two groups. But real research questions rarely involve just one variable. How does sex affect survival *after adjusting for age, blood pressure, and depression*? For that, we need Cox proportional hazards regression.

---

## [SLIDE: Cox Proportional Hazards Regression]

**Cox regression** is the multivariable method for survival outcomes. It extends the log rank test to:
- Handle multiple predictors simultaneously
- Adjust for confounders
- Estimate the size of each predictor's effect

The effect size in Cox regression is the **hazard ratio (HR)**.

---

## [SLIDE: The Hazard Ratio]

The **hazard** is the instantaneous probability of experiencing the event at any given point in time — think of it as the "risk rate" at a specific moment.

The **hazard ratio** compares the hazard between two groups:

- **HR > 1:** Higher hazard — worse prognosis — compared to the reference group
- **HR < 1:** Lower hazard — better prognosis
- **HR = 1:** No difference

This is conceptually parallel to the odds ratio in logistic regression: both are ratios comparing two groups, both equal 1 when there's no effect, and both are interpreted relative to a reference category.

---

## [SLIDE: Fitting a Cox Model in R]

```r
library(survival)

cox_model <- coxph(
  Surv(mos_to_death, died) ~ female + age_2014 + bp_dx + depress_dx,
  data = hrs_df
)
summary(cox_model)
```

The formula structure is familiar: `Surv(time, status)` on the left, predictors on the right.

---

## [SLIDE: Reading Cox Regression Output]

```
             coef  exp(coef)  se(coef)    z        p
female      0.394     1.483    0.086    4.55  5.3e-06
age_2014    0.290     1.337    0.010   30.51  < 2e-16
bp_dx      -0.059     0.943    0.089   -0.66  0.512
depress_dx  0.376     1.456    0.104    3.62  0.0003
```

The `coef` column contains log hazard ratios — not directly interpretable. Use `exp(coef)` for the actual hazard ratios.

Interpretation of `depress_dx` (HR = 1.456, p = 0.0003):
> "Patients with a depression diagnosis had 1.46 times the hazard of death compared to those without depression, after adjusting for sex, age, and hypertension. This association was statistically significant."

Interpretation of `bp_dx` (HR = 0.943, p = 0.512):
> "Hypertension diagnosis was not significantly associated with mortality after adjusting for other covariates (p = 0.51)."

---

## [SLIDE: The Proportional Hazards Assumption]

Cox regression rests on one key assumption: the **proportional hazards assumption** — that the hazard ratio between any two groups remains constant over time.

Think of it this way: if people with depression have 1.46 times the hazard of death compared to those without, that ratio should hold at month 6, month 24, month 48 — not just on average.

Test this assumption formally:

```r
cox.zph(cox_model)
```

---

## [SLIDE: Interpreting the Proportional Hazards Test]

```
           chisq  df      p
female     0.004   1  0.950
age_2014   4.337   1  0.037
bp_dx      0.459   1  0.498
depress_dx 0.001   1  0.978
GLOBAL     5.745   4  0.219
```

For each variable, the null hypothesis is that the hazard ratio is constant over time. A significant p-value (< 0.05) indicates the assumption may be violated for that variable.

Here, `age_2014` has p = 0.037 — borderline evidence that the age hazard ratio changes over time. However, the global test (p = 0.219) is not significant, suggesting the model as a whole meets the proportional hazards assumption reasonably well.

If a variable strongly violates this assumption, options include stratifying the model by that variable or using time-varying coefficients.

---

## Knowledge Check

A Cox model reports HR = 0.72 (p = 0.008) for a new treatment. Write a plain-language interpretation.

"Patients who received the new treatment had 0.72 times the hazard of the outcome compared to those who did not — a 28% reduction in hazard. This effect is statistically significant (p = 0.008)."

Note how to calculate the percent reduction: 1 - HR = 1 - 0.72 = 0.28 = 28% reduction. This is a natural way to communicate hazard ratios below 1.

---

## Closing

Cox regression is the culmination of the methods this course has built toward: a multivariable model that accounts for the unique features of time-to-event data, adjusts for confounders, and provides interpretable effect sizes. 

Congratulations on completing the statistical methods content. Week 8 brings everything together in the final project.

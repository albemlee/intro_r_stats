# Video Script: Model Diagnostics

**Estimated length:** 7–8 minutes  
**Slides:** [03_linear_regression_diagnostic.pdf](../slides/03_linear_regression_diagnostic.pdf) · [06_other_regression_diagnostics.pdf](../slides/06_other_regression_diagnostics.pdf)

---

## Introduction

Fitting a model and getting output isn't the end of the analysis. You need to verify that the model was applied correctly — that its assumptions are reasonably met. If they're not, the p-values and confidence intervals the model produces may be misleading. This lesson covers the two main diagnostic checks: residuals for linear regression, and multicollinearity for any regression model.

---

# Part 1: Linear Regression Diagnostics

## [SLIDE: Model Diagnostics — Linear Regression]

The question for any model is: how do we know we've applied it correctly?

For linear regression, the primary tool is the **residual**. A residual is the difference between the observed value and the model's predicted value.

```
residual = observed - predicted
```

A well-fitting linear model has residuals that:
1. Are approximately normally distributed, centered at zero
2. Show no systematic relationship with the predicted values

---

## [SLIDE: What to Check in Residuals]

```r
model <- glm(bp_sys ~ bp_dia + age + female, data = hrs_df)

plot(model, which = 1)   # Residuals vs. Fitted — check for patterns
plot(model, which = 2)   # QQ plot — check normality of residuals
```

The **Residuals vs. Fitted plot** should look like a random scatter around zero. If you see a curved pattern, the relationship may not be linear. If you see a fan shape — residuals that spread wider as fitted values increase — that indicates **heteroscedasticity**: the variance isn't constant, which violates the linear regression assumption.

The **QQ plot of residuals** checks whether the residuals are normally distributed. Points should fall along the diagonal line. Systematic deviations — especially in the tails — suggest non-normality.

---

## [SLIDE: Demo — Checking Residuals]

In the demo, you'll generate and interpret both diagnostic plots. The key skill is learning to distinguish a "good enough" pattern from a genuine violation. Some deviation from ideal is expected in real data — the question is whether it's substantial enough to undermine the model's conclusions.

---

# Part 2: Multicollinearity

## [SLIDE: Other Regression Diagnostics — Multicollinearity]

The second diagnostic applies to any multivariable regression — linear or logistic.

**Multicollinearity** occurs when two or more independent variables are highly correlated with each other. When this happens, the model can't cleanly attribute the variation in the outcome to each predictor separately. The result: standard errors inflate, coefficients become unstable, and individual p-values become unreliable — even though the overall model may still fit well.

---

## [SLIDE: Variance Inflation Factor (VIF)]

The standard tool for detecting multicollinearity is the **Variance Inflation Factor (VIF)**:

```r
library(car)
vif(model_multi)
```

Example output:
```
  bp_dx   female  age_2014
  1.019    1.042    1.061
```

Interpreting VIF:
- VIF = 1: no correlation with other predictors
- 1 < VIF < 5: moderate correlation — usually acceptable
- VIF ≥ 5: severe correlation — problematic

In this example, all VIFs are near 1, so multicollinearity is not a concern. When VIFs are large, consider removing one of the correlated variables or combining them into a composite measure.

---

## Knowledge Check

You fit a linear regression and the Residuals vs. Fitted plot shows a clear fan shape — residuals that spread wider as fitted values get larger. What does this tell you, and what might you do about it?

This indicates **heteroscedasticity** — non-constant variance. The assumption of equal variance across fitted values is violated. Options include transforming the outcome variable (a log transformation often helps with right-skewed outcomes), using a model that explicitly accounts for varying variance, or using robust standard errors.

---

## Closing

Model diagnostics are a habit, not an afterthought. Every time you fit a regression, check the residuals. Every time you fit a multivariable model, check VIF. These checks take a few minutes and can save you from reporting conclusions that rest on violated assumptions.

This completes Week 6. In Week 7, we move to survival analysis — a specialized set of methods for handling time-to-event outcomes.

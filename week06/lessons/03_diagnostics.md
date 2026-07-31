# Model Diagnostics

## Why diagnostics matter

Fitting a model is not enough — you need to verify that the model's assumptions are met. If they are violated, the model's estimates and p-values may be unreliable.

---

## Linear regression: checking residuals

A **residual** is the difference between the observed value and the model's predicted value.

For a well-fitting linear model:
- Residuals should be approximately normally distributed (mean ≈ 0)
- Residuals should not be correlated with predicted values (no pattern in the residuals vs. fitted plot)

```r
# Fit model
model <- glm(bp_sys ~ bp_dia + age + female, data = hrs_df)

# Residual plots
plot(model, which = 1)   # Residuals vs. Fitted — check for patterns
plot(model, which = 2)   # QQ plot — check normality of residuals
```

A fan-shaped pattern in the residuals vs. fitted plot indicates heteroscedasticity (non-constant variance) — a violation of the linear regression assumption.

---

## Multicollinearity: VIF

**Multicollinearity** occurs when independent variables are highly correlated with each other. This inflates standard errors and makes individual coefficients unreliable.

Detect it with the **Variance Inflation Factor (VIF)**:

```r
library(car)

model_multi <- glm(depress_dx ~ bp_dx + female + age_2014, 
                   family = binomial, data = hrs_df)
vif(model_multi)
```

| VIF value | Interpretation |
|-----------|---------------|
| VIF = 1 | No correlation |
| 1 < VIF < 5 | Moderate — usually acceptable |
| VIF ≥ 5 | Severe — consider removing or combining variables |

---

## Knowledge check

You fit a linear regression and the residuals vs. fitted plot shows a clear fan shape (residuals spread wider as fitted values increase). What does this indicate?

<details>
<summary>Answer</summary>

**Heteroscedasticity** — the variance of the residuals is not constant across fitted values. This violates a key assumption of linear regression. Options include transforming the outcome variable (e.g., log transformation) or using a model that handles non-constant variance.

</details>

---

## Optional video

A video (~7–8 min) walks through the slides for this lesson and covers residual plots for linear regression, detecting and interpreting heteroscedasticity, and checking multicollinearity with VIF.

📄 [View the video script](video_scripts/03_diagnostics_script.md) · 🖼️ [Download slides (linear diagnostic)](../slides/03_linear_regression_diagnostic.pdf) · [Download slides (other diagnostics)](../slides/06_other_regression_diagnostics.pdf)

# Model Diagnostics

## Why diagnostics matter

Fitting a model is not enough - you also need to check whether its assumptions are reasonable. If they are violated, the model’s estimates, standard errors, and p-values may be unreliable.

---

## Linear regression: checking residuals

A **residual** is the difference between the observed value and the model's predicted value.

For a well-fitting linear model:
- Residuals should be approximately normally distributed for traditional statistical inference (e.g., p-values and confidence intervals), particularly in small samples.
- Residuals should be scattered randomly around zero, with no clear pattern or change in spread in the residuals vs. fitted plot.

> **Data source:** This data was obtained from the publicly available Health and Retirement Study: https://hrs.isr.umich.edu/about

```r
# Fit model
model <- lm(bp_sys ~ bp_dia + age + female, data = hrs_df)

# Residual plots
plot(model, which = 1)   # Residuals vs. Fitted 
plot(model, which = 2)   # Normal QQ plot 
```

A fan-shaped pattern in the residuals vs. fitted plot suggests heteroscedasticity (non-constant variance), meaning the spread of residuals changes across predicted values.

---

## Multicollinearity: VIF

**Multicollinearity** occurs when predictors are strongly related to one another. This can increase standard errors, making it harder to estimate their individual associations with the outcome precisely.

Detect it with the **Variance Inflation Factor (VIF)**:

```r
library(car)

model_multi <- glm(depress_dx ~ bp_dx + female + age_2014, 
                   family = binomial, data = hrs_df)
vif(model_multi)
```

| VIF value | Interpretation |
|-----------|---------------|
| VIF = 1 | No multicollinearity |
| 1 < VIF < 5 | Some multicollinearity — usually acceptable |
| VIF ≥ 5 | Potentially concerning multicollinearity — investigate further |

---

## Knowledge check

You fit a linear regression and the residuals vs. fitted plot shows a clear fan shape (residuals spread wider as fitted values increase). What does this indicate?

<details>
<summary>Answer</summary>

**Heteroscedasticity** - the spread of residuals increases as predicted values increase, indicating non-constant variance. Possible approaches include transforming the outcome (e.g., log transformation) or using methods that account for non-constant variance.

</details>

---

## Slides

🖼️ [Download slides (linear diagnostic)](../slides/03_linear_regression_diagnostic.pdf) · [Download slides (other diagnostics)](../slides/06_other_regression_diagnostics.pdf)

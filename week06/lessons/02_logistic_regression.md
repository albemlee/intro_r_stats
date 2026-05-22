# Logistic Regression

## When to use logistic regression

Use logistic regression when your dependent variable is **binary** (yes/no, 0/1, disease/no disease).

| Model | Dependent variable |
|-------|------------------|
| Linear regression | Continuous (e.g., blood pressure) |
| Logistic regression | Binary (e.g., diagnosed: yes/no) |

---

## Fitting a logistic model

```r
# Predict depression diagnosis from hypertension diagnosis
model <- glm(depress_dx ~ bp_dx, family = binomial, data = hrs_df)
summary(model)
```

`family = binomial` tells `glm()` to fit a logistic regression.

---

## Interpreting the output — odds ratios

The raw coefficients from logistic regression are **log-odds** — not directly interpretable. Convert them to **odds ratios** using `exp()`:

```r
exp(coef(model))
```

```
(Intercept)   bp_dx
  0.163        1.750
```

An **odds ratio (OR)**:
- OR = 1: no association
- OR > 1: higher odds of the outcome
- OR < 1: lower odds of the outcome

Interpretation of OR = 1.75 for `bp_dx`:
> "Patients with a hypertension diagnosis have 1.75 times the odds of a depression diagnosis compared to those without hypertension."

> ⚠️ Odds ratios are **not** the same as probability ratios. An OR of 1.75 does not mean "75% more likely."

---

## Knowledge check

A logistic regression reports exp(coef) = 1.46 for depression diagnosis (p < 0.001) in a survival model. Write a plain-language interpretation.

<details>
<summary>Answer</summary>

"Patients with a depression diagnosis have 1.46 times the odds of the outcome compared to those without depression. This association is statistically significant."

</details>

---

## Optional video

Search YouTube for **"logistic regression explained StatQuest"** (~10 min).

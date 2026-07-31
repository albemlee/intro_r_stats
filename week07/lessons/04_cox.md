# Cox Proportional Hazards Regression

## Why Cox regression?

The log rank test compares two groups. **Cox proportional hazards regression** extends this to:
- Include multiple predictors simultaneously
- Adjust for confounders
- Estimate the size of the effect

---

## The hazard ratio

Cox regression estimates **hazard ratios (HR)**:

- **Hazard:** The instantaneous probability of experiencing the event at a given time
- **HR > 1:** Higher hazard (worse prognosis) compared to the reference group
- **HR < 1:** Lower hazard (better prognosis)
- **HR = 1:** No difference

---

## Fitting a Cox model in R

```r
library(survival)

cox_model <- coxph(
  Surv(mos_to_death, died) ~ female + age_2014 + bp_dx + depress_dx,
  data = hrs_df
)
summary(cox_model)
```

Key output columns:
- `coef`: log hazard ratio (not directly interpretable)
- `exp(coef)`: hazard ratio ✅
- `Pr(>|z|)`: p-value for each predictor

---

## Interpreting hazard ratios

```
             coef  exp(coef)  p
depress_dx   0.376  1.456     0.0003 ***
```

> "Patients with a depression diagnosis had 1.46 times the hazard of death compared to those without depression, after adjusting for sex, age, and hypertension. This association was statistically significant."

---

## Knowledge check

A Cox model reports HR = 0.72 (p = 0.008) for a new treatment. Write a plain-language interpretation.

<details>
<summary>Answer</summary>

"Patients who received the new treatment had 0.72 times the hazard of the outcome compared to those who did not — a 28% reduction in hazard. This effect is statistically significant."

</details>

---

## Optional video

A video (~8–9 min) walks through the slides for this lesson and covers hazard ratios, fitting a Cox model with `coxph()`, interpreting the output, and testing the proportional hazards assumption.

📄 [View the video script](video_scripts/04_cox_script.md) · 🖼️ [Download the slides](../slides/04_cox.pdf)

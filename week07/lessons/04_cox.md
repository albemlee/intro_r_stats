# Cox Proportional Hazards Regression

## Why Cox regression?

The log rank test compares survival between groups. **Cox proportional hazards regression** allows us to:
- Examine multiple predictors simultaneously
- Adjust for potential confounders
- Estimate the strength of associations with survival

---

## The hazard ratio

Cox regression estimates **hazard ratios (HR)**:

- **Hazard:** The rate at which events occur at a given time among those who have not yet experienced the event.
- **HR > 1:** Higher hazard of experiencing the event compared to the reference group
- **HR < 1:** Lower hazard of experiencing the event compared to the reference group
- **HR = 1:** No difference in hazard between groups
  
## Proportional hazards assumption 

This is a central assumption of Cox regression - it means that the hazard ratio between groups is assumed to remain constant over time.

- **How to check:** Kaplan-Meier curves can provide clues — curves that cross may suggest the assumption is violated, although formal statistical tests are needed to assess it.
- **If violated:** Consider alternative approaches, such as allowing the hazard ratio to change over time.

This is a more advanced topic that is beyond the scope of this course. For now, just be aware that the proportional hazards assumption should be checked when using Cox regression.

---

## Fitting a Cox model in R

> **Data source:** This data was obtained from the publicly available Health and Retirement Study: https://hrs.isr.umich.edu/about

```r
library(survival)

cox_model <- coxph(
  Surv(mos_to_death, died) ~ female + age_2014 + bp_dx + depress_dx,
  data = hrs_df
)
summary(cox_model)
```

`coxph()` fits a Cox proportional hazards regression model.

Key output columns:
- `coef`: Log hazard ratio (usually interpreted after exponentiating)
- `exp(coef)`: Hazard ratio (HR)
- `Pr(>|z|)`: P-value testing whether each predictor is associated with the hazard of the event

---

## Interpreting hazard ratios

```
             coef  exp(coef)  p
depress_dx   0.376  1.456     0.0003 ***
```

> "Patients with a depression diagnosis had a 46% higher hazard of death compared to those without depression, after adjusting for sex, age, and hypertension. This association was statistically significant."

---

## Knowledge check

A Cox model reports HR = 0.72 (p = 0.008) for patients receiving a new treatment compared to those not receiving it. How would you interpret this result?

<details>
<summary>Answer</summary>

"Patients who received the new treatment had a 28% lower hazard of experiencing the event compared to those who did not receive the treatment. This association was statistically significant."

</details>

---

## Slides

🖼️ [Download the slides](../slides/04_cox.pdf)

# Log Rank Test

## What is the log rank test?

The **log rank test** compares survival between two (or more) groups. It is the hypothesis test counterpart to the Kaplan-Meier curve.

- **H₀:** There is no difference in survival between the groups
- **Hₐ:** There is a difference in survival between the groups

The test is **non-parametric** — it makes no distributional assumptions.

---

## Running the log rank test in R

> **Data source:** This data was obtained from the publicly available Health and Retirement Study: https://hrs.isr.umich.edu/about

```r
library(survival)

survdiff(Surv(mos_to_death, died) ~ female, data = hrs_df)
```

Example output:
```
        N  Observed  Expected  (O-E)^2/E  (O-E)^2/V
female=0  936   325       271      10.98       18.7
female=1 1458   354       408       7.27       18.7
Chisq = 18.7 on 1 df, p = 2e-05
```

Interpretation:
> "There is a statistically significant difference in survival between male and female participants (log rank p < 0.001). We reject the null hypothesis of no difference in survival."

---

## Knowledge check

A log rank test returns p = 0.0002 at a significance level of 0.05. What is your conclusion?

<details>
<summary>Answer</summary>

Reject the null hypothesis. There is a statistically significant difference in survival between the groups. The probability of observing this or a more extreme result if the groups had equal survival is 0.02%.

</details>

---

## Slides

🖼️ [Download the slides](../slides/03_logrank.pdf)

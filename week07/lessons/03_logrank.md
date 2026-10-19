# Log-Rank Test

## What is the log-rank test?

The **log rank test** compares survival over time between two or more groups. It tests whether the groups have different survival experiences.

- **H₀:** The groups have the same survival probabilities over time.
- **Hₐ:** The groups have different survival probabilities over time.

The test is **non-parametric** — it does not assume that survival times follow a particular distribution.

---

## Running the log rank test in R

> **Data source:** This data was obtained from the publicly available Health and Retirement Study: https://hrs.isr.umich.edu/about

```r
library(survival)

survdiff(Surv(mos_to_death, died) ~ female, data = hrs_df)
```

`survdiff()` performs the log rank test to compare survival between groups.


Example output:
```
        N  Observed  Expected  (O-E)^2/E  (O-E)^2/V
female=0  936   325       271      10.98       18.7
female=1 1458   354       408       7.27       18.7
Chisq = 18.7 on 1 df, p = 2e-05
```

Focus on the p-value at the bottom of the output to determine whether there is evidence of a difference in survival between groups.

Interpretation:
> "There is evidence of a difference in survival between male and female participants (log rank p < 0.001). We reject the null hypothesis of equal survival between groups."

---

## Knowledge check

A log rank test gives a p-value of 0.0002. Using a significance level of 0.05, what would you conclude?

<details>
<summary>Answer</summary>

Reject the null hypothesis because p < 0.05. There is statistically significant evidence that survival differs between the groups.

</details>

---

## Slides

🖼️ [Download the slides](../slides/03_logrank.pdf)

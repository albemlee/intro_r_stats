# Video Script: Log Rank Test

**Estimated length:** 5–6 minutes  
**Slides:** [03_logrank.pdf](../slides/03_logrank.pdf)

---

## Introduction

The Kaplan-Meier curve shows you what survival looks like in your sample. The **log rank test** takes the next step: it tells you whether any differences you see between groups are statistically significant — or whether they're consistent with sampling variation under the null hypothesis of no difference.

---

## [SLIDE: Log Rank Test]

The log rank test compares survival between two groups. It's the hypothesis test counterpart to the Kaplan-Meier curve.

- **H₀:** There is no difference in survival between the groups
- **Hₐ:** There is a difference in survival between the groups

The test is **non-parametric** — it makes no assumption about the shape of the survival distribution. It works by comparing the observed number of events in each group to what would be expected if survival were identical in both groups.

---

## [SLIDE: Demo — Log Rank Test]

```r
library(survival)

survdiff(Surv(mos_to_death, died) ~ female, data = hrs_df)
```

---

## [SLIDE: Reading the Output]

```
        N  Observed  Expected  (O-E)^2/E  (O-E)^2/V
female=0  936   325       271      10.98       18.7
female=1 1458   354       408       7.27       18.7
Chisq = 18.7 on 1 df, p = 2e-05
```

Let's walk through this. Male participants (female=0) had 325 observed deaths, but only 271 were *expected* under the null hypothesis of equal survival. Female participants (female=1) had 354 observed deaths versus 408 expected.

So males died more than expected, and females died less than expected — consistent with the KM curves showing better female survival.

The chi-squared statistic of 18.7 with p = 2e-05 is far below 0.05. We reject the null hypothesis.

Interpretation:
> "There is a statistically significant difference in survival between male and female participants (log rank p < 0.001). Males experienced higher-than-expected mortality and females lower-than-expected mortality."

---

## Knowledge Check

A log rank test returns p = 0.0002 at a significance level of 0.05. What is your conclusion?

Reject the null hypothesis. There is a statistically significant difference in survival between the two groups. The probability of observing this or a more extreme result if the groups had identical survival is 0.02% — far below the 5% threshold.

---

## Closing

The log rank test is a clean, assumption-light way to compare survival between two groups. But it can only handle one grouping variable at a time, and it doesn't adjust for confounders. For a multivariable analysis of survival — adjusting for age, sex, disease status simultaneously — we need Cox regression, which is the final lesson of the course.

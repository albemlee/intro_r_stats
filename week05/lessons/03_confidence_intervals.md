# Confidence Intervals

## What is a confidence interval?

A **95% confidence interval** gives a range of plausible values for the true population parameter.

Two ways to think about it:

**Detailed interpretation:**  
If we collected many samples and built a 95% CI from each, approximately 95% of those intervals would contain the true population value.

**Lazy interpretation (commonly used):**  
We are 95% confident the true population value lies within this interval.

---

## Calculating a confidence interval

If the bootstrap distribution of your statistic is approximately normal:

```
95% CI = point estimate ± (1.96 × standard error)
```

```r
library(tidyverse)
library(palmerpenguins)

# Point estimate
point_est <- mean(penguins$bill_length_mm, na.rm = TRUE)

# Bootstrap SE
set.seed(42)
boot_means <- replicate(300, {
  resample <- penguins %>% sample_n(nrow(penguins), replace = TRUE)
  mean(resample$bill_length_mm, na.rm = TRUE)
})
se <- sd(boot_means)

# 95% CI
lower <- point_est - 1.96 * se
upper <- point_est + 1.96 * se

cat("95% CI:", round(lower, 2), "to", round(upper, 2))
```

If the bootstrap distribution is not normal, use the **BCa bootstrap interval** instead (available in the `boot` package).

---

## Knowledge check

A study reports a 95% CI for mean age at diagnosis as (52.3, 58.7). What does this mean?

<details>
<summary>Answer</summary>

We are 95% confident the true mean age at diagnosis in the population lies between 52.3 and 58.7 years. The interval, not the point estimate alone, is the appropriate summary of our uncertainty.

</details>

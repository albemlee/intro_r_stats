# Confidence Intervals

## What is a confidence interval?

A **95% confidence interval** gives a range of values that are consistent with the observed data and our estimate of its uncertainty.

Two ways to think about it:

**Technical interpretation:**  
If we repeatedly collected samples from the same population and calculated a 95% CI from each, approximately 95% of those intervals would contain the true population value.

**Common shorthand:**  
We are 95% confident the true population value lies within this interval.

---

## Calculating a confidence interval

If the sampling distribution of your statistic is approximately normal, a 95% CI can be estimated as:

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
complete_bill_lengths <- penguins %>%
  drop_na(bill_length_mm)
boot_means <- replicate(300, {
  resample <- penguins %>% sample_n(nrow(penguins), replace = TRUE)
  mean(resample$bill_length_mm)
})
se <- sd(boot_means)

# 95% CI
lower <- point_est - 1.96 * se
upper <- point_est + 1.96 * se

cat("95% CI:", round(lower, 2), "to", round(upper, 2))
```

If the bootstrap distribution is not normal, there are some alternate methods (e.g., see the R `boot` package).

---

## Knowledge check

A study reports a 95% CI for mean age at diagnosis as (52.3, 58.7). What does this mean?

<details>
<summary>Answer</summary>

We are 95% confident that the true mean age at diagnosis is between 52.3 and 58.7 years. More precisely, if we repeatedly sampled from this population and calculated intervals in the same way, about 95% of those intervals would contain the true population mean.

</details>

---

## Slides

🖼️ [Download the slides](../slides/04_confidence_interval.pdf)

</details>

# Video Script: Confidence Intervals

**Estimated length:** 6–7 minutes  
**Slides:** [04_confidence_interval.pdf](../slides/04_confidence_interval.pdf)

---

## Introduction

We now have a point estimate — our best single guess — and a standard error — our measure of how uncertain that guess is. This lesson puts them together to construct a confidence interval: a range of plausible values for the true population parameter.

---

## [SLIDE: Confidence Interval]

A **95% confidence interval** gives a range of values that likely contains the true population parameter.

There are two ways to interpret it, and it's worth knowing both.

**The technically precise interpretation:** If we collected many samples from the population and built a 95% CI from each one, approximately 95% of those intervals would contain the true population value. Any single interval either does or doesn't contain it — but following this procedure guarantees a 95% success rate in the long run.

**The everyday interpretation (what most people mean):** We are 95% confident the true population value lies within this interval.

The second is less precise but commonly used in research writing. Just know what it actually means.

---

## [SLIDE: Calculating the Confidence Interval]

If your bootstrap distribution of the statistic is approximately normal, the 95% confidence interval is:

```
95% CI = Point Estimate ± (1.96 × Standard Error)
```

In R:

```r
# Point estimate
point_est <- mean(penguins$bill_length_mm, na.rm = TRUE)

# Bootstrap SE (from previous lesson)
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

The 1.96 comes from the fact that for a normal distribution, 95% of values fall within 1.96 standard deviations of the mean.

---

## When the Bootstrap Distribution Is Not Normal

If your bootstrap statistics are not normally distributed, the formula above doesn't apply. In that case, use the **Bias-Corrected and Accelerated (BCa) bootstrap interval**, available in the `boot` package. The lesson has code for this.

In practice, thanks to the Central Limit Theorem, the bootstrap distribution of the mean is usually approximately normal — but it's worth checking with a histogram or QQ plot before using the formula.

---

## Knowledge Check

A study reports a 95% confidence interval for mean age at diagnosis as (52.3, 58.7). What does this mean?

We are 95% confident the true mean age at diagnosis in the population lies between 52.3 and 58.7 years. The interval is the appropriate summary of our uncertainty — not just the point estimate alone.

Note what it does *not* mean: it does not mean there's a 95% probability the true value is in this specific interval. The true value is fixed — the interval either contains it or it doesn't. The 95% refers to the long-run reliability of the method.

---

## Closing

Point estimate, standard error, confidence interval — these three together give you an honest, complete description of what your sample tells you about the population. From here, we move to hypothesis testing: a framework for making decisions based on that evidence.

# Video Script: Point Estimate and Standard Error

**Estimated length:** 8–9 minutes  
**Slides:** [02_point_estimate.pdf](../slides/02_point_estimate.pdf) · [03_standard_error.pdf](../slides/03_standard_error.pdf)

---

## Introduction

This lesson covers two concepts that go hand in hand: the point estimate and the standard error. Together, they give you a best guess at a population value and an honest measure of how much uncertainty surrounds that guess.

---

# Part 1: Point Estimate

## [SLIDE: Point Estimate]

A **point estimate** is your sample statistic used as a best guess for the corresponding population parameter.

If your sample is representative of the population, then the sample mean is your best estimate of the population mean. The sample proportion is your best estimate of the population proportion.

```r
# Point estimate: mean bill length for all penguins in our sample
mean(penguins$bill_length_mm, na.rm = TRUE)
```

That number — whatever it comes out to — is your point estimate of the true mean bill length in the penguin population.

---

## [SLIDE: It Depends on How the Sample Was Collected]

Here's the critical caveat: whether a sample statistic is a valid point estimate depends entirely on how the sample was collected.

If your sample is a convenience sample — a group that was easy to reach rather than randomly selected — it may not be representative of the broader population. In that case, using your sample mean as a point estimate of the population mean could be misleading.

This is not a statistical problem — it's a study design problem. Inferential statistics assumes representative sampling. If that assumption is violated, the methods don't apply.

---

# Part 2: Standard Error

## [SLIDE: Standard Deviation vs. Standard Error]

Now, a point estimate by itself is just a number. It doesn't tell you how reliable it is. That's where the standard error comes in.

Here's a conceptual distinction that trips people up:

**Standard deviation** measures variability of individual observations in your sample. If penguin bill lengths have a high SD, individual penguins vary a lot.

**Standard error** measures variability of the sample statistic — the mean — across repeated samples. If you collected 1,000 different samples and computed the mean from each, how much would those means vary?

Standard error is the inferential counterpart to standard deviation. SD describes individuals; SE describes how reliable your estimate is.

---

## [SLIDE: Bootstrapping to Calculate Standard Error]

We estimate the standard error using a technique called **bootstrapping**. Here's the intuition: since we can't actually collect 300 different samples from the population, we simulate the process by resampling from the data we have.

The steps:
1. Draw 200–300 resamples from your sample, **with replacement**, each the same size as the original
2. Calculate the statistic (e.g., the mean) for each resample
3. The standard deviation of those resample statistics is your standard error

```r
set.seed(42)

boot_means <- replicate(300, {
  resample <- penguins %>%
    sample_n(size = nrow(penguins), replace = TRUE)
  mean(resample$bill_length_mm, na.rm = TRUE)
})

se <- sd(boot_means)
print(se)
```

One important check: look at the distribution of your bootstrap statistics. Thanks to the Central Limit Theorem, this distribution is usually approximately normal even if the original data isn't. If it's not normal, you'll need a different approach for your confidence interval — which we cover in the next lesson.

---

## [SLIDE: Demo — Calculate Standard Error]

In the demo, you'll walk through the full bootstrapping process. Pay attention to how the distribution of bootstrap means compares to the distribution of the raw data — they're related but different, and understanding that relationship is key to understanding what the standard error actually represents.

---

## Knowledge Check

What is the conceptual difference between standard deviation and standard error?

Standard deviation tells you how spread out individual measurements are in your sample. Standard error tells you how much your sample statistic — the mean — would vary if you collected many different samples from the same population.

They measure variability at different levels: SD at the observation level, SE at the sample-statistic level.

---

## Closing

Point estimate plus standard error gives you a foundation for quantifying uncertainty. In the next lesson, we'll use these two values together to construct a confidence interval — a range of plausible values for the true population statistic.

# Point Estimate and Standard Error

## Point estimate

A **point estimate** is a single value calculated from your sample that is used to estimate a corresponding population parameter.

If your sample is representative of the population:
- Sample mean → point estimate of population mean
- Sample proportion → point estimate of population proportion

*Caveat:* How well a point estimate represents the population depends on how the sample was collected. A convenience sample, for example, may produce a biased estimate.

```r
library(tidyverse)
library(palmerpenguins)

# Point estimate: mean bill length for all penguins
mean(penguins$bill_length_mm, na.rm = TRUE)
```

> **Caveat:** Whether a sample statistic is a valid point estimate depends entirely on how the sample was collected. A convenience sample may not be representative.

---

## Standard error

**Standard deviation** measures variability of individual observations in your sample.  
**Standard error** measures uncertainty in the sample statistic itself - it tells us how much the statistic would vary across different samples drawn from the same population.

We can estimate the standard error using **bootstrapping**:

1. Draw many (e.g., 1,000) resamples from your sample (with replacement, same size)
2. Compute the statistic (e.g., mean) for each resample
3. The standard deviation of those statistics - this estimates the standard error

```r
library(tidyverse)
library(palmerpenguins)

# Bootstrap standard error of mean bill length (we will use 300 re-samplings here for efficiency)
# First set a seed for reproducibility (on your machine) and remove penguins with missing bill lengths

set.seed(42)

complete_bill_lengths <- penguins %>%
  drop_na(bill_length_mm)

boot_means <- replicate(300, {
  resample <- complete_bill_lengths %>%
    sample_n(size = nrow(complete_bill_lengths), replace = TRUE)
  mean(resample$bill_length_mm)
})

se <- sd(boot_means)
print(se)
```

---

## Knowledge check

What is the conceptual difference between standard deviation and standard error?

<details>
<summary>Answer</summary>

- **Standard deviation:** measures how spread out individual measurements are in your sample
- **Standard error:** measures how much your sample statistic (e.g., the mean) would vary if you collected many different samples from the same population

</details>

---

## Slides

🖼️ [Download slides (point estimate)](../slides/02_point_estimate.pdf) · [Download slides (standard error)](../slides/03_standard_error.pdf)

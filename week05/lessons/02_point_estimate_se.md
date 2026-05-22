# Point Estimate and Standard Error

## Point estimate

A **point estimate** is your sample statistic used as a best guess for the corresponding population parameter.

If your sample is representative of the population:
- Sample mean → point estimate of population mean
- Sample proportion → point estimate of population proportion

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
**Standard error** measures variability of the sample statistic itself — if you repeated the study many times, how much would the mean vary?

We estimate standard error using **bootstrapping**:

1. Draw 200–300 resamples from your sample (with replacement, same size)
2. Compute the statistic (e.g., mean) for each resample
3. The standard deviation of those statistics = the standard error

```r
library(tidyverse)
library(palmerpenguins)

# Bootstrap standard error of mean bill length
set.seed(42)

boot_means <- replicate(300, {
  resample <- penguins %>%
    sample_n(size = nrow(penguins), replace = TRUE)
  mean(resample$bill_length_mm, na.rm = TRUE)
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

Standard error is the inferential counterpart to standard deviation.

</details>

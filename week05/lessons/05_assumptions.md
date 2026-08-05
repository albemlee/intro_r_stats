# Assumptions and Test Selection

## Why assumptions matter

Every statistical test makes assumptions about the data. Using the wrong test — one whose assumptions your data violates — produces unreliable results.

The most important distinction: **parametric vs. non-parametric tests**.

| Type | Assumption | Examples |
|------|-----------|---------|
| **Parametric** | Data follows a specific distribution (usually normal) | t-test, ANOVA |
| **Non-parametric** | No distributional assumption | Wilcoxon rank-sum, chi-squared |

---

## Checking normality

Before choosing a test, check whether your data is normally distributed.

### 1. Histogram

```r
library(tidyverse)
library(palmerpenguins)

penguins %>%
  filter(species == "Gentoo") %>%
  ggplot() +
    geom_histogram(aes(x = flipper_length_mm), bins = 20)
```

### 2. QQ plot

Points falling along the diagonal line suggest normality:

```r
penguins %>%
  filter(species == "Gentoo") %>%
  pull(flipper_length_mm) %>%
  qqnorm()
qqline(penguins %>% filter(species == "Gentoo") %>% pull(flipper_length_mm))
```

### 3. Shapiro-Wilk test

```r
gentoo_flipper <- penguins %>%
  filter(species == "Gentoo") %>%
  pull(flipper_length_mm)

shapiro.test(gentoo_flipper)
```

- p > 0.05 → do not reject normality → parametric test may be appropriate
- p ≤ 0.05 → evidence against normality → use non-parametric test

---

## Test selection guide

| Research question | Data type | Normal? | Test |
|------------------|-----------|---------|------|
| Compare means: 2 groups | Continuous | Yes | t-test |
| Compare medians: 2 groups | Continuous | No | Wilcoxon rank-sum |
| Compare means: 3+ groups | Continuous | Yes | One-way ANOVA |
| Association between 2 categorical variables | Categorical | — | Chi-squared |

---

## Knowledge check

You want to compare hospital stay duration between patients who received treatment A vs. treatment B. A histogram shows the data is strongly right-skewed. Which test should you use?

<details>
<summary>Answer</summary>

**Wilcoxon rank-sum test** (non-parametric). The data is not normally distributed, so a t-test is not appropriate.

</details>

---

## Slides

🖼️ [Download the slides](../slides/06_assumptions.pdf)

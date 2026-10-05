# Assumptions and Test Selection

## Why assumptions matter

Every statistical test makes assumptions about the data. Using the wrong test — one whose assumptions your data violates — produces unreliable results.

The most important distinction: **parametric vs. non-parametric tests**.

| Type | Assumption | Examples |
|------|-----------|---------|
| **Parametric** | Makes assumptions about the distribution of the outcome (or model errors) | t-test, ANOVA |
| **Non-parametric** | Makes fewer assumptions about the outcome distribution | Wilcoxon rank-sum, Kruskal-Wallis|

---

## Checking normality

For tests that assume normality, examine the distribution of the outcome **within each group**. Histograms and QQ plots can help identify strong skewness or outliers.

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

---

## Test selection guide

| Research question | Test |
|------------------|------|
| Compare a continuous outcome: 2 groups | t-test |
| Compare a continuous outcome: 2 groups with strong skew/outliers | Wilcoxon rank-sum |
| Compare a continuous outcome: 3+ groups | One-way ANOVA |
| Compare a continuous outcome: 3+ groups with strong skew/outliers | Kruskal-Wallis |

---

## Knowledge check

You want to compare hospital stay duration between patients who received treatment A vs. treatment B. A histogram shows the data is strongly right-skewed. Which test should you use?

<details>
<summary>Answer</summary>

**Wilcoxon rank-sum test** (non-parametric) is a reasonable choice because hospital stay duration is strongly right-skewed.

</details>

---

## Slides

🖼️ [Download the slides](../slides/06_assumptions.pdf)

# Describing Continuous Variables

## Start with a histogram

Always plot a continuous variable before calculating summary statistics. The shape of the distribution determines which statistics are appropriate.

```r
library(tidyverse)
library(palmerpenguins)

penguins %>%
  ggplot() +
    geom_histogram(
      mapping = aes(x = bill_length_mm),
      bins = 30
    )
```

---

## Choosing summary statistics

| Distribution shape | Appropriate statistics |
|-------------------|----------------------|
| **Normal** (bell-shaped, symmetric) | Mean and standard deviation |
| **Skewed** or non-normal | Five-number summary: min, Q1, median, Q3, max |

```r
# For a normal distribution
mean(penguins$bill_length_mm, na.rm = TRUE)
sd(penguins$bill_length_mm, na.rm = TRUE)

# Five-number summary (works for any distribution)
summary(penguins$bill_length_mm)
```

---

## Computing by group

Often you want summaries per group (e.g., per species):

```r
penguins %>%
  group_by(species) %>%
  summarize(
    mean_bill = mean(bill_length_mm, na.rm = TRUE),
    sd_bill   = sd(bill_length_mm, na.rm = TRUE)
  )
```

---

## Faceting: one plot per group

`facet_wrap()` creates a separate panel for each level of a variable:

```r
penguins %>%
  ggplot() +
    geom_histogram(mapping = aes(x = bill_length_mm), bins = 20) +
    facet_wrap(~species)
```

---

## Knowledge check

You plot a histogram of patient hospital stay duration and it is strongly right-skewed (most stays are short, but a few are very long). Should you report mean + SD or the five-number summary?

<details>
<summary>Answer</summary>

**Five-number summary.** The mean and SD are appropriate only for normally distributed data. For skewed data, the median and IQR (Q1 to Q3) give a more accurate picture of the typical value.

</details>

---

## Slides

🖼️ [Download the slides](../slides/04_continuous.pdf) · [Bonus: lazy exploration](../slides/05_lazy_exploration.pdf)

# Describing Categorical Variables

## Bar plots

The standard visualization for a categorical variable is a **bar plot** showing counts per category:

```r
library(tidyverse)
library(palmerpenguins)

penguins %>%
  ggplot() +
    geom_bar(mapping = aes(x = species))
```

---

## Controlling category order with factors

By default, ggplot2 orders categories alphabetically. To control the order, convert the column to a **factor** and specify `levels`:

```r
penguins %>%
  mutate(
    species = factor(species, levels = c("Gentoo", "Adelie", "Chinstrap"))
  ) %>%
  ggplot() +
    geom_bar(mapping = aes(x = species))
```

Factors tell R there is a meaningful order to the categories.

---

## Computing counts

Use `group_by()` and `summarize()` to get the numbers behind the bar chart:

```r
penguins %>%
  group_by(species) %>%
  summarize(count = n())
```

---

## Knowledge check

**True or False:** Categorical variables must be converted to factors before you can plot them in a bar chart.

<details>
<summary>Answer</summary>

**False.** You can plot a categorical variable without converting it to a factor. However, factors are needed if you want to control the order of the bars.

</details>

---

## Slides

🖼️ [Download the slides](../slides/03_categorical.pdf)

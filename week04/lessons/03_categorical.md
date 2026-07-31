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

## Practice

```r
library(tidyverse)
library(palmerpenguins)

# 1. Create a bar plot of penguin counts by island
# Your code here

# 2. Reorder the bars so they appear as: Biscoe, Dream, Torgersen
# Your code here

# 3. Compute the count and proportion of penguins per species
#    (proportion = count / sum(count))
# Your code here
```

---

## Optional video

A short video (~5–6 min) walks through the slides for this lesson and covers bar plots, controlling category order with factors, and computing counts with `group_by()` and `summarize()`.

📄 [View the video script](video_scripts/03_categorical_script.md) · 🖼️ [Download the slides](../slides/03_categorical.pdf)

# Video Script: Describing Categorical Variables

**Estimated length:** 5–6 minutes  
**Slides:** [03_categorical.pdf](../slides/03_categorical.pdf)

---

## Introduction

This lesson focuses on categorical variables — the kind where values fall into named groups rather than on a continuous scale. Species, sex, island, treatment arm — these are all categorical. We'll look at how to visualize them and how to control the way they appear in your plots.

---

## [SLIDE: Demo — Create a Bar Plot of Counts]

The standard visualization for a categorical variable is a **bar plot**. In ggplot2, `geom_bar()` builds one automatically:

```r
penguins %>%
  ggplot() +
    geom_bar(mapping = aes(x = species))
```

By default, ggplot2 counts the rows in each category and uses those counts as the bar heights. You don't need to calculate counts first — `geom_bar()` does it for you.

---

## [SLIDE: Factors — Controlling Category Order]

By default, ggplot2 orders bars alphabetically. Sometimes you want a specific order — maybe because there's a clinical progression, or because you want to compare categories in a meaningful sequence.

To control the order, you convert the column to a **factor** and specify the levels:

```r
penguins %>%
  mutate(
    species = factor(species, levels = c("Gentoo", "Adelie", "Chinstrap"))
  ) %>%
  ggplot() +
    geom_bar(mapping = aes(x = species))
```

The `levels` argument tells R the order you want. Gentoo goes first, then Adelie, then Chinstrap. A factor is just a categorical variable with an explicit ordering attached to it.

This also matters for statistical tests. If you're running a model with a categorical predictor, the first level of the factor is used as the reference group. Knowing how to set factor levels gives you control over how your results are reported.

---

## Computing Counts Directly

If you want the counts as a table — not just in a plot — use `group_by()` and `summarize()`:

```r
penguins %>%
  group_by(species) %>%
  summarize(count = n())
```

This is useful for reporting tables or when you need the proportions as well:

```r
penguins %>%
  group_by(species) %>%
  summarize(
    count = n(),
    proportion = n() / nrow(penguins)
  )
```

---

## [SLIDE: Knowledge Check]

**True or False:** Categorical variables must be converted to factors before you can plot them in a bar chart.

**False.** ggplot2 will happily plot a character column as a bar chart — you'll just get alphabetical order. You only need to convert to a factor when you want to control the order of the bars.

---

## Closing

Categorical variables are straightforward to describe: count them, plot them, and when needed, control their ordering with factors. In the next lesson, we'll look at continuous variables — where the shape of the distribution becomes the most important thing to understand first.

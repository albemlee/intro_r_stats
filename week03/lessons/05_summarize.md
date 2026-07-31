# Aggregating with group_by() and summarize()

## The problem

Each row in the penguins dataset represents one penguin. But what if you want to understand each *species* as a whole — like the average bill length per species?

That is what `group_by()` and `summarize()` are for.

---

## group_by() + summarize()

```r
library(tidyverse)
library(palmerpenguins)

penguins %>%
  group_by(species) %>%
  summarize(
    n_penguins        = n(),
    mean_bill_length  = mean(bill_length_mm, na.rm = TRUE),
    mean_body_mass    = mean(body_mass_g, na.rm = TRUE)
  )
```

Reading aloud: "Take penguins, then group by species, then for each group compute the count, mean bill length, and mean body mass."

- `group_by()` defines what each row in the output represents (here: one row per species)
- `summarize()` defines what each column in the output contains
- `n()` counts the number of rows per group
- `na.rm = TRUE` tells `mean()` to ignore missing values

---

## Grouping by multiple variables

```r
penguins %>%
  group_by(species, sex) %>%
  summarize(
    count        = n(),
    mean_mass    = mean(body_mass_g, na.rm = TRUE)
  )
```

---

## mutate() vs. summarize() — revisited

```r
# mutate(): keeps all 344 rows, adds a column
penguins %>%
  group_by(species) %>%
  mutate(mean_mass_by_species = mean(body_mass_g, na.rm = TRUE))

# summarize(): collapses to 3 rows (one per species)
penguins %>%
  group_by(species) %>%
  summarize(mean_mass = mean(body_mass_g, na.rm = TRUE))
```

---

## Knowledge check

**True or False:** You can use `summarize()` and `mutate()` interchangeably.

<details>
<summary>Answer</summary>

**False.** `summarize()` collapses rows (returns one row per group). `mutate()` keeps all rows and adds a column. They serve different purposes.

</details>

---

## Practice

```r
library(tidyverse)
library(palmerpenguins)

# 1. Compute the number of penguins and mean flipper length per island
# Your code here

# 2. Compute the min and max bill_length_mm per species
# Your code here

# 3. Filter to non-missing sex, then compute mean body mass per species AND sex
# Your code here
```

---

## Optional video

A short video (~7–8 min) walks through the slides for this lesson and covers `group_by()`, `summarize()`, grouping by multiple variables, and why `summarize()` and `mutate()` are not interchangeable.

📄 [View the video script](video_scripts/05_summarize_script.md) · 🖼️ [Download the slides](../slides/05_summarize.pdf)

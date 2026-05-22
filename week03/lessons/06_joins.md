# Combining Data: bind_rows() and Joins

## bind_rows() — stacking tibbles vertically

If you have two tibbles with the **same columns**, you can stack them:

```r
library(tidyverse)

# Two batches of penguin measurements
batch_1 <- tibble(species = c("Adelie", "Chinstrap"), bill_length_mm = c(39.1, 46.5))
batch_2 <- tibble(species = c("Gentoo", "Adelie"),    bill_length_mm = c(47.3, 40.2))

combined <- batch_1 %>%
  bind_rows(batch_2)
```

> **Important:** Both tibbles must have the same column names. If columns differ, `bind_rows()` will fill missing values with `NA`.

---

## Joins — connecting related tibbles

When data lives in separate tables linked by a shared key, you use a **join**.

```r
# Penguin measurements
measurements <- tibble(
  penguin_id = c(1, 2, 3),
  bill_length_mm = c(39.1, 46.5, 47.3)
)

# Penguin species lookup
species_lookup <- tibble(
  penguin_id = c(1, 2, 3),
  species = c("Adelie", "Chinstrap", "Gentoo")
)

# Join on penguin_id
measurements %>%
  left_join(species_lookup, by = "penguin_id")
```

---

## Types of joins

| Join | What it keeps |
|------|--------------|
| `left_join()` | All rows from the left tibble; matches from the right |
| `inner_join()` | Only rows that match in both tibbles |
| `full_join()` | All rows from both tibbles |

**Always check `nrow()` before and after a join** to verify you haven't accidentally dropped or duplicated rows.

---

## Knowledge check

**True or False:** You should use `bind_rows()` to combine tibbles with different columns.

<details>
<summary>Answer</summary>

**False.** `bind_rows()` requires the same columns. For tibbles with different columns linked by a shared key, use a join.

</details>

---

## Practice

```r
library(tidyverse)

# Two tibbles to work with:
sites <- tibble(
  island = c("Torgersen", "Biscoe", "Dream"),
  region = c("Antarctic Peninsula", "Palmer Archipelago", "Palmer Archipelago")
)

library(palmerpenguins)

# 1. Left-join the sites tibble to the penguins tibble by island
# How many rows does the result have? Why?
# Your code here

# 2. Check: does the number of rows change with an inner_join instead?
# Your code here
```

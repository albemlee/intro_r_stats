# Adding Variables with mutate()

## What does mutate() do?

`mutate()` adds new columns to a tibble (or modifies existing ones) based on expressions you define.

```r
library(tidyverse)
library(palmerpenguins)

# Add a column converting bill length from mm to cm
penguins %>%
  mutate(bill_length_cm = bill_length_mm / 10)
```

The original tibble is unchanged — `mutate()` returns a new tibble with the added column.

---

## Creating multiple columns at once

```r
penguins %>%
  mutate(
    bill_length_cm = bill_length_mm / 10,
    bill_depth_cm  = bill_depth_mm / 10,
    bill_ratio     = bill_length_mm / bill_depth_mm
  )
```

---

## Modifying existing columns

You can also use `mutate()` to overwrite an existing column:

```r
# Round bill_length_mm to the nearest integer
penguins %>%
  mutate(bill_length_mm = round(bill_length_mm, 0))
```

---

## mutate() vs. summarize()

A common point of confusion:

| Function | What it returns |
|----------|----------------|
| `mutate()` | Same number of rows as input — adds a column |
| `summarize()` | Fewer rows — collapses rows into a summary |

Use `mutate()` when you want to add or change a column row by row.

---

## Knowledge check

**True or False:** You can use `mutate()` to change an existing column.

<details>
<summary>Answer</summary>

**True.** `mutate()` can create new columns or overwrite existing ones.

</details>

---

## Practice

```r
library(tidyverse)
library(palmerpenguins)

# 1. Add a column called flipper_length_cm (flipper_length_mm / 10)
# Your code here

# 2. Add a column called is_large_penguin that is TRUE if body_mass_g > 4500
# Your code here

# 3. Chain: filter to Adelie penguins, then add bill_ratio (bill_length_mm / bill_depth_mm)
# Your code here
```

---

## Optional video

A short video (~6–7 min) walks through the slides for this lesson and covers creating new columns, modifying existing ones, and the key difference between `mutate()` and `summarize()`.

📄 [View the video script](video_scripts/04_mutate_script.md) · 🖼️ [Download the slides](../slides/04_mutate.pdf)

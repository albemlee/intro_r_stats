# Grammar of Graphics and ggplot2

## What is ggplot2?

`ggplot2` is R's premier visualization package, included in the tidyverse. It implements the **Grammar of Graphics** — a system for describing plots in terms of their components.

Every ggplot2 plot has:
1. **Data** — the tibble you are plotting
2. **Aesthetics** (`aes()`) — which variables map to which visual properties (x-axis, y-axis, color, size)
3. **Geometry** (`geom_*()`) — the type of plot (histogram, bar, point, line)

---

## Building a plot layer by layer

```r
library(tidyverse)
library(palmerpenguins)

# A histogram of bill lengths
penguins %>%
  ggplot() +
    geom_histogram(
      mapping = aes(x = bill_length_mm)
    )
```

Notice: ggplot2 uses `+` to add layers — not `%>%`. The pipe hands data to `ggplot()`, then `+` adds each new layer.

---

## Changing the geometry

The same structure works for different plot types — just swap the `geom_`:

```r
# Scatter plot
penguins %>%
  ggplot() +
    geom_point(
      mapping = aes(x = bill_length_mm, y = bill_depth_mm)
    )

# Bar plot
penguins %>%
  ggplot() +
    geom_bar(
      mapping = aes(x = species)
    )
```

---

## Adding color

Map a variable to `color` (or `fill` for bar/histogram) inside `aes()`:

```r
penguins %>%
  ggplot() +
    geom_point(
      mapping = aes(x = bill_length_mm, y = bill_depth_mm, color = species)
    )
```

---

## Knowledge check

Which code block generates a histogram (not a scatter plot)?

```r
# Option A
penguins %>%
  ggplot() +
    geom_histogram(mapping = aes(x = bill_length_mm))

# Option B
penguins %>%
  ggplot() +
    geom_point(mapping = aes(x = bill_length_mm, y = bill_depth_mm))
```

<details>
<summary>Answer</summary>

**Option A.** `geom_histogram()` creates a histogram using one variable. Option B creates a scatter plot using two variables.

</details>

---

## Practice

```r
library(tidyverse)
library(palmerpenguins)

# 1. Create a histogram of flipper_length_mm
# Your code here

# 2. Create a scatter plot of bill_length_mm (x) vs body_mass_g (y), colored by species
# Your code here

# 3. Add a title to your scatter plot using + labs(title = "...")
# Your code here
```

---

## Optional video

A short video (~7–8 min) walks through the slides for this lesson and covers the Grammar of Graphics, the three components of every ggplot2 plot, and how to build histograms, scatter plots, and bar charts.

📄 [View the video script](video_scripts/02_ggplot_script.md) · 🖼️ [Download the slides](../slides/02_ggplot.pdf)

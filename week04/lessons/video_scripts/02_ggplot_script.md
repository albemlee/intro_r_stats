# Video Script: Grammar of Graphics and ggplot2

**Estimated length:** 7–8 minutes  
**Slides:** [02_ggplot.pdf](../slides/02_ggplot.pdf)

---

## Introduction

In this lesson, we start building visualizations in R. We'll use `ggplot2` — the tidyverse's visualization package — which is built around a concept called the Grammar of Graphics. By the end, you'll understand the three essential building blocks of every ggplot2 plot and be able to build several common chart types.

---

## [SLIDE: Grammar of Graphics]

`ggplot2` implements the **Grammar of Graphics** — a framework for describing any plot in terms of its components. The idea is that every visualization, no matter how complex, can be broken down into the same fundamental pieces.

In `ggplot2`, every plot needs three things:

1. **Data** — the tibble you're plotting
2. **Aesthetics** (`aes()`) — which columns map to which visual properties: the x-axis, y-axis, color, size
3. **Geometry** (`geom_*()`) — the type of mark: histogram, bar, point, line

That's the full grammar. Everything else is optional customization.

---

## [SLIDE: Two Examples Side by Side]

Here are two plots using the same structure but different geometries:

```r
# Histogram (one variable)
penguins %>%
  ggplot() +
    geom_histogram(
      mapping = aes(x = bill_length_mm)
    )

# Scatter plot (two variables)
penguins %>%
  ggplot() +
    geom_point(
      mapping = aes(x = bill_length_mm, y = bill_depth_mm)
    )
```

Notice the pattern: pipe the data into `ggplot()`, then use `+` to add a geometry layer. The `+` in ggplot2 plays the same role the `%>%` plays in dplyr — it adds the next piece. But these are not interchangeable. `%>%` passes data; `+` adds a plot layer.

---

## The Three-Step Template

Every ggplot2 plot you write follows this template:

```r
data %>%
  ggplot() +
    geom_*(mapping = aes(...))
```

To change the plot type, swap the `geom_`. To add more visual information, add more mappings inside `aes()`.

---

## Adding Color

Map a variable to `color` or `fill` inside `aes()` to color by group:

```r
penguins %>%
  ggplot() +
    geom_point(
      mapping = aes(x = bill_length_mm, y = bill_depth_mm, color = species)
    )
```

When the mapping goes inside `aes()`, the color varies by data. If you set `color = "blue"` outside `aes()`, the whole plot is that single color.

---

## [SLIDE: You Don't Need to Memorize Every Visualization]

One thing worth saying explicitly: you don't need to memorize every chart type in ggplot2. There are dozens. What matters is knowing the pattern — data, aesthetics, geometry — and knowing how to look things up.

The **R Graph Gallery** (r-graph-gallery.com) is an excellent resource. It shows you what a chart looks like and gives you the code to reproduce it. When you need a chart you haven't built before, go there first.

---

## [SLIDE: Knowledge Check]

Which of these code blocks produces a histogram?

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

**Option A** uses `geom_histogram()` and maps one variable to the x-axis. Option B uses `geom_point()` and maps two variables — that's a scatter plot.

---

## Closing

ggplot2 has a learning curve, but once you internalize the grammar — data, aesthetics, geometry — you can build almost any chart by finding the right `geom_` and mapping the right variables. In the next two lessons, we'll apply this to categorical and continuous variables specifically.

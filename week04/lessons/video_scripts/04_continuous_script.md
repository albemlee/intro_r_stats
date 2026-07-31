# Video Script: Describing Continuous Variables

**Estimated length:** 6–7 minutes  
**Slides:** [04_continuous.pdf](../slides/04_continuous.pdf) · [Bonus: 05_lazy_exploration.pdf](../slides/05_lazy_exploration.pdf)

---

## Introduction

This lesson is about continuous variables — measurements that can take any value on a scale, like bill length in millimeters or body mass in grams. The key principle here is simple: **always plot before you summarize.** The shape of your distribution tells you which statistics are meaningful.

---

## [SLIDE: Demo — Create a Histogram]

The standard starting point for a continuous variable is a histogram:

```r
penguins %>%
  ggplot() +
    geom_histogram(
      mapping = aes(x = bill_length_mm),
      bins = 30
    )
```

A histogram shows you the distribution of your data — where values cluster, whether there are outliers, and whether the distribution is symmetric or skewed.

Don't skip this step. Summary statistics alone can hide important patterns in your data.

---

## [SLIDE: Choosing Summary Statistics Based on Shape]

Once you've plotted your data, use the distribution shape to decide which statistics to report:

**If the distribution is approximately normal** — bell-shaped and symmetric — report the **mean** and **standard deviation**. These two numbers fully characterize a normal distribution.

**If the distribution is skewed** — with a long tail on one side — report the **five-number summary**: minimum, Q1, median, Q3, and maximum. The mean is pulled by the tail and misrepresents the typical value. The median is more robust.

In R:

```r
# Normal distribution
mean(penguins$bill_length_mm, na.rm = TRUE)
sd(penguins$bill_length_mm, na.rm = TRUE)

# Any distribution — especially skewed
summary(penguins$bill_length_mm)
```

---

## [SLIDE: Knowledge Check]

You plot a histogram of hospital stay duration and find it's strongly right-skewed — most patients have short stays, but a few had very long ones. Should you report mean and SD, or the five-number summary?

**The five-number summary.** The mean will be pulled upward by the long-stay outliers and won't represent the typical patient's experience. The median and IQR give a more accurate picture.

---

## Computing Summaries by Group

Often you want to describe a variable separately for each group:

```r
penguins %>%
  group_by(species) %>%
  summarize(
    mean_bill = mean(bill_length_mm, na.rm = TRUE),
    sd_bill   = sd(bill_length_mm, na.rm = TRUE)
  )
```

And to visualize each group separately, `facet_wrap()` creates side-by-side panels:

```r
penguins %>%
  ggplot() +
    geom_histogram(mapping = aes(x = bill_length_mm), bins = 20) +
    facet_wrap(~species)
```

This lets you check whether the distribution shape — and therefore the appropriate statistics — is the same across groups.

---

## Bonus: Lazy Exploration with ggpairs

If you want a quick look at all pairwise relationships in your dataset, the `ggpairs()` function from the `GGally` package creates a matrix of plots automatically:

```r
library(GGally)

penguins %>%
  select(bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g) %>%
  ggpairs()
```

This isn't a substitute for careful univariable description — but it's a great way to get oriented to a new dataset quickly before deciding where to focus your analysis. The slides include a short demo of this approach.

---

## Closing

Plot first, summarize second. The distribution shape is the most important thing a histogram tells you, and getting this right makes all your downstream statistics more credible. This wraps up Week 4's descriptive methods. In Week 5, we move into inferential statistics — using the sample to make honest claims about the population.

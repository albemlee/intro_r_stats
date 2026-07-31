# Comparing Groups

## Comparing two groups

### t-test (parametric — assumes normality)

```r
library(tidyverse)
library(palmerpenguins)

# Compare bill length between male and female Gentoo penguins
gentoo <- penguins %>%
  filter(species == "Gentoo", !is.na(sex))

t.test(bill_length_mm ~ sex, data = gentoo)
```

### Wilcoxon rank-sum test (non-parametric)

```r
wilcox.test(bill_length_mm ~ sex, data = gentoo)
```

---

## Comparing a categorical outcome: chi-squared test

Use `chisq.test()` to test whether two categorical variables are independent:

```r
# Is species independent of sex?
chisq.test(table(penguins$species, penguins$sex))
```

---

## Comparing 3+ groups: ANOVA

```r
# Compare body mass across all three species
model <- aov(body_mass_g ~ species, data = penguins)
summary(model)
```

A significant ANOVA tells you *at least one group differs* — not which one. Run pairwise tests to find out:

```r
pairwise.t.test(penguins$body_mass_g, penguins$species,
                p.adjust.method = "bonferroni")
```

The **Bonferroni correction** adjusts the significance threshold to account for multiple comparisons, reducing the chance of a false positive.

---

## Knowledge check

**True or False:** You can use non-parametric tests to compare the flipper length of male and female Gentoo penguins, even if the data is normally distributed.

<details>
<summary>Answer</summary>

**True.** Non-parametric tests can always be used — they make fewer assumptions. However, parametric tests are generally more powerful (better at detecting real differences) when their assumptions are met, so they are preferred when normality holds.

</details>

---

## Practice

```r
library(tidyverse)
library(palmerpenguins)

# 1. Check normality of flipper_length_mm for Adelie penguins (histogram + Shapiro-Wilk)
# Your code here

# 2. Based on the result, run the appropriate test to compare flipper length
#    between male and female Adelie penguins
# Your code here

# 3. State H₀, Hₐ, your p-value, and your conclusion in plain language
# (Write as a comment in your R script)
```

---

## Optional video

A video (~10–12 min) walks through the slides for this lesson and covers the t-test, Wilcoxon rank-sum test, chi-squared test, one-way ANOVA with pairwise post-hoc tests, and two-way ANOVA for multiple grouping factors.

📄 [View the video script](video_scripts/06_comparing_groups_script.md) · 🖼️ [Download slides (two groups)](../slides/07_compare_two.pdf) · [Download slides (3+ groups)](../slides/09_compare_over_two.pdf)

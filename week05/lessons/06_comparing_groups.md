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

## Slides

🖼️ [Download slides (two groups)](../slides/07_compare_two.pdf) · [Download slides (3+ groups)](../slides/09_compare_over_two.pdf)

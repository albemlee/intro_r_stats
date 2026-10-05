# Comparing Groups

## Comparing two groups

### t-test (parametric - compares means)

```r
library(tidyverse)
library(palmerpenguins)

# Compare bill length between male and female Gentoo penguins
gentoo <- penguins %>%
  filter(species == "Gentoo", !is.na(sex))

t.test(bill_length_mm ~ sex, data = gentoo)
```

### Wilcoxon rank-sum test (non-parametric - compares distributions between groups)

```r
wilcox.test(bill_length_mm ~ sex, data = gentoo)
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

The **Bonferroni correction** adjusts for multiple comparisons, reducing the chance of false-positive findings.

---

## Knowledge check

**Which test would you use?** If you want to compare mean bill length between male and female Gentoo penguins.

<details>
<summary>Answer</summary>

**Two-sample t-test.** The outcome (bill length) is continuous, there are two groups (male and female), and the goal is to compare their means.

</details>

---

## Slides

🖼️ [Download slides (two groups)](../slides/07_compare_two.pdf) · [Download slides (3+ groups)](../slides/09_compare_over_two.pdf)

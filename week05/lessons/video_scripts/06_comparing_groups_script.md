# Video Script: Comparing Groups

**Estimated length:** 10–12 minutes  
**Slides:** [07_compare_two.pdf](../slides/07_compare_two.pdf) · [09_compare_over_two.pdf](../slides/09_compare_over_two.pdf)

---

## Introduction

This lesson puts hypothesis testing into practice. We'll run tests to compare groups — starting with two groups, then extending to three or more. By the end, you'll know which test to reach for depending on how many groups you have and whether your data meets the normality assumption.

---

# Part 1: Comparing Two Groups

## [SLIDE: Types of Tests — Two Groups]

When comparing a continuous variable between two groups, you have two options:

The **t-test** is parametric — it assumes the data in each group is approximately normally distributed. It's more powerful when that assumption holds.

The **Wilcoxon rank-sum test** is non-parametric — no normality assumption. Use it when your data is skewed or the normality assumption is violated.

---

## Running a t-test in R

```r
gentoo <- penguins %>%
  filter(species == "Gentoo", !is.na(sex))

t.test(bill_length_mm ~ sex, data = gentoo)
```

The formula `bill_length_mm ~ sex` means: compare bill length between the two levels of sex. The output gives you the test statistic, degrees of freedom, p-value, and a confidence interval for the difference in means.

---

## Running a Wilcoxon Rank-Sum Test

```r
wilcox.test(bill_length_mm ~ sex, data = gentoo)
```

The syntax is identical — same formula, different function. The interpretation is similar: a small p-value gives evidence against the null hypothesis of no difference between groups.

---

## Comparing Categorical Outcomes: Chi-Squared Test

When both variables are categorical — for example, testing whether species and sex are independent — use `chisq.test()`:

```r
chisq.test(table(penguins$species, penguins$sex))
```

`table()` creates a contingency table, and `chisq.test()` tests whether the two variables are independent. A small p-value suggests the variables are associated.

---

# Part 2: Comparing More Than Two Groups

## [SLIDE: Comparing More Than 2 Groups — ANOVA]

What if you have three or more groups? Running multiple t-tests — one for each pair — inflates the probability of finding a false positive. This is the multiple comparisons problem.

The solution for three or more groups is **ANOVA** (Analysis of Variance):

```r
model <- aov(body_mass_g ~ species, data = penguins)
summary(model)
```

ANOVA tests the null hypothesis that all group means are equal. A significant result tells you *at least one group is different* — but not which one.

---

## [SLIDE: Post-Hoc Pairwise Tests]

To find which groups differ, you need to run pairwise comparisons after a significant ANOVA. But now you're doing multiple tests — which brings back the multiple comparisons problem.

The **Bonferroni correction** adjusts the significance threshold to control the familywise error rate — the probability of at least one false positive across all your comparisons:

```r
pairwise.t.test(penguins$body_mass_g, penguins$species,
                p.adjust.method = "bonferroni")
```

---

## [SLIDE: Familywise Error Rate and Bonferroni Correction]

Here's why this matters. If you run 20 tests at α = 0.05, you'd expect at least one false positive by chance even if nothing is truly different. The Bonferroni correction adjusts each test's significance threshold to keep the overall false positive rate controlled.

The tradeoff: Bonferroni is conservative. It reduces false positives but also reduces power — you're more likely to miss real differences. Use it when the cost of a false positive is high.

---

## [SLIDE: Two-Way ANOVA]

The slides also introduce **Two-Way ANOVA**, which applies when you have two grouping factors rather than one.

For example, if you want to compare flipper size across all combinations of species (3 levels) and sex (2 levels), treating this as a one-way ANOVA with 6 groups loses important information about the structure of the data. Two-way ANOVA handles this properly — it tests for main effects of each factor and whether the factors interact with each other.

As a general rule:
- 1 grouping factor → one-way ANOVA
- 2 grouping factors → two-way ANOVA
- X grouping factors → X-way ANOVA

The null hypotheses expand accordingly: no main effect of factor A, no main effect of factor B, no interaction between A and B.

---

## Knowledge Check

True or False: You can always use a non-parametric test instead of a parametric one, regardless of your data.

**True** — you can always use non-parametric tests. However, parametric tests are more powerful when their assumptions are met. If your data is normally distributed, a t-test will detect real differences more reliably than the Wilcoxon rank-sum test. Use parametric tests when the assumptions hold; fall back to non-parametric when they don't.

---

## Closing

Comparing groups is one of the most common tasks in biomedical research. Whether you're comparing two treatment arms with a t-test or six combination groups with a two-way ANOVA, the logic is the same: state your hypotheses, check your assumptions, run the appropriate test, and interpret the result. In the next lesson, we'll discuss what can go wrong — Type I and Type II errors.

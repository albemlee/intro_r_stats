# TA Self-Assessment

This self-assessment is for PROPEL scholars considering a teaching assistant (TA) role for *Introduction to R and Statistics*. It is not graded and does not need to be submitted — it's a tool to help you gauge your own readiness.

Work through all 10 questions **without notes or AI tools**, then check your answers. If you can answer at least 8 of these confidently and correctly, and can explain *why* the answer is correct (not just what it is), you likely have the foundation to help other scholars as a TA. If a topic below is shaky, revisit that week's lessons before applying.

The questions move from Week 1 fundamentals to Week 7 survival analysis, roughly in order of difficulty.

---

### 1. Objects and assignment (Week 1)

What are the final values of `a` and `b` after running this code?

```r
a <- 10
a <- a * 2
b <- a - 5
```

<details>
<summary>Answer</summary>

`a = 20` (10 * 2), then `b = 15` (20 - 5). R executes top to bottom, and reassigning `a` overwrites its previous value.

</details>

---

### 2. Data structures (Week 2)

What is the key difference between a **matrix** and a **data frame** in R?

<details>
<summary>Answer</summary>

Both are 2-dimensional, but a matrix requires all values to be the same type, while a data frame allows each column to have a different type (numeric, character, logical, etc.). Data frames are the standard structure for real-world tabular data.

</details>

---

### 3. The pipe and tidyverse verbs (Week 3)

What does the following code do?

```r
penguins %>%
  filter(species == "Gentoo") %>%
  select(bill_length_mm, body_mass_g)
```

<details>
<summary>Answer</summary>

It takes the `penguins` tibble, keeps only rows where `species` is `"Gentoo"` (`filter()`), then keeps only the `bill_length_mm` and `body_mass_g` columns (`select()`). The `%>%` pipe passes the result of each step into the next function as its first argument.

</details>

---

### 4. Joins (Week 3)

A scholar uses `bind_rows()` to combine two tibbles that have different column names and gets a result full of `NA` values. What went wrong, and what should they use instead?

<details>
<summary>Answer</summary>

`bind_rows()` stacks tibbles vertically and requires the **same columns** in both — mismatched columns produce `NA`s. If the tables have different columns linked by a shared key (e.g., an ID column), the scholar should use a **join** (`left_join()`, `inner_join()`, or `full_join()`) instead.

</details>

---

### 5. Grammar of Graphics (Week 4)

Name the three components every `ggplot2` plot needs, and explain what changes if you swap `geom_histogram()` for `geom_point()`.

<details>
<summary>Answer</summary>

Every plot needs **data** (a tibble), **aesthetics** (`aes()`, mapping variables to visual properties like x, y, color), and a **geometry** (`geom_*()`, the type of plot). Swapping `geom_histogram()` (one variable, shows distribution) for `geom_point()` (two variables, shows relationship) changes the plot type but keeps the same data/aesthetics structure — you'd also need to add a `y` mapping since `geom_point()` requires both x and y.

</details>

---

### 6. Confidence intervals (Week 5)

A 95% confidence interval for mean blood pressure is [128, 136]. A scholar interprets this as "there is a 95% probability the true mean falls between 128 and 136." Is this interpretation correct? Why or why not?

<details>
<summary>Answer</summary>

**No.** The true population mean is a fixed (though unknown) value — it either is or isn't in the interval; there's no probability attached to it. The correct interpretation is that if we repeated the sampling process many times and built a confidence interval each time, about 95% of those intervals would contain the true population mean. This is one of the most common misconceptions scholars will bring to office hours, so being able to correct it clearly is an important TA skill.

</details>

---

### 7. Test selection under assumption violations (Week 5)

A scholar wants to compare hospital length of stay between two treatment groups. A histogram of the data shows strong right skew, and a Shapiro-Wilk test returns p < 0.001. Which test should they use, and why not a t-test?

<details>
<summary>Answer</summary>

They should use the **Wilcoxon rank-sum test** (non-parametric). A t-test assumes the underlying data is approximately normally distributed; the skewed histogram and significant Shapiro-Wilk result (p ≤ 0.05, rejecting normality) both indicate that assumption is violated, so a non-parametric alternative that doesn't rely on distributional assumptions is more appropriate.

</details>

---

### 8. Interpreting logistic regression output (Week 6)

A logistic regression predicting depression diagnosis reports `exp(coef) = 1.75` for hypertension diagnosis (p < 0.001). Write a plain-language interpretation, and explain one common mistake scholars make with this number.

<details>
<summary>Answer</summary>

"Patients with a hypertension diagnosis have 1.75 times the odds of a depression diagnosis compared to those without hypertension, and this association is statistically significant." The common mistake is treating an odds ratio like a probability ratio — an OR of 1.75 does **not** mean "75% more likely" in terms of raw probability. Odds and probability are related but distinct, and conflating them is a frequent error worth catching as a TA.

</details>

---

### 9. Model diagnostics and multicollinearity (Week 6)

Why is it a problem if two predictors in a linear regression model are highly correlated with each other (multicollinearity), even if the overall model fits the data well?

<details>
<summary>Answer</summary>

Multicollinearity doesn't necessarily hurt the model's overall predictive fit, but it inflates the standard errors of the correlated coefficients, making individual coefficient estimates unstable and their p-values unreliable. This means you can no longer trust the interpretation of *which* predictor is driving the effect — small changes in the data can swing coefficient estimates substantially, even though the model's overall fit stays about the same.

</details>

---

### 10. Cox regression vs. the log-rank test (Week 7)

A scholar has already run a log-rank test comparing survival between two treatment groups and found a significant difference. Their PI now asks them to also adjust for age and sex. Why can't they just add these to the log-rank test, and what should they use instead?

<details>
<summary>Answer</summary>

The log-rank test only compares survival curves between groups defined by a single categorical variable — it cannot incorporate additional covariates. To adjust for age and sex while estimating the effect of treatment, the scholar needs **Cox proportional hazards regression** (`coxph()`), which can include multiple predictors simultaneously and produces a **hazard ratio** for each one, adjusted for the others. For example, an HR of 0.72 for treatment (adjusting for age and sex) would mean treated patients had 0.72 times the hazard of the outcome compared to untreated patients, holding age and sex constant — a 28% reduction in hazard.

</details>

---

## Scoring yourself

- **9–10 correct, with confident explanations:** You're well-positioned to TA this course.
- **6–8 correct:** Solid foundation — review the specific weeks behind any questions you missed before applying.
- **5 or fewer:** Consider retaking the relevant weeks' lessons and assignments before applying; TAs need to explain these concepts clearly to scholars who are seeing them for the first time.

Being a good TA isn't about getting every question right on the first try — it's about being able to explain *why* an answer is correct in a way that helps another scholar understand it too. If you found yourself able to identify the right answer but struggled to explain the reasoning, that's worth practicing before the term starts.

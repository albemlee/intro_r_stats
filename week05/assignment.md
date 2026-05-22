# Week 5 Assignment — Inferential Statistics

**Due:** Before Week 6 session  
**Submit:** One `.R` script + written conclusion (150–200 words)

---

## Instructions

Using your dataset from Weeks 3–4, identify a research question that can be answered with a hypothesis test.

> 💡 This written conclusion will become the inferential statistics section of your final project. Save it.

---

### Task 1: State your hypotheses

Write your null and alternative hypotheses in **plain language** (as comments in your R script).

Example:
```r
# H₀: Male and female Gentoo penguins have the same mean flipper length
# Hₐ: Male and female Gentoo penguins have different mean flipper lengths
```

### Task 2: Check normality

Run a histogram and Shapiro-Wilk test (if applicable) on the variable of interest. Document your decision about which test to use based on the result.

### Task 3: Run the appropriate test

Choose and run the correct test based on your data type and normality check:
- Continuous + normal: `t.test()` (2 groups) or `aov()` (3+ groups)
- Continuous + not normal: `wilcox.test()`
- Two categorical variables: `chisq.test()`

### Task 4: Written conclusion

Write 150–200 words reporting:
- The test you used and why
- The p-value
- Your conclusion in plain language
- Which type of error (Type I or Type II) you might be making

---

## Submission

Submit your `.R` script and written conclusion via [LMS / email].

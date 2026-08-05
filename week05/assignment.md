# Week 5 Assignment — Inferential Statistics

**Due:** Before Week 6 session  
**Submit:** One `.Rmd` notebook

---

## Instructions

Using your dataset from Weeks 3–4, identify a research question that can be answered with a hypothesis test.

> 💡 This written conclusion can become the inferential statistics section of your final project. Save it.

---

### Task 1: State your hypotheses

Write your null and alternative hypotheses in **plain language** in a prose section of your notebook.

Example:

> H₀: Male and female Gentoo penguins have the same mean flipper length  
> Hₐ: Male and female Gentoo penguins have different mean flipper lengths

### Task 2: Check normality

Run a histogram and/or Shapiro-Wilk test (if applicable) on the variable of interest. In a prose section after the output, document your decision about which test to use based on the result.

### Task 3: Run the appropriate test

Choose and run the correct test based on your data type and normality check:
- Continuous + normal: `t.test()` (2 groups) or `aov()` (3+ groups)
- Continuous + not normal: `wilcox.test()`
- Two categorical variables: `chisq.test()`

### Task 4: Written conclusion

In a prose section at the end of your notebook, write 150–200 words reporting:
- The test you used and why
- The p-value
- Your conclusion in plain language
- Which type of error (Type I or Type II) you might be making

---

## Submission

Submit your `.Rmd` file via [LMS / email]. Name it `week05_[your_last_name].Rmd`.

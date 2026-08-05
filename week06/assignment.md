# Week 6 Assignment — Regression Analysis

**Due:** Before Week 7 session  
**Submit:** One `.Rmd` notebook

---

## Instructions

Using your dataset, fit and interpret a regression model. Choose the model type based on your outcome variable.

> 💡 This written paragraph can become the regression section of your final project. Save it.

---

### Task 1: Identify your outcome variable

Determine whether your dependent variable is:
- **Continuous** → use linear regression (`glm()`, default family)
- **Binary** → use logistic regression (`glm(..., family = binomial)`)

Show a data check (histogram for continuous; frequency table for binary) confirming your choice. In a prose section, briefly justify your choice of model.

### Task 2: Fit the model

Include at least one independent variable. Show the model code and full output.

### Task 3: Interpret at least two coefficients

In a prose section after the model output, interpret each coefficient (or odds ratio for logistic):
- Name the predictor and outcome
- State the direction and magnitude
- Note whether it is statistically significant

For logistic regression, remember to use `exp(coef(model))` for odds ratios.

### Task 4: Run one diagnostic check

- **Linear regression:** Run `plot(model, which = 1)` and `plot(model, which = 2)`. In a prose section, describe what you see.
- **Logistic regression (multivariable):** Run `car::vif(model)`. In a prose section, note whether any values are concerning.

---

## Written paragraph

Include a final prose section (150–200 words) summarizing:
- Your model (outcome + predictors)
- Key results (coefficient interpretations)
- Any diagnostic concerns

---

## Submission

Submit your `.Rmd` file via [LMS / email]. Name it `week06_[your_last_name].Rmd`.

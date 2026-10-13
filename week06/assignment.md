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
- **Continuous** → use linear regression (`lm()`)
- **Binary** → use logistic regression (`glm(..., family = binomial)`)

Show a data check (histogram for continuous; frequency table for binary) to examine your outcome variable. Briefly explain why you chose linear or logistic regression.

### Task 2: Fit the model

Include at least one independent variable. Show the model code and full output.

### Task 3: Interpret your regression coefficients

Interpret at least one predictor coefficient (or odds ratio for logistic regression). If your model includes multiple predictors, interpret at least two.
- Name the predictor and outcome
- State the direction and magnitude
- Note whether it is statistically significant

For logistic regression, remember to use `exp(coef(model))` for odds ratios.

### Task 4: Run one diagnostic check

- **Linear regression:** Run `plot(model, which = 1)` and `plot(model, which = 2)`.     Describe whether you see any clear patterns or changes in spread in the residuals vs. fitted plot, and whether the residuals appear approximately normally distributed in the Q-Q plot.
- **Logistic regression (multivariable):** Run `car::vif(model)`. Report whether any VIF values are 5 or higher and what this suggests about multicollinearity. Note: If you fit a logistic regression with only one predictor, add a second predictor before checking VIF.

---

## Written paragraph

Include a final prose section (150–200 words) summarizing:
- Your model (outcome + predictors)
- Key results (including direction, magnitude, and statistical significance)
- Any concerns identified by your diagnostic checks

---

## Submission

Submit your .Rmd file via Canvas: https://canvas.ucsf.edu/courses/3084/assignments


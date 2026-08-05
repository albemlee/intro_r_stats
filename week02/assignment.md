# Week 2 Assignment — R Programming Fundamentals

**Due:** Before Week 3 session  
**Submit:** One `.Rmd` notebook

---

## Instructions

Write a single R Markdown notebook that does all of the following.

Use prose sections (outside of code chunks) to explain your thinking where indicated.

### 1. Create a data frame

Create a data frame called `my_df` with at least **3 columns** and **6 rows** representing any real-world scenario you choose (patients, students, recipes, sports teams, etc.).

Requirements:
- At least one column must be **numeric**
- At least one column must be **character**
- Use descriptive column names

### 2. Write a function

Write a function that takes your data frame as input and does **at least two** of the following:

- a) Filters rows using a condition
- b) Adds a new column based on a calculation
- c) Calculates and prints a summary statistic (e.g., mean, count) for one column

### 3. Call your function

Call your function on `my_df` and print the result.

### 4. Explain your code

Above each major code chunk, add a brief prose paragraph (or use chunk labels/comments) explaining **what it does and why** — not just restating the code in English.

---

## Example structure (do not copy — write your own)

````
---
title: "Week 2 Assignment"
author: "Your Name"
---

## Data

Patient data from a fictional clinical study.

```{r create-data}
patient_df <- data.frame(
  patient_id  = c(1, 2, 3, 4, 5, 6),
  age         = c(34, 52, 61, 45, 38, 70),
  diagnosis   = c("hypertension", "diabetes", "hypertension",
                  "healthy", "diabetes", "healthy"),
  systolic_bp = c(142, 118, 155, 108, 130, 145)
)
```

## Function

This function identifies high-risk patients (systolic BP > 140) and returns them as a filtered data frame.

```{r define-function}
summarize_high_risk <- function(df) {
  high_risk <- df[df$systolic_bp > 140, ]
  cat("High-risk patients:", nrow(high_risk), "\n")
  return(high_risk)
}
```

## Result

```{r call-function}
result <- summarize_high_risk(patient_df)
print(result)
```
````

---

## Submission

Submit your `.Rmd` file via [LMS / email]. Name it `week02_[your_last_name].Rmd`.

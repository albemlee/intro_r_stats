# Computer Programming

[Watch Video Lesson](https://media.ucsf.edu/media/Computer+Programming/1_yjhzlwqc)

## What is computer programming?

Computer programming — often called **coding** — is the act of writing instructions that a computer can execute. A program is a sequence of these instructions.

Here is something worth sitting with: **computers include humans.** When you write an R script, it will be read by R (the software) but also by your future self, your collaborators, and anyone who reviews your work. Code that only R can understand is not good code.

> Write your programs so that humans can read them just as easily as computers can.

---

## R scripts

An **R script** is a plain text file (ending in `.R`) that contains a sequence of R commands. You write commands in the Script editor and run them — either line by line or all at once.

Here is an example of a R script:

```r
# Calculate the average age of patients in our study
patient_ages <- c(34, 52, 61, 45, 38, 70, 29)

# Compute and print the mean
mean_age <- mean(patient_ages)
print(mean_age)
```

Notice:
- Lines starting with `#` are **comments** — R ignores them, but humans read them
- Variable names are descriptive (`patient_ages`, not `x`)

---

## Why readable code matters

Imagine you write a 200-line analysis script today. Six months later, your PI asks you to explain how you calculated a result. If your script is full of cryptic variable names and no comments, you will spend hours figuring out what your past self did.

Readable code is a form of scientific documentation.

---

## Knowledge check

**True or False:** My R scripts don't need to be interpretable by anyone but me and R.

<details>
<summary>Answer</summary>

**False.** You should strive to make your programs interpretable to all "computers" — including human readers. Your collaborators, reviewers, and future self all need to understand your code.

</details>

---

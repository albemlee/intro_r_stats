# Functions

## What are functions?

A **function** is a named block of code that performs a specific task on a set of inputs and returns a result. You have already used built-in functions like `print()`, `mean()`, and `sqrt()`.

```r
x <- 1
y <- 2
z <- sum(x, y)   # sum() is a built-in function
print(z)         # [1] 3
```

The inputs to a function are called **arguments**. The value it produces is called the **return value**.

---

## You do not need to memorize functions

R has thousands of functions. Nobody memorizes them all. What matters is knowing how to look them up.

In RStudio, type `?` followed by a function name in the Console to open its documentation:

```r
?mean
?sqrt
?sum
```

The Help pane (bottom right) will show: what the function does, its arguments, and examples.

---

## Defining your own functions

You can write custom functions using the `function()` keyword:

```r
# Define a function that converts between inches and centimeters
convert_in_cm <- function(measurement, unit) {
  if (unit == "in") {
    conversion <- measurement * 2.54
  } else if (unit == "cm") {
    conversion <- measurement / 2.54
  }
  return(conversion)
}

# Call the function
result <- convert_in_cm(measurement = 5, unit = "in")
print(result)   # [1] 12.7
```

Breaking this down:

| Part | What it does |
|------|-------------|
| `convert_in_cm <-` | Stores the function in an object |
| `function(measurement, unit)` | Declares the arguments |
| `{ ... }` | The body — code that runs when called |
| `return(conversion)` | Sends the result back to the caller |

---

## Functions are reusable

Once defined, you can call a function as many times as you need:

```r
convert_in_cm(measurement = 12, unit = "in")   # 30.48
convert_in_cm(measurement = 100, unit = "cm")  # 39.37
```

This is the key benefit: write the logic once, use it many times.

---

## Packages: functions written by other people

`print()`, `mean()`, and `sqrt()` come built into R, but most functions you will use in this course do not. They live in **packages** — collections of functions (and sometimes data) that someone else wrote and shared, so you don't have to write everything from scratch.

Two separate steps are involved in using a package:

1. **Install it** — download the package onto your computer. You only need to do this once.
2. **Load it** — make its functions available in your current R session. You need to do this every time you start a new session.

### Installing a package

Use `install.packages()`, with the package name in quotes:

```r
install.packages("dplyr")
```

Run this in the Console (not in a script file you'll re-run often) — since it only needs to happen once per computer, there's no reason to install the package every time your script runs.

### Loading a package

Use `library()`, with the package name *without* quotes, at the top of your script:

```r
library(dplyr)
```

Once loaded, you can use any function the package provides:

```r
library(dplyr)

# filter() is a function from the dplyr package
filter(mtcars, mpg > 25)
```

If you try to use a package's function without loading it first, R will give you an error like `could not find function "filter"` — a sign you forgot the `library()` call.

### Where do packages come from?

Most packages are hosted on **CRAN** (the Comprehensive R Archive Network), which is what `install.packages()` downloads from by default. Throughout this course, you will regularly install and load packages like `dplyr`, `ggplot2`, and `tidyr`, which are part of a larger collection called the **tidyverse**.

---

## Knowledge check

What does the function below return when called with `evaluate_grade(85)`?

```r
evaluate_grade <- function(grade) {
  if (grade >= 90) {
    return("A")
  } else if (grade >= 80) {
    return("B")
  } else {
    return("C or below")
  }
}
```

<details>
<summary>Answer</summary>

`"B"` — 85 is not ≥ 90, but it is ≥ 80, so the second branch runs.

</details>

---
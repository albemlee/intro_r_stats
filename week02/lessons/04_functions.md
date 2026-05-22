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

## Practice

```r
# Write a function called classify_bill that takes a bill_length_mm argument.
# It should return "Long" if bill_length_mm > 43, and "Short" otherwise.

# Your function definition here


# Test your function with these values:
classify_bill(39.1)   # should return "Short"
classify_bill(47.5)   # should return "Long"
```

---

## Optional video

Search YouTube for **"how to write functions in R"** (~8 min).

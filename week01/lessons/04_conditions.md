# Conditions

## What are conditions?

A **condition** is something that must be `TRUE` for a block of code to run. Conditions let your programs make decisions.

In everyday language:
- "If the temperature drops below 15°F, drip your faucets."
- "If you have a question, raise your hand."

In R:

```r
temperature <- 10

if (temperature < 15) {
  print("Drip your faucets!")
}
# [1] "Drip your faucets!"
```

---

## Boolean values

A **Boolean** is a value that is either `TRUE` or `FALSE`. Conditions evaluate to a Boolean.

```r
1 == 1   # TRUE  (== means "is equal to")
2 < 1    # FALSE
3 >= 3   # TRUE
"a" != "b"  # TRUE (!= means "is not equal to")
```

Common comparison operators:

| Operator | Meaning |
|----------|---------|
| `==` | equal to |
| `!=` | not equal to |
| `<` | less than |
| `>` | greater than |
| `<=` | less than or equal to |
| `>=` | greater than or equal to |

---

## if / else if / else

```r
grade <- 85

if (grade >= 90) {
  print("A")
} else if (grade >= 80) {
  print("B")
} else if (grade >= 70) {
  print("C")
} else {
  print("Below passing")
}
# [1] "B"
```

R checks each condition in order. As soon as one is `TRUE`, it runs that block and skips the rest.

---

## Knowledge check

What are the values of `x` and `y` after this code runs?

```r
x <- 1 == 1
y <- 2 < 1
```

<details>
<summary>Answer</summary>

- `x = TRUE` (1 does equal 1)
- `y = FALSE` (2 is not less than 1)

</details>

---

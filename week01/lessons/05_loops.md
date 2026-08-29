# Loops

[Watch Video Lesson](https://media.ucsf.edu/media/Loops/1_jie0yrsu)

## Why loops exist

Imagine you need to check whether each of 50 patients passes a screening threshold. You could write 50 separate `if` statements — but that is error-prone and tedious. A **loop** lets you repeat the same block of code automatically.

---

## The for loop

A `for` loop runs a block of code once for each item in a sequence:

```r
# Without a loop (repetitive and fragile):
x <- 1
if (x < 7) { x <- x + 1 }
if (x < 7) { x <- x + 1 }
# ... repeated 7 times

# With a loop (clean and scalable):
grades <- c(78, 92, 65, 88, 71)

for (grade in grades) {
  if (grade >= 70) {
    print("Pass")
  } else {
    print("Fail")
  }
}
```

**Reading a for loop aloud:** "For each `grade` in `grades`, check if it passes."

---

## Loop syntax

```r
for (variable in sequence) {
  # code to run for each item
}
```

- `variable` takes the value of each item in `sequence`, one at a time
- `sequence` is usually a vector (we cover vectors in the next lesson)
- The code inside `{ }` runs once per item

---

## Combining loops with conditions

Loops and conditions work naturally together:

```r
species <- c("Adelie", "Chinstrap", "Gentoo", "Adelie")

for (s in species) {
  if (s == "Adelie") {
    print(paste(s, "- most common species"))
  } else {
    print(paste(s, "- other species"))
  }
}
```

---

## Knowledge check

What is the value of `x` after this loop finishes?

```r
x <- 1
for (i in 1:6) {
  if (x < 7) {
    x <- x + 1
  }
}
```

<details>
<summary>Answer</summary>

`x = 7`. The loop runs 6 times. Each time, `x` is less than 7 and gets incremented. After 6 iterations: 1 → 2 → 3 → 4 → 5 → 6 → 7.

</details>

---

# Objects

## What are objects?

In R, an **object** (also called a **variable**) stores a value so you can use it later. You create an object using the **assignment operator** `<-`.

```r
# Assign the result of 3 + 5 to an object called x
x <- 3 + 5

# Print the value stored in x
print(x)
# [1] 8
```

Think of an object as a labeled box. You put a value in the box (`<-`), give it a name, and then refer to it by name whenever you need it.

---

## Objects can be updated

When you assign a new value to an existing object, the old value is replaced:

```r
x <- 3 + 5   # x is now 8
x <- x - 4   # x is now 4 (8 - 4)
y <- x + 1   # y is now 5

print(x)     # [1] 4
print(y)     # [1] 5
```

R executes code **sequentially** — line by line, top to bottom. The value of `x` when `y` is calculated is 4, not 8.

---

## Comments

Lines that begin with `#` are **comments**. R ignores them entirely — they exist for human readers.

```r
# This is a comment — R skips this line
x <- 10  # You can also add comments at the end of a line
```

Use comments generously. Explain *why* you are doing something, not just *what* you are doing.

---

## Naming rules and recommendations

**Rules (R will give you an error if you break these):**

- No spaces: `num obj` ✗ → `num_obj` ✓
- No mathematical operators: `num-obj` ✗
- Cannot start with an underscore or number: `_obj` ✗, `2obj` ✗
- Case sensitive: `my_obj` and `My_obj` are different objects

**Recommendations:**

- Use descriptive names: `patient_age` is clearer than `x`
- Use `snake_case` (lowercase with underscores): `mean_bill_length`
- Keep names short but meaningful

---

## Knowledge check

Trace through this code. What are the final values of `x` and `y`?

```r
x <- 3 + 5
x <- x - 4
y <- x + 1
print(x)
print(y)
```

<details>
<summary>Answer</summary>

- After line 1: `x = 8`
- After line 2: `x = 4` (x is reassigned)
- After line 3: `y = 5`
- `print(x)` → `4`
- `print(y)` → `5`

</details>

---
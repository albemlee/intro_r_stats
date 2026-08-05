# Vectors, Matrices, and Data Frames

## Vectors

A **vector** stores a sequence of values of the same type. Create one with `c()` (short for "combine"):

```r
# Numeric vector
bill_lengths <- c(39.1, 45.2, 36.7, 50.3, 42.8)

# Character vector
species <- c("Adelie", "Chinstrap", "Gentoo")

# Logical vector
passed <- c(TRUE, FALSE, TRUE, TRUE)
```

### Why vectors matter

Instead of creating a separate object for each value, vectors let you operate on all values at once:

```r
# Without a vector (tedious and error-prone):
grade_1 <- 80
grade_2 <- 95
grade_1 <- grade_1 + 5
grade_2 <- grade_2 + 5

# With a vector (clean):
grades <- c(80, 95, 90, 90)
grades <- grades + 5   # adds 5 to every element
# [1] 85 100 95 95
```

### Indexing vectors

Access individual elements using `[ ]`:

```r
grades <- c(80, 95, 90, 90)
grades[1]      # [1] 80  (first element)
grades[2:4]    # [1] 95 90 90  (elements 2 through 4)
```

---

## Matrices

A **matrix** stores values in a 2-dimensional grid. All values must be the same type.

```r
# Create a 4x2 matrix
grades_matrix <- matrix(
  c(80, 90, 85, 85, 90, 90, 85, 100),
  nrow = 4,
  ncol = 2
)

# Index a matrix: [row, column]
grades_matrix[1, 2]   # row 1, column 2 → 90
grades_matrix[, 1]    # all rows, column 1
grades_matrix[2, ]    # row 2, all columns
```

---

## Data frames

A **data frame** is the most important data structure for real-world analysis. Like a matrix, it is 2-dimensional — but **each column can be a different type**.

```r
# A data frame with mixed column types
penguins_small <- data.frame(
  species       = c("Adelie", "Chinstrap", "Gentoo"),
  bill_length   = c(39.1, 45.2, 47.3),
  is_large      = c(FALSE, FALSE, TRUE)
)

# Access a column with $
penguins_small$species        # character vector
penguins_small$bill_length    # numeric vector

# Index like a matrix
penguins_small[1, ]           # first row
penguins_small[, "species"]   # species column
```

---

## Choosing the right structure

| Structure | Dimensions | Types | Use when... |
|-----------|-----------|-------|-------------|
| Object | 1 value | Any | Storing a single result |
| Vector | 1D | All same | A list of values of one type |
| Matrix | 2D | All same | Grid of numbers (e.g., pixel values) |
| Data frame | 2D | Mixed | Real datasets with multiple variable types |

> In practice, you will work with data frames almost exclusively once you start doing data analysis on tabular data.

---

## Knowledge check

**True or False:** Columns in a data frame must all be the same type.

<details>
<summary>Answer</summary>

**False.** Data frames can contain columns of different types — that is one of their key advantages over matrices.

</details>

---
# Data Frames and Tibbles

## From data frames to tibbles

You already know what a data frame is. A **tibble** is the tidyverse's improved version of a data frame. Tibbles behave almost identically, but with two key differences.

### Nicer printing

When you print a tibble, R shows only the first 10 rows and as many columns as fit on screen — along with column types. This prevents the console from being flooded with output.

```r
library(tidyverse)
library(palmerpenguins)

# penguins is a tibble
penguins
```

### Slightly different subsetting

```r
# [ ] on a tibble always returns a tibble
penguins[1:3, "species"]       # returns a 3-row tibble

# [[ ]] returns a vector (like base R)
penguins[["species"]]          # returns a character vector

# $ also returns a vector
penguins$species               # returns a character vector
```

> **Watch out:** Some older R code expects a plain data frame, not a tibble. If you run into unexpected errors with older functions, try wrapping your tibble with `as.data.frame()`.

---

## Knowledge check

**True or False:** Columns in a data frame must all be of the same type.

<details>
<summary>Answer</summary>

**False.** Both data frames and tibbles can contain columns of different types — numeric, character, logical, and more.

</details>

# Subsetting Tibbles: select() and filter()

## select() — choose columns

`select()` keeps the columns you name and drops the rest:

```r
library(tidyverse)
library(palmerpenguins)

# Keep only species and bill_length_mm
penguins %>%
  select(species, bill_length_mm)
```

You can also drop columns using `-`:

```r
penguins %>%
  select(-year, -island)
```

---

## filter() — choose rows

`filter()` keeps rows where a condition is `TRUE`:

```r
# Keep only Adelie penguins
penguins %>%
  filter(species == "Adelie")

# Keep penguins with bill length greater than 45mm
penguins %>%
  filter(bill_length_mm > 45)
```

### Combining conditions

Use `&` (AND) and `|` (OR) to combine conditions:

```r
# Adelie penguins with bill length > 40mm
penguins %>%
  filter(species == "Adelie" & bill_length_mm > 40)

# Penguins that are either Adelie or Chinstrap
penguins %>%
  filter(species == "Adelie" | species == "Chinstrap")
```

---

## Chaining with the pipe

`select()` and `filter()` combine naturally:

```r
# Filter to Gentoo penguins, then keep only species and body_mass_g
penguins %>%
  filter(species == "Gentoo") %>%
  select(species, body_mass_g)
```

---

## Knowledge check

Translate this plain-English instruction into tidyverse code:

> "Select the species and flipper length of penguins that weighed more than 4500g."

<details>
<summary>Answer</summary>

```r
penguins %>%
  filter(body_mass_g > 4500) %>%
  select(species, flipper_length_mm)
```

</details>

---

## Practice

```r
library(tidyverse)
library(palmerpenguins)

# 1. Select only the species, island, and sex columns
# Your code here

# 2. Filter to only female penguins
# Your code here

# 3. Filter to Chinstrap penguins on Dream island, keeping only
#    species, island, and bill_length_mm
# Your code here
```

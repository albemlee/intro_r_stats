# The Tidyverse and the Pipe Operator

## What is the tidyverse?

The **tidyverse** is a collection of R packages that share a common philosophy: code should read like a description of what you are doing with your data.

Compare these two approaches to the same task — "select the names of students with a final grade of 90 or higher":

```r
# Base R approach
student_df[student_df$final_grade >= 90, "full_name"]

# Tidyverse approach
student_df %>%
  filter(final_grade >= 90) %>%
  select(full_name)
```

The tidyverse version reads almost like English. That is the goal.

---

## The pipe operator: %>%

The **pipe** (`%>%`) takes whatever is on its left and passes it as the first argument to the function on its right.

Read `%>%` aloud as **"then"**:

```r
penguins %>%           # start with penguins, THEN
  filter(year == 2008) %>%   # keep only 2008 rows, THEN
  select(species, bill_length_mm)  # keep only these columns
```

Reading aloud: "Take penguins, then filter to 2008, then select species and bill length."

---

## Loading the tidyverse

```r
library(tidyverse)
```

This loads all core tidyverse packages at once, including `dplyr` (data manipulation) and `ggplot2` (visualization).

---

## Knowledge check

Which of these uses the tidyverse approach?

```r
# Option A
prescriptions_df <- prescriptions_df %>%
  filter(RXDUSE == 1) %>%
  select(SEQN, RXDDRUG)

# Option B
prescriptions_df <- prescriptions_df[
  prescriptions_df$RXDUSE == 1,
  c("SEQN", "RXDDRUG")
]
```

<details>
<summary>Answer</summary>

**Option A.** It uses `%>%`, `filter()`, and `select()` — all tidyverse functions.

</details>

---

## Slides

🖼️ [Download the slides](../slides/02_tidyverse.pdf)

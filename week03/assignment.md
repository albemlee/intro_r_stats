# Week 3 Assignment — Data Manipulation with the Tidyverse

**Due:** Before Week 4 session  
**Submit:** One `.R` script file + a brief written note (2–3 sentences)

---

## Instructions

Find a publicly available dataset (CSV format) with at least **4 columns** and **50 rows**.

**Suggested sources:**
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [CDC Open Data](https://data.cdc.gov/)
- [data.gov](https://data.gov/)
- Palmer Penguins (built into R): `library(palmerpenguins); data(penguins)`

> 💡 **Project tip:** If you find a dataset you find interesting, consider using it for your final project.

---

### Task 1: Filter and select

Write a tidyverse pipeline that filters your data to a meaningful subset of rows and keeps only relevant columns. Add a comment explaining the research question you are addressing.

### Task 2: mutate()

Create at least one new column using `mutate()`. The new column should be derived from existing columns in a meaningful way.

### Task 3: group_by() and summarize()

Produce a grouped summary table. Your summary should include at least one count and one mean (or other aggregate statistic).

### Task 4: Comments

Add a plain-English comment **above each pipeline step** explaining what it does.

---

## Written note

In 2–3 sentences, describe:
- What dataset you chose and where it came from
- What you found interesting about the summary table from Task 3

---

## Submission

Submit your `.R` script and written note (in the same document or as a comment at the top of the script) via [LMS / email].

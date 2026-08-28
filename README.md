# Introduction to R and Statistics for PROPEL

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Lead Instructors:** 
    Albert Lee · albert.lee8@ucsf.edu
    Karla Lindquist · karla.lindquist@ucsf.edu
**Program:** UCSF PROPEL  
**Duration:** 8 weeks

---

## About this course

Welcome, PROPEL scholars! Over 8 weeks you will learn R programming and applied statistics — skills you can use directly in your own research. The course is structured as a **reverse classroom**: you read and work through lessons before each session, and class time is spent on hands-on activities and discussion.

By the end of the course, you will be able to import and wrangle a real dataset, produce publication-quality visualizations, run inferential tests, build regression models, and interpret survival curves. You will put these skills together in a **final project**: working in a small group, you will choose a publicly available dataset, conduct an end-to-end analysis in R, and present your findings to the class.

Every week follows the same pattern:

| Step | What | Where |
|------|------|--------|
| 1 | Read the lesson(s) for the week | `weekXX/lessons/` |
| 2 | Follow along if there is a notebook | `weekXX/notebook/
| 3 | Attend the 90-minute session | In person |
| 4 | Complete the assignment | `weekXX/assignment.md` |

---

## AI tools

You have access to **UCSF ChatGPT Enterprise** — a HIPAA-compliant AI platform appropriate for use with UCSF data. Use it to understand error messages, explore concepts, and brainstorm analysis approaches. If you use it for assignments, document your prompts.

- Access & login: [ChatGPT Enterprise FAQs](https://ai.ucsf.edu/ucsf-chatgpt-enterprise-faqs#paragraph-2271)
- Required training: [UCSF SPARK-AI Foundations](https://ai.ucsf.edu/ucsf-spark-ai-foundations)
- Support: chatgpt.support@ucsf.edu

---

## Course map

### Week 1 — Setup, Tools, and R Basics
*Install R, RStudio, and the tidyverse. Objects, conditions, and loops. Introduction to UCSF ChatGPT Enterprise.*

| Lessons |
|---------|
| [R and RStudio](week01/lessons/01_r_and_rstudio.md) |
| [Computer Programming](week01/lessons/02_computer_programming.md) |
| [Objects](week01/lessons/03_objects.md) |
| [Conditions](week01/lessons/04_conditions.md) |
| [Loops](week01/lessons/05_loops.md) |

**Supplement:** [UCSF ChatGPT Enterprise](week01/supplement/chatgpt_enterprise.md)  
**Assignment:** [Week 1 Assignment](week01/assignment.md)

---

### Week 2 — Functions and Data Structures
*Functions, vectors, matrices, data frames.*

| Lessons |
|---------|
| [Functions](week02/lessons/01_functions.md) |
| [Vectors, Matrices, and Data Frames](week02/lessons/02_data_structures.md) |

**Notebook:** [Week 2 Notebook](week02/notebook/week02_r_fundamentals.Rmd)  
**Assignment:** [Week 2 Assignment](week02/assignment.md)

---

### Week 3 — Data Manipulation with the Tidyverse
*Tibbles, the pipe operator, select, filter, mutate, group_by, summarize, joins.*

| Lessons |
|---------|
| [Data Frames and Tibbles](week03/lessons/01_tibbles.md) |
| [The Tidyverse and the Pipe](week03/lessons/02_tidyverse.md) |
| [Subsetting with select() and filter()](week03/lessons/03_subset.md) |
| [Adding Variables with mutate()](week03/lessons/04_mutate.md) |
| [Aggregating with group_by() and summarize()](week03/lessons/05_summarize.md) |
| [Combining Data: bind_rows() and Joins](week03/lessons/06_joins.md) |

**Notebook:** [Week 3 Notebook](week03/notebook/week03_tidyverse.Rmd)  
**Assignment:** [Week 3 Assignment](week03/assignment.md)

---

### Week 4 — Descriptive Statistics and Data Visualization
*Descriptive vs. inferential statistics, ggplot2, categorical and continuous variables.*

| Lessons |
|---------|
| [Descriptive Statistics](week04/lessons/01_descriptive_stats.md) |
| [Grammar of Graphics and ggplot2](week04/lessons/02_ggplot.md) |
| [Describing Categorical Variables](week04/lessons/03_categorical.md) |
| [Describing Continuous Variables](week04/lessons/04_continuous.md) |

**Notebook:** [Week 4 Notebook](week04/notebook/week04_descriptive_stats.Rmd)  
**Assignment:** [Week 4 Assignment](week04/assignment.md)

---

### Week 5 — Inferential Statistics and Hypothesis Testing
*Point estimates, standard error, confidence intervals, hypothesis testing, Type I/II errors, comparing groups.*

| Lessons |
|---------|
| [Inferential Statistics](week05/lessons/01_inferential_stats.md) |
| [Point Estimate and Standard Error](week05/lessons/02_point_estimate_se.md) |
| [Confidence Intervals](week05/lessons/03_confidence_intervals.md) |
| [Hypothesis Testing](week05/lessons/04_hypothesis_testing.md) |
| [Assumptions and Test Selection](week05/lessons/05_assumptions.md) |
| [Comparing Groups](week05/lessons/06_comparing_groups.md) |
| [Type I and Type II Errors](week05/lessons/07_errors.md) |

**Notebook:** [Week 5 Notebook](week05/notebook/week05_inferential_stats.Rmd)  
**Assignment:** [Week 5 Assignment](week05/assignment.md)

---

### Week 6 — Linear and Logistic Regression
*Linear regression, logistic regression, model interpretation, diagnostics, multicollinearity.*

| Lessons |
|---------|
| [Linear Regression](week06/lessons/01_linear_regression.md) |
| [Logistic Regression](week06/lessons/02_logistic_regression.md) |
| [Model Diagnostics](week06/lessons/03_diagnostics.md) |

**Notebook:** [Week 6 Notebook](week06/notebook/week06_regression.Rmd)  
**Assignment:** [Week 6 Assignment](week06/assignment.md)

---

### Week 7 — Survival Analysis
*Kaplan-Meier curves, log rank test, Cox proportional hazards regression.*

| Lessons |
|---------|
| [Survival Analysis Overview](week07/lessons/01_survival_overview.md) |
| [Kaplan-Meier Curves](week07/lessons/02_kaplan_meier.md) |
| [Log Rank Test](week07/lessons/03_logrank.md) |
| [Cox Proportional Hazards Regression](week07/lessons/04_cox.md) |

**Notebook:** [Week 7 Notebook](week07/notebook/week07_survival.Rmd)  
**Assignment:** [Week 7 Assignment](week07/assignment.md)

---

### Week 8 — Final Project Presentations
*No pre-class material. See the final project description for deliverables.*

- [Final Project Description](week08/final_project.md)

---

## Becoming a helper

Have prior programming or statistics experience and interested in helping out your classmates? Try the [Helper self-assessment](self_assessment.md) — 10 questions spanning the full course, from R basics to survival analysis, to help you gauge your readiness.

---

## Final project

In groups of 3–4, you will analyze a publicly available dataset and present your findings in a 2-minute video. See the [final project description](week08/final_project.md) for full details.

**Dataset ideas:** [Kaggle](https://www.kaggle.com/datasets) · [UCI ML Repository](https://archive.ics.uci.edu/) · [data.gov](https://data.gov/) · [CDC Open Data](https://data.cdc.gov/)

---

## How this course was made

This course was developed with the help of [Claude](https://claude.ai) (Anthropic's AI assistant) using a reverse-classroom conversion workflow.

The starting point was a set of existing workshop materials developed by the UCSF Library, available at:
**[UCSF Library R Course Materials](https://courses.ucsf.edu/course/view.php?id=8499)** *(UCSF login required)*

The original workshops covered:

- **R for Everyone** — an introductory workshop covering R fundamentals and the RStudio environment
- **R for Data Manipulation** — a workshop on the tidyverse, data wrangling, and the pipe operator
- **R for Statistics** — a workshop covering descriptive and inferential statistics, regression, and survival analysis

These materials were used as source content. Claude helped restructure them into a flipped/reverse-classroom format suitable for a credit-bearing 8-week course — producing student-facing lesson notes in Markdown, Rmd notebooks, comprehension checks, weekly assignments, and instructor guidance for each week.

---

## License

This course material is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to share and adapt these materials for any purpose, including commercial use, as long as you give appropriate credit. See the [LICENSE](LICENSE) file for full terms.

---

## R resources

- [R for Data Science](https://r4ds.hadley.nz/) — free online book, the definitive tidyverse reference
- [R Graph Gallery](https://r-graph-gallery.com/) — ready-to-run ggplot2 code for dozens of plot types
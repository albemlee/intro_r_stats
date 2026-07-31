# Video Script: Descriptive Statistics

**Estimated length:** 5–6 minutes  
**Slides:** [01_descriptive_stats.pdf](../slides/01_descriptive_stats.pdf)

---

## Introduction

Welcome to Week 4. This week is about describing and visualizing data. Before we get into the mechanics of plots and summary statistics, I want to make sure we're clear on one foundational idea that a lot of researchers blur in practice: the difference between descriptive and inferential statistics.

---

## [SLIDE: Descriptive Stats]

Descriptive statistics describes your sample. That is all it does.

It does not generate conclusions about the world, about the broader population, or about some underlying mechanism. It just tells you what is in your data.

Here is the distinction in action:

> "Chinstrap penguins have longer bills than Adelie penguins."

That sentence sounds like a fact about penguins in general. But what you can actually say — if all you have is a sample — is:

> "In our sample of 344 penguins, Chinstrap penguins have longer bills on average than Adelie penguins."

The first statement is an inferential claim. It requires inferential statistics to support it — which we cover in Week 5. The second statement is descriptive. It's an accurate characterization of what you measured.

Being precise about this distinction is a mark of rigorous research.

---

## [SLIDE: Descriptive Statistics Describes Your Sample]

Let me say it one more time to make it stick: descriptive statistics describes your sample. It does not generate conclusions about underlying phenomena.

When you write up your results, always be explicit about what your data can and cannot tell you.

---

## [SLIDE: Choosing the Right Summary]

Once we know we're doing descriptive statistics, the next question is: what type of variable are we describing?

For **categorical variables** — like penguin species or patient sex — the standard approach is a bar plot showing counts. That's it. No means, no standard deviations.

For **continuous variables**, the right choice depends on the shape of the distribution. If a histogram shows a normal, bell-shaped curve, use the mean and standard deviation. If the data is skewed — long tail on one side — use the five-number summary instead: minimum, Q1, median, Q3, and maximum.

The rule: always plot your data first, then decide which statistics to report.

---

## Knowledge Check

Here's the knowledge check from your lesson. A researcher analyzes 200 hospital patients and finds 60% have hypertension. Can they conclude that most hospital patients have hypertension?

No. That would overstep the data. What they *can* say is: "In our sample of 200 hospital patients, 60% have a hypertension diagnosis." Whether that generalizes to the broader population of hospital patients requires inferential methods.

---

## Closing

Descriptive statistics is where every analysis begins — and it's often undervalued. Before you run any tests or build any models, you need to understand what your data looks like. In the next lessons, we'll build that understanding through visualization with ggplot2.

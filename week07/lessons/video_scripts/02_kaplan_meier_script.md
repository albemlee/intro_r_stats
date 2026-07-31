# Video Script: Kaplan-Meier Curves

**Estimated length:** 6–7 minutes  
**Slides:** [02_kaplan_meier.pdf](../slides/02_kaplan_meier.pdf)

---

## Introduction

This lesson is about the Kaplan-Meier curve — the standard way to visualize survival data. By the end, you'll know how to read one, how to fit one in R, and what warning signs to look for.

---

## [SLIDE: Kaplan-Meier Curve]

A **Kaplan-Meier (KM) curve** plots the probability of surviving — not experiencing the event — over time. It's a descriptive tool. It tells you what happened in your sample.

Reading the curve:

- The **Y-axis** shows survival probability, from 1.0 (everyone event-free) down to 0 (no one event-free)
- The **X-axis** is time
- Each **downward step** marks a time point where one or more events occurred
- **Flat sections** mean no events happened during that interval
- **Small tick marks** on the curve indicate censored observations — patients who left the study or reached the end without experiencing the event

A key heuristic: **a flatter curve means better prognosis**. The group is maintaining higher survival probability for longer.

---

## [SLIDE: Red Flag — Crossing Curves]

One important warning: if two survival curves **cross each other multiple times**, it's a red flag. This suggests the proportional hazards assumption — the idea that the hazard ratio between groups is constant over time — may be violated. If that assumption doesn't hold, the log rank test and Cox model may not give reliable results, and you'll need to investigate further before proceeding.

---

## Fitting a KM Curve in R

```r
library(survival)

# Fit KM curve stratified by sex
km_fit <- survfit(Surv(mos_to_death, died) ~ female, data = hrs_df)

# Plot
plot(km_fit,
     col = c("blue", "red"),
     xlab = "Months",
     ylab = "Survival probability",
     main = "Survival by sex")
legend("topright", legend = c("Male", "Female"), col = c("blue", "red"), lty = 1)
```

The `Surv(mos_to_death, died)` call creates a survival object: the first argument is time, the second is status (1 = event, 0 = censored). The `~ female` formula stratifies the curve by sex, giving you two separate survival curves on the same plot.

---

## [SLIDE: Demo — Kaplan-Meier Curve]

In the demo, you'll fit and plot the KM curve for the Health and Retirement Study dataset. As you examine the output, pay attention to where the two curves diverge and whether they cross. That will set up the log rank test in the next lesson.

---

## Knowledge Check

A KM plot shows two groups. Group A's curve stays near 0.8 through 24 months. Group B's drops to 0.4 by month 12. What does this tell you?

In this sample, Group A has considerably better survival — a higher proportion remain event-free throughout the study period. This is a descriptive observation. To assess whether the difference is statistically significant — more than we'd expect from sampling variation — we need the log rank test.

---

## Closing

The Kaplan-Meier curve is the first thing you look at in a survival analysis. It gives you a visual sense of the data before running any tests. In the next lesson, we'll use the log rank test to formally compare the two survival curves.

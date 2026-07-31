# Video Script: Survival Analysis Overview

**Estimated length:** 6–7 minutes  
**Slides:** [01_survival_overview.pdf](../slides/01_survival_overview.pdf)

---

## Introduction

Welcome to Week 7 — our final topic: survival analysis. This is a family of methods specifically designed for a type of question that comes up constantly in clinical and epidemiological research: how long until something happens?

---

## [SLIDE: Survival Analysis]

**Survival analysis** studies time until an event occurs. The "event" can be death — which is where the name comes from — but it can also be disease progression, hospital discharge, equipment failure, or any other outcome with a clear start and end point.

Two variables define every survival dataset:

- **Time to event** (or time to censoring): how long until the event happened, or until the observation ended
- **Status**: did the event occur (coded as 1) or is the observation censored (coded as 0)?

---

## [SLIDE: What Is Censoring?]

Censoring is the concept that makes survival analysis different from everything we've covered so far — and it's crucial to understand correctly.

A **censored observation** is one where the event had not yet occurred by the end of the study. The patient was still alive, the disease hadn't progressed, or they left the study early. Their exact time to event is unknown — we only know they survived *at least* until their censoring time.

Censored observations are **not missing data**. They contribute real information: we know the patient was event-free for that much time. If you removed them from the analysis, you'd systematically bias your results toward patients who experienced the event faster — making outcomes look worse than they actually are.

Survival analysis handles censoring correctly by design. Standard regression does not. This is the core reason survival analysis exists as its own toolkit.

---

## [SLIDE: The Three Methods of Survival Analysis]

This week covers three complementary methods:

The **Kaplan-Meier curve** is descriptive. It visualizes the probability of surviving over time in your sample — the same role a histogram plays for a continuous variable.

The **log rank test** is a hypothesis test. It compares survival between two groups — analogous to the t-test for continuous variables.

**Cox proportional hazards regression** is a multivariable regression for survival outcomes. It lets you adjust for confounders and estimate effect sizes — the survival analysis equivalent of logistic regression.

---

## [SLIDE: Data Format]

The data format for survival analysis has two required columns:

```r
hrs_df %>%
  select(mos_to_death, died)
```

`mos_to_death` is the time variable — months from the study start to death or censoring. `died` is the status variable — 1 if the person died during the study, 0 if they were censored.

The `Surv()` function from the `survival` package packages these two columns into a survival object that the analysis functions expect.

---

## Knowledge Check

True or False: We must remove all censored observations before beginning survival analysis.

**False.** Censored observations must be retained and handled by the survival methods. Removing them biases the analysis by eliminating the information those patients contribute about event-free survival time.

---

## Closing

Survival analysis is the right tool whenever your outcome is time-to-event and some observations don't reach the event by the end of your study — which is almost always the case in longitudinal research. In the next lesson, we'll build the Kaplan-Meier curve to visualize survival in our dataset.

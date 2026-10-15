# Survival Analysis Overview

## What is survival analysis?

Survival analysis studies **time until an event occurs** — the event could be death, disease progression, hospital discharge, equipment failure, or any other event of interest.

Two key variables:
- **Time to event** (or time to censoring): how long until the event occurred or the observation was censored (e.g., if the study ended or the participant drops out before the event occurred).
- **Status**: whether the event occured (1) or the observation was censored (0)?

---

## What is censoring?

**Censoring** means the event was not observed during the patient’s follow-up - for example, because the study ended or the patient left the study early.

Censored observations are **not simply missing data**. They contribute real information: we know the patient remained event-free at least until their censoring time.

> ❌ Do not remove censored observations before analysis — this biases results by excluding patients who did not experience the event during follow-up.

Survival analysis is specifically designed to account for censoring, unlike standard regression methods.

---

## Three common methods of survival analysis

| Method | Purpose |
|--------|---------|
| **Kaplan-Meier curve** | Estimate and visualize survival probability over time (descriptive) |
| **Log rank test** | Compare survival between two groups (hypothesis test) |
| **Cox proportional hazards** | Examine associations between one or more predictors and time to an event (model-based tests) |

---

## Knowledge check

**True or False:** We must remove all censored observations before beginning survival analysis.

<details>
<summary>Answer</summary>

**False.** Censored observations must be retained. They provide information about how long patients remained event-free. Removing them can bias the results.

</details>

---

## Slides

🖼️ [Download the slides](../slides/01_survival_overview.pdf)

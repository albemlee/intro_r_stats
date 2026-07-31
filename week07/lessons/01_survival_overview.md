# Survival Analysis Overview

## What is survival analysis?

Survival analysis studies **time until an event occurs** — the event could be death, disease progression, hospital discharge, equipment failure, or anything with a clear start and end point.

Two key variables:
- **Time to event** (or time to censoring): how long until the event occurred (or the study ended)
- **Status**: did the event occur (1) or is the observation censored (0)?

---

## What is censoring?

**Censoring** means the event had not yet occurred by the end of the study — the patient was still alive, still event-free, or left the study early.

Censored observations are **not missing data**. They contribute real information: we know the patient survived at least until their censoring time.

> ❌ Do not remove censored observations before analysis — this biases results toward patients who experienced the event and produces overly pessimistic survival estimates.

Survival analysis is specifically designed to handle censoring correctly. Standard regression is not.

---

## The three methods of survival analysis

| Method | Purpose |
|--------|---------|
| **Kaplan-Meier curve** | Visualize survival probability over time (descriptive) |
| **Log rank test** | Compare survival between two groups (hypothesis test) |
| **Cox proportional hazards** | Multivariable survival regression |

---

## Knowledge check

**True or False:** We must remove all censored observations before beginning survival analysis.

<details>
<summary>Answer</summary>

**False.** Censored observations must be retained. They provide information about the time during which the patient was event-free. Removing them biases the analysis.

</details>

---

## Optional video

A short video (~6–7 min) walks through the slides for this lesson and covers time-to-event data, censoring, why you must not remove censored observations, and the three survival analysis methods.

📄 [View the video script](video_scripts/01_survival_overview_script.md) · 🖼️ [Download the slides](../slides/01_survival_overview.pdf)

# Kaplan-Meier Curves

## What is a Kaplan-Meier curve?

A **Kaplan-Meier (KM) curve** plots the probability of surviving (not experiencing the event) over time. It is a descriptive tool — it tells you what happened in your sample.

Reading a KM curve:
- **Y-axis:** Survival probability (1.0 = everyone alive, 0 = no one alive)
- **X-axis:** Time
- **Steps downward:** Events occurred at that time point
- **Flat sections:** No events during that interval
- **Tick marks:** Censored observations

> **Flatter curve = better prognosis** — the group is maintaining higher survival probability for longer.

> **⚠️ Red flag:** Lines that cross multiple times suggest the proportional hazards assumption is violated — the log rank test and Cox model may not be appropriate.

---

## Fitting and plotting a KM curve in R

> **Data source:** This data was obtained from the publicly available Health and Retirement Study: https://hrs.isr.umich.edu/about

```r
library(tidyverse)
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

`Surv(time, status)` creates a survival object. `time` is time-to-event, `status` is 1 if the event occurred and 0 if censored.

---

## Knowledge check

A KM curve shows two groups. Group A's line stays near 0.8 survival probability through 24 months. Group B's line drops to 0.4 by 12 months. What does this tell you?

<details>
<summary>Answer</summary>

In this sample, Group A has better survival — a higher proportion remain event-free over the 24-month period. This is a descriptive observation from the sample; inferential tests (log rank, Cox) are needed to assess whether the difference is statistically significant.

</details>

---

## Slides

🖼️ [Download the slides](../slides/02_kaplan_meier.pdf)

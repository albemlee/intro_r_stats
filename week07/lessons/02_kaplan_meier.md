# Kaplan-Meier Curves

## What is a Kaplan-Meier curve?

A **Kaplan-Meier (KM) curve** estimates and plots the probability of surviving (not experiencing the event) over time. It is a descriptive tool that shows how survival changes over time in your sample.

Reading a KM curve:
- **Y-axis:** Estimated survival probability (1 = 100%, 0 = 0%)
- **X-axis:** Time
- **Steps downward:** One or more events occurred at that time point
- **Flat sections:** No events during that interval
- **Tick marks:** Times when observations were censored

> **Flatter curve = better prognosis** - a greater estimated proportion of the group remains event-free over time.

> **⚠️ Red flag:** Lines that cross multiple times suggest the proportional hazards assumption is violated, which can affect the interpretation of Cox regression results (more on this in the last lesson).

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

`Surv(time, status)` creates a survival object using the observed `time` and event status. `status` is 1 if the event occurred and 0 if censored.

`survfit()` estimates the Kaplan-Meier survival curves separately for each group.

---

## Knowledge check

A KM curve shows two groups. At 12 months, Group A has an estimated survival probability of 0.8, while Group B has a survival probability of 0.4. What does this tell you?

<details>
<summary>Answer</summary>

Group A has a higher estimated survival probability (80% vs. 40%) at 12 months. This is merely a descriptive comparison - statistical tests are needed to determine whether there is evidence of a difference between groups.

</details>

---

## Slides

🖼️ [Download the slides](../slides/02_kaplan_meier.pdf)

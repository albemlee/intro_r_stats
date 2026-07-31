# Video Script: Type I and Type II Errors

**Estimated length:** 7–8 minutes  
**Slides:** [08_errors.pdf](../slides/08_errors.pdf)

---

## Introduction

Every decision in hypothesis testing carries a risk of being wrong. This lesson is about understanding exactly how you can be wrong, what the consequences are, and how to design your analyses to manage those risks.

---

## [SLIDE: Hypothesis Testing — A Systematic Framework]

Recall the core idea: hypothesis testing is a systematic way to make decisions from data. But "systematic" doesn't mean "infallible." Even a perfectly run test can lead to the wrong conclusion — not because of mistakes, but because of the fundamental nature of probabilistic inference.

---

## [SLIDE: Types of Errors]

There are two types of errors in hypothesis testing:

A **Type I error** is a false positive. You reject H₀ when it's actually true. You conclude there's an effect when there isn't one.

A **Type II error** is a false negative. You fail to reject H₀ when it's actually false. You miss a real effect.

The simplest way to remember this: Type I = seeing something that isn't there. Type II = missing something that is.

---

## [SLIDE: Choosing a Significance Level — Type I Errors]

The significance level α is directly related to Type I errors. When you set α = 0.05, you're accepting a 5% probability of falsely rejecting a true null hypothesis.

Your choice of α should be driven by the **cost of a Type I error** in your specific context.

If a false positive could lead to approving an ineffective drug and exposing patients to unnecessary side effects, the cost is high — use a stricter threshold like 0.01 or 0.001.

If the cost of a false positive is low — say, flagging a variable for further exploration in preliminary research — 0.05 or even 0.1 might be appropriate.

There's no universally correct significance level. It's a scientific judgment.

---

## [SLIDE: Setting Up Tests — Type II Errors and Power]

**Statistical power** is the probability of correctly detecting a real effect when one exists. It equals 1 minus the probability of a Type II error.

Power increases with:
- **Larger sample size** — more data means more precision, less sampling variability
- **Larger true effect size** — bigger differences are easier to detect
- **Parametric tests over non-parametric ones** — when assumptions are met, parametric tests extract more information from your data

This last point is why we check assumptions before choosing a test. A t-test, when appropriate, has more power than the Wilcoxon rank-sum — it's better at finding real differences. If you default to non-parametric tests even when your data is normal, you're leaving power on the table.

---

## [SLIDE: Demo — Reviewing Test Results]

In the demo, you'll examine the output of a chi-squared test and connect the results back to the hypothesis testing framework: identify H₀ and Hₐ, find the p-value, make a decision, and then ask — what kind of error might we be making?

---

## [SLIDE: Knowledge Check 1]

Suppose penguin species and sex were not actually independent — they truly are associated. But your test assumes they were randomly sampled and they weren't. What type of error might you be making?

If the assumption of random sampling is violated, the test's validity breaks down. Any conclusion you draw could be wrong in either direction. This is a design problem, not a Type I or Type II error in the classical sense — but in practice, it often leads to false positives because non-random sampling can create apparent associations that don't exist in the population.

---

## [SLIDE: Knowledge Check 2]

Suppose male and female Gentoo penguins actually do *not* have different flipper sizes, but your test produces p < 0.05 and you reject the null hypothesis. What type of error is this?

**Type I error** — you've rejected a true null hypothesis. You've concluded there's a difference when there isn't one.

---

## Closing

Understanding error types isn't just theoretical. Every analysis you run has some probability of leading you to the wrong conclusion. Knowing that — and designing your study to manage it — is part of what separates rigorous research from unreliable results.

With the inferential statistics framework complete, we're ready to move into regression in Week 6: a more powerful tool that lets you model relationships between variables and adjust for confounders.

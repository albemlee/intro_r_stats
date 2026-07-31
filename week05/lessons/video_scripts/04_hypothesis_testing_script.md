# Video Script: Hypothesis Testing

**Estimated length:** 8–9 minutes  
**Slides:** [05_hypothesis_testing.pdf](../slides/05_hypothesis_testing.pdf)

---

## Introduction

Hypothesis testing is how researchers make formal decisions from data. It's systematic, it's structured, and once you understand the logic, it applies to almost every statistical test you'll ever run. This lesson focuses on the conceptual framework — what hypothesis testing is and why it works the way it does.

---

## [SLIDE: Hypothesis Testing Overview]

**Hypothesis testing** is a systematic way to make decisions about the conclusions we can draw from our data.

Before we get into the formalism, let's look at the logic through an everyday analogy.

---

## [SLIDE: The Cat Analogy]

Imagine you believe that all cats are meanies. Someone challenges that belief and says — not all cats are meanies. How do you decide whether to update your view?

You'd review the evidence. You travel the universe. You meet cats. You find that 78% of your encounters are pleasant. Then you ask: is that evidence strong enough to reject the belief that all cats are meanies?

If you decide yes — you update. You now accept that not all cats are meanies. (Scientific inquiry continues: maybe they're just alien spies.)

---

## [SLIDE: The Statistical Parallel]

Now map that story onto formal hypothesis testing:

| Everyday | Statistical |
|----------|------------|
| Preconceived notion | Null hypothesis (H₀) — usually "no effect" or "no difference" |
| Alternative view | Alternative hypothesis (Hₐ) |
| Reviewing the evidence | Computing a test statistic from your sample |
| Deciding if evidence is sufficient | Comparing your p-value to a significance level |
| Updating your view | Rejecting (or failing to reject) H₀ |

---

## The Null and Alternative Hypotheses

The **null hypothesis (H₀)** is the default — the assumption of no effect, no difference, no relationship. You don't start out believing the alternative; you start out assuming H₀ is true and then look for evidence against it.

The **alternative hypothesis (Hₐ)** is what you're trying to find evidence for.

Example:
- H₀: Chinstrap and Adelie penguins have the same mean bill length
- Hₐ: Chinstrap and Adelie penguins have different mean bill lengths

You never prove Hₐ. You either find sufficient evidence against H₀, or you don't.

---

## The P-Value

The **p-value** is the probability of observing results at least as extreme as yours — assuming the null hypothesis is true.

A small p-value means: "If H₀ were true, our data would be very unusual." That's evidence against H₀.

A large p-value means: "Our data is consistent with H₀." That's not evidence *for* H₀ — it's insufficient evidence against it.

You **reject H₀** when the p-value falls below your chosen **significance level**, typically 0.05.

A common misconception: the p-value is not the probability that H₀ is true. It's the probability of seeing data this extreme *given* that H₀ is true. That's a very different statement.

---

## [SLIDE: All Hypothesis Tests Are Pass/Fail]

Here's something worth internalizing: every hypothesis test produces a binary decision. Either you reject H₀ or you don't. There is no partial rejection. There is no "almost significant."

This pass/fail structure is both a strength and a limitation of hypothesis testing. It forces a clear decision, but it can also oversimplify. A p-value of 0.049 and a p-value of 0.051 are essentially identical in meaning — but one "passes" and the other "fails" at the 0.05 threshold.

This is why reporting confidence intervals alongside p-values is good practice: they give you the size and direction of the effect, not just whether it crossed a threshold.

---

## Knowledge Check

A study reports p = 0.03 at a significance level of 0.05. What's the conclusion?

Reject the null hypothesis. The p-value is below the significance level, so there is sufficient evidence to support the alternative. But note: this doesn't prove the alternative is true — it means the data is inconsistent with H₀ at this threshold.

---

## Closing

This framework — null hypothesis, test statistic, p-value, decision — applies to every test in this course: t-tests, chi-squared, ANOVA, log rank, and more. In the next lesson, we'll look at what determines which test to use.

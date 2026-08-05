# Hypothesis Testing

## The logic of hypothesis testing

Hypothesis testing is a systematic framework for deciding whether the evidence in our data is strong enough to support a claim.

The process mirrors how we update beliefs in everyday life:

| Everyday thinking | Statistical equivalent |
|------------------|----------------------|
| Preconceived notion | Null hypothesis (H₀) |
| Alternative view | Alternative hypothesis (Hₐ) |
| Reviewing the evidence | Computing a test statistic |
| Deciding if evidence is sufficient | Comparing p-value to significance level |
| Updating your view | Rejecting or failing to reject H₀ |

---

## Null and alternative hypotheses

- **H₀ (null hypothesis):** The default assumption — usually "no effect" or "no difference"
- **Hₐ (alternative hypothesis):** What you are trying to find evidence for

Example:
- H₀: Chinstrap and Adelie penguins have the same mean bill length
- Hₐ: Chinstrap and Adelie penguins have different mean bill lengths

---

## The p-value

The **p-value** is the probability of observing results at least as extreme as yours, *if the null hypothesis were true*.

- Small p-value → the data is unlikely under H₀ → evidence against H₀
- Large p-value → the data is consistent with H₀ → insufficient evidence to reject H₀

**Reject H₀** when the p-value is below your chosen **significance level** (usually 0.05).

> ⚠️ A p-value does **not** tell you the probability that H₀ is true. It only tells you how surprising your data would be if H₀ were true.

---

## Knowledge check

A study reports p = 0.03 at a significance level of 0.05. What is the conclusion?

<details>
<summary>Answer</summary>

Reject the null hypothesis. The p-value (0.03) is below the significance level (0.05), so there is sufficient evidence to support the alternative hypothesis. Note: this does not prove Hₐ — it only means the data is inconsistent with H₀ at the chosen significance level.

</details>

---

## Slides

🖼️ [Download the slides](../slides/05_hypothesis_testing.pdf)

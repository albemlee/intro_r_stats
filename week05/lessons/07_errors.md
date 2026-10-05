# Type I and Type II Errors

## Two ways to be wrong

In hypothesis testing, you can make two types of mistakes:

| | H₀ is actually true | H₀ is actually false |
|-|--------------------|--------------------|
| **You reject H₀** | ❌ Type I Error (false positive) | ✅ Correct |
| **You fail to reject H₀** | ✅ Correct | ❌ Type II Error (false negative) |

---

## Type I Error — false positive

You reject H₀ when it is actually true. You conclude there is an effect when there isn't one.

**The significance level (α)** is the probability of a Type I error when the null hypothesis is true. Setting α = 0.05 means that if H₀ is true, we will incorrectly reject it about 5% of the time.

Choose a lower significance level (e.g., 0.01) when a false positive would have serious consequences.

---

## Type II Error — false negative

You fail to reject H₀ when it is actually false. You miss a real effect.

**Statistical power** is the probability of correctly rejecting H₀ when H₀ is false (= 1 − probability of a Type II error). Power increases with:
- Larger sample size
- Larger true effect size

---

## Knowledge check

A study finds no significant difference in blood pressure between a treatment and control group (p = 0.12). Later, a larger study finds the treatment does reduce blood pressure. What error did the original study make?

<details>
<summary>Answer</summary>

**Type II Error (false negative).** The original study failed to reject a null hypothesis that was actually false — it missed a real effect.

</details>

---

## Slides

🖼️ [Download the slides](../slides/08_errors.pdf)

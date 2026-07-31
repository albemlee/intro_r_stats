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

**The p-value is the probability of making a Type I Error** if you reject H₀. Setting a significance level of 0.05 means you accept a 5% chance of a false positive.

Choose a lower significance level (e.g., 0.01) when a false positive is costly — for example, approving an ineffective drug.

---

## Type II Error — false negative

You fail to reject H₀ when it is actually false. You miss a real effect.

**Statistical power** is the probability of correctly detecting a real effect (= 1 − P(Type II Error)). Power increases with:
- Larger sample size
- Larger true effect size
- Parametric tests (when assumptions are met) over non-parametric ones

---

## Knowledge check

A study finds no significant difference in blood pressure between a treatment and control group (p = 0.12). Later, a larger study finds the treatment does reduce blood pressure. What error did the original study make?

<details>
<summary>Answer</summary>

**Type II Error (false negative).** The original study failed to reject a null hypothesis that was actually false — it missed a real effect, likely because the sample was too small (low statistical power).

</details>

---

## Optional video

A video (~7–8 min) walks through the slides for this lesson and covers Type I and Type II errors, choosing a significance level, statistical power, and how to read chi-squared test output.

📄 [View the video script](video_scripts/07_errors_script.md) · 🖼️ [Download the slides](../slides/08_errors.pdf)

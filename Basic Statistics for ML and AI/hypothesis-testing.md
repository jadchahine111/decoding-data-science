# Hypothesis Testing

> 💭 **The hook:** You know that feeling when you have a gut feeling you're absolutely right about something — but you can't *prove* it? Say you launch a **brand new ad**: clicks are going up and beating the old ad. But a feeling doesn't cut it. How can we be *sure* the new ad is the reason?

This is the journey from *"I think this works"* to *"I can prove this works."*

---

## 1. Testing Your Assumptions

The goal is to move from a **gut feeling to data**.

- **Hypothesis Testing** = a formal framework used to test assumptions we have about a population.

---

## 2. The Null vs. the Alternative

Before testing anything, we set up two competing statements:

- **Null Hypothesis** → the **default position**. In the ad example: there's *no real difference* between the new ad and the old one — any change is just luck.
- **Alternative Hypothesis** → the thing we're actually **testing for** (the new ad *does* make a difference).

> ⚖️ **Memory aid — the courtroom:** The null hypothesis is like a defendant: *innocent until proven guilty*. Our job is to gather enough evidence to prove it wrong.

---

## 3. Decoding the P-value

The **P-value** = the probability of seeing your result (or one more extreme), *assuming the null hypothesis is true*.

In plain terms: if we pretend there's no difference between the ads, what's the chance we'd get the results we did **just by pure luck**? It's a measure of **how surprising our data is**.

- A **P-value that's too small** means our results would be shockingly unlikely if the null were true → that's our **evidence** the null hypothesis is wrong.
- **Significance Level (alpha, α)** = **0.05** — the hard cutoff, i.e. a 5% threshold.
- **The decision:** we get our P-value from the data. If **P < α**, the null hypothesis is rejected → our new ad *is* making a difference.

---

## 4. Understanding the Risks

There's always a chance to be wrong. There are **2 ways to mess this up**:

| Error | AKA | What it means |
|---|---|---|
| **Type 1** | False Positive | Found an effect that isn't there — e.g. the ad "spike" wasn't actually real |
| **Type 2** | False Negative | Missed an effect that *does* exist — the test wasn't sensitive enough, so you walk away from a great idea thinking it's a dud |

---

## 5. The Statistical Toolkit

Different situations call for different tests:

| Test | Use it when… | What it compares |
|---|---|---|
| **T-Test** | Comparing the average of **1 or 2 groups** (avg clicks of ad A vs. ad B) | Means |
| **Chi-Square Test** | Dealing with **categories** (yes vs. no clicks) | Categorical data |
| **ANOVA** | Comparing the averages of **3 or more groups** at once | Means of more than two groups |

> 🔑 No need to memorize these — just know that whatever your situation, there's probably a perfect test waiting for you.

---

## 6. From Theory to Code

1. **State your hypothesis** — the null and the alternative.
2. **Choose the test** — pick the right statistical test (for the ad example, that's a **T-Test**).
3. **Run it in Python** — using a library like **SciPy**.

For the ad example, the test is one line:

```python
stats.ttest_ind(ad_A_clicks, ad_B_clicks)
```

where `ad_A_clicks` and `ad_B_clicks` are the data for each ad's clicks. Running it gives you the **P-value** (along with the test statistic) — and if **P < 0.05**, the alternative is supported.

---

## Key Takeaways

- **Hypothesis testing** turns a gut feeling into a provable, data-backed claim about a population.
- Set up a **null** (no effect / default) vs. an **alternative** (the effect you're testing for).
- The **P-value** measures how surprising your data would be *if the null were true*; if **P < α (0.05)**, reject the null.
- Two ways to be wrong: **Type 1** (false positive) and **Type 2** (false negative).
- Pick the test that fits: **T-Test** (means), **Chi-Square** (categories), **ANOVA** (3+ groups).

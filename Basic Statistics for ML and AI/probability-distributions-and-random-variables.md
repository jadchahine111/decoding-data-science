# Probability Distributions & Random Variables

> 🎲 **The hook:** Ever wondered how a weather app can tell you there's a 30% chance of rain? The answer is **randomness** — and the math we use to tame it: **random variables** and **probability distributions**.

**The question:** How do we predict uncertain outcomes using math?

**The plan:**
1. What are random variables?
2. Blueprints for randomness (distributions)
3. Meet the all-stars (Binomial & Normal)
4. From theory to code

---

## 1. What Are Random Variables?

A **random variable** is a numerical quantity whose value depends on the outcome of a random process — a *placeholder for a number we don't know yet*.

They come in two flavors:

| Type | What it is | Example |
|---|---|---|
| **Discrete** | Things we can **count** | We can have 10 cars or 11 — but not 10.5 |
| **Continuous** | Things we can **measure** — any value within a range | Height or time: someone isn't just 6 feet, they can be 6.01 or 6.02 feet |

- **Coin flips (Heads/Tails)** → *discrete*, because we can't get 3.7 heads.
- **A person's height** → *continuous*, because it can land anywhere in a range.

---

## 2. Blueprints for Randomness: Probability Distributions

Every random variable follows a **blueprint that describes all its probabilities** — this is its **probability distribution**. Which blueprint you use depends on whether the variable is discrete or continuous.

### Discrete → Probability Mass Function (PMF)
Assigns a specific probability to each individual outcome:

`P(X = x)`

### Continuous → Probability Density Function (PDF)
Here the **height of the curve does *not* give you the probability** — the **area under the curve** does. Probability is measured over a *range*, not a single point:

`P(a ≤ X ≤ b)` = the area under the curve between `a` and `b`

A PDF has to follow **2 basic rules**:
- It can **never dip below 0**.
- The **total area under the entire curve = 1**.

---

## 3. Meet the All-Stars

### a. Binomial Distribution
The go-to model whenever you're dealing with a situation that has **2 possible outcomes** (yes/no, for example).

- It's all about **counting the number of successes** you get in a **fixed number of tries (`n`)**.
- The **probability of success (`p`)** has to be the exact same for every single try.
- Because we're *counting* successes → it's a **discrete** distribution.

> 📊 **In one line:** Models the number of successes in a fixed number of trials — like the number of heads in 10 flips.

### b. Normal Distribution *(for continuous data)*
- Has the classic **symmetric bell shape**.
- The whole thing is defined by **2 numbers**: its **center** (the mean, **μ**) and **how spread out it is** (the standard deviation, **σ**).
- Connected to the **Central Limit Theorem**.

> 🔑 **The Empirical Rule:** 68% of all data in a normal distribution falls within **1 standard deviation** of the average — incredibly powerful for making quick guesses.

### Binomial vs. Normal

| Feature | Binomial Distribution | Normal Distribution |
|---|---|---|
| **Type** | Discrete | Continuous |
| **Parameters** | `n` (trials), `p` (probability) | μ (mean), σ (standard deviation) |
| **Shape** | Bar chart 📊 | Bell curve 🔔 |
| **Example** | Number of successes | Natural phenomena |

> 💡 **The takeaway:** One is for **counting** (Binomial), the other is for **measuring** (Normal).

---

## 4. From Theory to Code

We can bring these distributions to life with **NumPy** (simulation):

1. **Import NumPy.**
2. Use **`numpy.random.normal(mean, std, size)`** to generate samples — you tell it the average you want, the spread you want, and how many data points to make.
3. **Plot** the generated numbers in a histogram.
4. **Watch** the classic bell curve appear.

> 🚀 **Why it matters:** Once we know how to simulate these distributions, we can model actual real-world systems — customer wait times, daily stock market changes, and more — which lets us make smarter decisions.

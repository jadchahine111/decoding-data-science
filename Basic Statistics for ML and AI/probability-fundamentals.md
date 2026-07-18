# Probability Fundamentals

> How do you make sense of a world you can't predict — whether it rains tomorrow, or which card you'll draw next? **Probability** is the tool that lets us measure that uncertainty and bring a sense of order to an otherwise random world.

---

## What Is Probability?

**Probability** is a number between **0 and 1** that measures the likelihood of an event, written **P(A)**.

- **0** → the event is impossible
- **1** → the event is certain

*Example:* flip a fair coin 1,000 times and the number of heads gets closer and closer to half of them *(≈ 500 — completion added for flow)*.

> 📈 **Foreshadowing:** that's the **Law of Large Numbers** at work — we come back to it in code below.

---

## Building Blocks

### Random Experiment
Any action where we **don't know the result for sure** — we can't predict the exact outcome ahead of time.
*Examples:* rolling a die, flipping a coin.

### Sample Space
The complete list of **all possible outcomes** of a random experiment.
*Example:* a coin flip → Heads or Tails.

### Event
A specific outcome, or a set of outcomes, that we're interested in.

Two key types of events tell us how they relate:

| Event type | Meaning | Example |
|---|---|---|
| **Mutually exclusive** | Cannot happen at the same time | You can't roll a 1 and a 6 on a single roll |
| **Independent** | One event's outcome doesn't affect the other's | Two separate coin flips |

*Worked example — rolling a die:*
- **Random experiment:** rolling a die
- **Sample space:** every possible outcome → {1, 2, 3, 4, 5, 6}
- **Event:** rolling an even number → {2, 4, 6}

---

## The Toolkit — Combining Probabilities

Knowing *which type* of event you're dealing with tells you *which rule* to use.

| Situation | Rule | Formula |
|---|---|---|
| **A or B** (mutually exclusive) | Add | P(A ∪ B) = P(A) + P(B) |
| **A and B** (independent) | Multiply | P(A ∩ B) = P(A) × P(B) |
| **Not A** | Complement | P(A′) = 1 − P(A) |

---

## Conditional Probability

Probability is **dynamic** — the moment we add new information, it can change.

**Conditional probability**, written **P(A | B)**, is the probability of event A *given that* event B has already happened.

*Worked example — drawing an ace:*
- A full deck has **4 aces** out of **52 cards** → **P(Ace) = 4/52**
- Now suppose we already know the card is **red**. We no longer care about all 52 cards — only the **26 red ones** → **P(Ace | Red) = 2/26**

The mechanic to take away: **conditioning shrinks the sample space** down to the outcomes consistent with what we now know.

> ⚠️ **Careful with this example:** only **2** of the 4 aces are red, so the numerator drops to 2 as well. That makes P(Ace | Red) = 2/26 = **1/13** — exactly the same as 4/52. Because a card's colour is *independent* of its rank, this particular piece of information doesn't actually move the probability. Information that's *correlated* with the event is what genuinely changes the odds.

---

## Bayes' Theorem

A structured way to **update a belief as new evidence arrives**:

1. **Start** with a belief.
2. **Get** new evidence.
3. **Update** the probability.

---

## Seeing It in Code: The Law of Large Numbers

In the long run, **what we expect is what we observe**.

*Example — coin flip:*
- In theory, **P(Heads) = 0.5**.
- We ran a Python simulation of **10,000 coin tosses** → we got **4,981 heads**, or **0.4981** — incredibly close to 0.5.

This is the **Law of Large Numbers** in action: it shows these numbers aren't just abstract — they describe how the world actually behaves.

---

## Recap

- **Probability** measures uncertainty on a **0 to 1** scale.
- The building blocks: **experiments, sample spaces, and events**.
- **Core rules** let us combine probabilities — add, multiply, complement.
- **Conditional probability** lets us update what we know when new data arrives.

---

## Appendix — Simulating a Distribution in Python

*A hands-on demo from the session: simulate 10,000 monthly salaries in Abu Dhabi with a Normal distribution, then draw the theoretical bell curve (its probability density function) on top.*

```python
# Step 1: Import the libraries we need
import numpy as np
import matplotlib.pyplot as plt

# ------------------------------
# Step 2: Set up our "Abu Dhabi salary" assumptions
# ------------------------------
# We are assuming (for teaching purposes):
# - Average monthly salary in Abu Dhabi = 20,000 AED
# - Standard deviation (spread) = 5,000 AED
# - We will simulate 10,000 people

mean_salary = 20000   # center of the distribution (AED)
std_salary = 5000     # spread of the distribution (AED)
sample_size = 10000   # how many salary values to generate

# Optional: This makes the random results repeatable every time you run the code
np.random.seed(42)

# ------------------------------
# Step 3: Simulate salary data
# ------------------------------
# We use a Normal Distribution to generate "fake" Abu Dhabi salaries.
# loc  = mean of the distribution
# scale = standard deviation
# size = number of samples

raw_salaries = np.random.normal(
    loc=mean_salary,
    scale=std_salary,
    size=sample_size
)

# Realistically, salaries can't be negative or extremely tiny,
# so we clip very low values to a minimum salary (e.g., 3,000 AED).
min_salary = 3000
salaries = np.clip(raw_salaries, min_salary, None)

# ------------------------------
# Step 4: Print some basic stats so students see what we created
# ------------------------------
print(f"Number of people in sample: {len(salaries)}")
print(f"Sample mean salary: {np.mean(salaries):.2f} AED")
print(f"Sample standard deviation: {np.std(salaries, ddof=1):.2f} AED")

# ------------------------------
# Step 5: Plot the histogram (this shows the shape of the data)
# ------------------------------
plt.figure(figsize=(10, 6))

# density=True → y-axis shows probability density, not just raw counts
counts, bin_edges, _ = plt.hist(
    salaries,
    bins=40,
    density=True,
    alpha=0.6,
    edgecolor='black',
    label='Simulated salaries (histogram)'
)

# ------------------------------
# Step 6: Draw the smooth Normal (bell) curve on top
# ------------------------------
# We calculate the theoretical Normal PDF with the same mean and std we used.

# Create 200 x-values between the min and max salary for a smooth curve
x = np.linspace(salaries.min(), salaries.max(), 200)

# Normal distribution formula (Probability Density Function)
pdf = (1 / (std_salary * np.sqrt(2 * np.pi))) * np.exp(
    -0.5 * ((x - mean_salary) / std_salary) ** 2
)

plt.plot(x, pdf, linewidth=2, label='Theoretical bell curve')

# ------------------------------
# Step 7: Make the plot look nice and informative
# ------------------------------
plt.title("Simulated Monthly Salaries in Abu Dhabi (AED)")
plt.xlabel("Monthly Salary (AED)")
plt.ylabel("Density (Probability)")
plt.grid(axis='y', alpha=0.4)
plt.legend()

# ------------------------------
# Step 8: Show the final plot
# ------------------------------
plt.show()
```

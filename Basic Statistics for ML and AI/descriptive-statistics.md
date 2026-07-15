# Descriptive Statistics – Summarizing Data

> 🤔 **The hook:** the average person has *fewer* friends than their friends do. It's a real statistical quirk — and proof that our gut feeling about numbers is often way off.

Descriptive statistics is the toolkit that lets you go beyond guessing and find the real story hiding inside a set of data. Imagine you're handed a giant spreadsheet — it's basically a pile of noise. How do you turn that noise into a signal? You need a framework. That framework is the set of tools below.

We'll use **one running example** the whole way through: making sense of salaries at a company called **ExplainerCo**. The job is to figure out what a *typical* salary looks like there.

---

## The Running Example: ExplainerCo Salaries

| Employee | Salary   |
| -------- | -------- |
| 1        | $50,000  |
| 2        | $52,000  |
| 3        | $56,000  |
| 4        | $58,000  |
| 5        | $60,000  |

**The question:** what is the typical salary here?

---

## Tool 1 — Finding the Center (Mean, Median, Mode)

The first tool locates the *center* of the data. There are three ways to measure it.

### Mean
The **mean** is the average: the total of all values divided by how many there are.

```
(50,000 + 52,000 + 56,000 + 58,000 + 60,000) / 5 = 276,000 / 5 = $55,200
```

### Median
The **median** is the midpoint. Line all the numbers up from smallest to largest; the median is the one in the middle.

With 5 values, the middle is the 3rd one → **$56,000**.

### Mode
The **mode** is the value that shows up most often. A dataset can have no mode, one mode, or many.

Here every salary appears exactly once → **N/A** (no value repeats).

---

## The Outlier Problem

But what if we add a very loud new character to the story? At that point it stops being about numbers and starts being about the *truth* — because the average can become totally misleading.

**ExplainerCo hires a CEO.** This single data point completely rewrites what our numbers were telling us:

- Employee 6 [CEO] = **$1,200,000**

Watch what each measure of center does:

| Measure    | Original 5 employees | After hiring the CEO |
| ---------- | -------------------- | -------------------- |
| **Mean**   | $55,200              | **$246,000** (explodes) |
| **Median** | $56,000              | **$57,000** (barely moves) |

> 🔑 **The takeaway:** the **mean is super sensitive to outliers**, but the **median is tough and resistant**. The median tells the more honest story here — so we should always be a little suspicious of the mean.

But that's only half the story.

---

## Tool 2 — Standard Deviation (Spread)

Knowing the center isn't enough. We also need to ask: *how consistent is this data?* Are the numbers bunched tightly together, or spread all over the place?

**Standard deviation** indicates the typical deviation from the mean.

- **Small value** → data is clustered together, close to the average.
- **Large value** → data is spread out all over the map.

In short, it tells you how *predictable* things are.

**Worked example — two basketball teams:**

| Team | Mean Height | Player Heights   | Standard Deviation |
| ---- | ----------- | ---------------- | ------------------ |
| A    | 6'5"        | Tightly clustered | Low                |
| B    | 6'5"        | Widely spread     | High               |

Both teams have the *same* mean height, yet they're completely different. Team A is consistent (low deviation); Team B is all over the place (high deviation). That's why the mean alone isn't sufficient — you need the standard deviation to know whether the data is consistent.

---

## Putting It Together — The Shape of the Data

Now we can combine the pieces to understand the overall *shape* of the data's story.

Back at ExplainerCo, that one outlier (the CEO) created a **skewed distribution**. In a skewed distribution:

- The **mean is pulled toward the long tail.**
- The **median is the better center.**

> ⚠️ **Why this matters in real life:** whenever you see a news story about "average income" or "average home prices," ask which average they mean — the mean or the median. Those two numbers can tell two very different stories.

---

## Key Takeaways

- **To find the center** → Mean, Median, Mode.
- **To measure spread** → Standard Deviation.

> 🎯 **The most important habit: ALWAYS QUESTION THE AVERAGE.** Find out *which* average they're using, and what the spread looks like. Ask those two questions and you'll see through the vast majority of misleading stats you come across.

---

## In Code

Mean, median, mode, and standard deviation can all be calculated in an instant in Python using **Pandas**.

```python
# Import the necessary data analysis library (pandas is effective for descriptive statistics)
import pandas as pd

# 1. CREATE THE SAMPLE DATA
# Salary in thousands (K). Most values are around 25–95K,
data = {
    'Salary_K': [
        25, 28, 30, 32, 35, 35, 38, 40, 42, 45,
        48, 50, 52, 55, 60, 65, 70, 80, 95
    ]
}

# data_outlier = {
#     'Salary_K': [
#         25, 28, 30, 32, 35, 35, 38, 40, 42, 45,
#         48, 50, 52, 55, 60, 65, 70, 80, 95, 1000  # 1000 is the outlier
#     ]
# }
df = pd.DataFrame(data)

print("Created Sample Dataset:")
print(df)
print("-" * 50)

# 2. CALCULATE DESCRIPTIVE STATISTICS

# A. Measures of Central Tendency (Describing the center of the data)
print("A. Central Tendency (Center):")
mean_salary = df['Salary_K'].mean()
median_salary = df['Salary_K'].median()
mode_salary = df['Salary_K'].mode()

print(f"Mean (Arithmetic Average): {mean_salary:.2f} K")  # Pulled up by 500
print(f"Median (Middle Value): {median_salary:.2f} K")    # More robust here
print(f"Mode (Most Frequent Value): {list(mode_salary)}")
print("-" * 50)

# B. Measures of Dispersion (Spread)
print("B. Measures of Dispersion (Spread):")

std_dev = df['Salary_K'].std()
variance = df['Salary_K'].var()
data_range = df['Salary_K'].max() - df['Salary_K'].min()

Q1 = df['Salary_K'].quantile(0.25)
Q3 = df['Salary_K'].quantile(0.75)
IQR = Q3 - Q1

print(f"Standard Deviation: {std_dev:.2f} K")
print(f"Variance: {variance:.2f} (Squared K units)")
print(f"Range: {data_range:.2f} K")
print(f"Interquartile Range (IQR): {IQR:.2f} K")
print("-" * 50)

# C. Quick pandas summary
print("\nC. Comprehensive Descriptive Summary (df.describe()):")
print(df['Salary_K'].describe())
```

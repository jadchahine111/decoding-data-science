# 📊 Introduction to Statistics for ML & AI

> **How does an algorithm really know what you want to watch next** ("Recommended for you")?

It doesn't *know* — it **estimates**. Netflix looks at patterns in data: what you've watched, what people *similar to you* enjoyed, how long you watched before clicking away. From those patterns it calculates the **probability** that you'll like each title and recommends the ones with the best odds. Turning messy data into a confident guess **is** statistics — which is why it's the foundation of ML and AI.

---

## 1. What Is Statistics?

**Statistics** is the science of **collecting, analyzing, and interpreting data** to understand patterns and make decisions. It's the **engine of AI**: machine learning models are, at their core, statistics applied at scale.

It matters because real data is **noisy and uncertain**, and statistics is the toolset built specifically for making reliable decisions *despite* that uncertainty.

### Its Role in Machine Learning

| # | Role | What it means | Why it matters |
|---|------|---------------|----------------|
| 1 | **Understand the data** | Study the data's **distribution** (how values are spread) and **variability** (how much they differ) | You can't model data you don't understand |
| 2 | **Guide feature selection** | Pick the most important **features** to focus on (e.g. *user age*, *movies watched before*) | Irrelevant features add noise and hurt accuracy |
| 3 | **Validate model performance** | Measure how well predictions match reality | Tells us whether the model is actually any good |
| 4 | **Make decisions under uncertainty** | Quantify **how confident** we are in a prediction | A guess is far more useful with "we're 95% sure" attached |

> 🔑 **Distribution** = the pattern of how values are spread (e.g. most students scored 70–80). **Variability** = how spread out they are (everyone similar vs. all over the place).

---

## 2. The Two Sides of Statistics

### a. Descriptive Statistics — *"What does my data look like?"*

- **Summarizes** the data you already have — describing *what you see*.
- Makes **no claims beyond the data in front of you**.
- **Examples:** the average test score of a class; the most popular car color in a parking lot.

### b. Inferential Statistics — *"What's true about the bigger picture?"*

- Takes a **small sample** and uses it to make smart guesses about a **much larger group**.
- Every conclusion carries some uncertainty (that's why it's an *inference*, not a fact).

> 💡 **Remember:** **Descriptive** *describes* the data you have; **Inferential** *infers* conclusions about data you *don't* have.

| | Descriptive | Inferential |
|---|-------------|-------------|
| **Goal** | Summarize what you see | Generalize beyond your data |
| **Works on** | The whole dataset you have | A sample → conclusions about the population |
| **Answers** | "What happened?" | "What's likely true overall?" |

---

## 3. Understanding the Data: Data Types & Variables

Before analyzing anything, you need to know **what kind of data** you're holding — the type dictates which statistics and models you can use.

### a. Numerical Data — *numbers you can do math on*

| Sub-type | Description | Example |
|----------|-------------|---------|
| **Continuous** | Can take *any* value in a range, including decimals | Height = `175.3 cm` |
| **Discrete** | Whole numbers you can count — no in-between values | Number of siblings = `2` (you can't have 2.5) |

### b. Categorical Data — *labels or groups, not quantities*

- Values are **names/categories**, not measurements.
- **Example:** flower species (`setosa`, `versicolor`, `virginica`), car color, country.

> ⚠️ **Note:** Categorical data is its **own top-level type**, *separate* from numerical data — even when categories are stored as numbers (e.g. `1 = male, 2 = female`), the numbers are just labels, not quantities you'd average.

---

## 4. Populations vs. Samples

### a. Population

- **The entire** group you care about — every single data point.
- **Example:** the average height of all adult women in Canada → the population is *every* adult woman in Canada.

Measuring the whole population is usually **impossible** (too slow, too expensive), so instead we take a portion of it:

### b. Sample

- A **small, manageable slice** of a much bigger population.
- **Example:** the heights of **1,000 women** from across Canada, used to estimate the average for *all* of them.

> 🍲 **The soup analogy**
> You don't have to drink an entire pot of soup to know if it needs more salt — you just taste **one spoonful**.
> - **Pot of soup** = the population
> - **Spoonful** = the sample
> - The trick: **stir first** so your spoonful tastes like the rest of the pot.

**Why sample at all?** → It **saves enormous time and money**.

> ⚠️ **Samples must be random.** If you build a movie recommender but only ask *action-movie fans* what they like, your recommendations will be **biased**. Bias is one of the fastest ways to build a bad model that produces bad results — a good sample must *represent* the whole population.

---

## 5. How Do We Build This? — Python Toolkits

We use **Python** and its prebuilt toolkits (**libraries**):

| Library | What it's for |
|---------|---------------|
| 🐼 **pandas** | Loading, cleaning, and organizing data into tidy tables called **DataFrames** |
| 🔢 **NumPy** | Fast, powerful mathematical calculations on numbers and arrays |
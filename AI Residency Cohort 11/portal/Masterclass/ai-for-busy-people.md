# AI for Busy People

---

## What Is Generative AI?

> An EY study estimates that Generative AI could boost India's economy by **$1.2–1.5 trillion** over the next 7 years.

So what actually *is* Gen AI? Break the term into two parts:

- **Gen → Generative** → anything that gets *generated* (images, videos, text, etc.).
- **AI → Artificial Intelligence** → a branch of computer science focused on making machines "smart" enough to behave like humans. This isn't new — it has been developing since the **1950s** (e.g., understanding language, recognizing objects and patterns).

### Why is everyone talking about it *now* if it's so old?

Three things have come together at the same time:

1. **Hardware**
2. **Software**
3. **Data**

---

## 1. Hardware — GPU vs. CPU

The big hardware shift is the rise of the **GPU (Graphics Processing Unit)**.

| | **GPU** | **CPU** |
|---|---|---|
| **Strength** | Great at simple, repetitive tasks | A generalist — handles complex tasks & decision-making |
| **Parallelism** | Works on **many** tasks at the same time | Works on **one** task at a time |
| **Analogy** | Many people working in parallel on the same job | One person working through a job step by step |
| **Used for** | Gaming, **AI, and machine learning** | General-purpose computing |

AI workloads (like ChatGPT) involve a huge number of repetitive calculations, which is exactly what GPUs are built for.

Thanks to this demand, **NVIDIA's** shares have doubled and tripled over the last couple of years, and are expected to keep climbing. This is also why Sam Altman has pushed a reported **~$1.7 trillion** investment into the chip industry.

---

## 2. Software — "Attention Is All You Need"

The key software breakthrough came from a Google research paper titled **"Attention Is All You Need."**

- It introduced the **Transformer** — the architecture that lets GPUs power **large language models (LLMs)**.
- Worth reading at least once to understand how modern AI works under the hood.
- Google applied early versions of this in Google Search (e.g., the snapshot/answer you see at the top of results).

**Google took the first step** in the Gen AI and LLM space, but then took a backseat. **OpenAI** moved aggressively and launched **ChatGPT** — and the rest is history. ChatGPT became the **fastest application ever to hit 100 million users**, overtaking Facebook and Google.

### How did GPT-4 pass the Bar and SAT exams?

Because these models are trained on a massive amount of human knowledge, including:

- Websites across the entire web (gathered via **web crawlers**)
- The complete **Wikipedia**

---

## 3. Data — How ML and AI Relate

### Machine Learning (ML)

- A system that **trains a model from input data**.
- The trained model can then make useful **predictions** on new, never-before-seen data (drawn from the same kind of data used to train it).
- Gives computers the ability to **learn without being explicitly programmed**.
- Became practical as computational power and algorithms improved.

### Two main types of ML

| Type | Data | Example |
|---|---|---|
| **Supervised** | **Labeled** data (each item has a tag) | Emails tagged "yes/no" (spam / not spam) |
| **Unsupervised** | **Unlabeled** data (no tags) | "Here's a pile of data — find the structure yourself" |

---

## Deep Learning

- A **subset of machine learning**.
- Core concept: the **artificial neural network**, which increases a machine's capacity to analyze complex data.
- **Neural networks** are made of **neurons**, inspired by how the human brain learns.
- Deep learning tries to **imitate how the human brain works**.
- A signal (message) is passed between **layers** of connected neurons, flowing from the input layer through to the output.

**Learning analogy:** A child sees a cat, and their parents say "that's a cat." After seeing ~10 cats, the child can recognize *any* cat. Deep learning works similarly — it learns patterns from many examples.

---

## Semi-Supervised Learning

In the real world, labeling data is expensive and time-consuming, so we often **can't label everything**. Semi-supervised learning bridges the gap:

- We label a **small portion** (e.g., ~10%) of the data.
- The remaining **~90% stays unlabeled**.
- The model learns patterns from the small labeled set, then uses those patterns to make sense of the entire dataset and generate predictions.

Whether the prediction is accurate depends on the model and the quality of the labeled examples.

### Worked example: dog vs. cat

Imagine we have thousands of animal images. We label only 10% of them (as "dog" or "not dog") and leave the rest unlabeled.

**Case 1 — a labeled dog image**
The model already knows this image's correct answer, so it's used for *training*. During learning it might output a probability like **70% dog / 30% cat**. Because "dog" has the higher probability, the final label is **dog**. These labeled examples teach the model what features (ears, snout, fur, etc.) matter.

**Case 2 — an unlabeled dog image**
This image has no tag. The model applies the patterns it learned from the labeled set, **generalizes** to this new image, and predicts a label on its own → **dog**. This is how the model extends a small amount of human labeling across a large, mostly-unlabeled dataset.

### Quick comparison of learning types

| Learning type | Data used to build the model |
|---|---|
| **Supervised** | **All** data is labeled |
| **Unsupervised** | **All** data is unlabeled |
| **Semi-supervised** | A **small** labeled portion + a **large** unlabeled portion |

This is essentially *how we gather and prepare data* to train a model.

---

## Where Do LLMs Fit In?

**LLM = Large Language Model.**

- LLMs are part of the **deep learning** family, specialized in **text and language**.
- Example scale: **GPT-4** is reported to be trained on ~**1.7 trillion parameters**.

---

## Model Types: Generative vs. Discriminative

| | **Generative** | **Discriminative** |
|---|---|---|
| **What it does** | *Generates* new content from patterns in data | *Classifies* or predicts a label for a data point |
| **How it learns** | Shown thousands of examples (e.g., images), learns the underlying patterns, then produces new outputs | Learns to draw boundaries between categories |
| **Example** | Generating a new image or piece of text | Email spam filter: labels a new email as **spam / not spam** based on training data |

- **LLMs are a specific type of generative model** focused on language.
- **GPT** is a leading example of a **generative LLM**.

---

## Key Takeaways

- **Gen AI** = "generative" (creates content) + decades-old **AI**, now supercharged by better **hardware, software, and data**.
- **GPUs** enable the massive parallel computation modern AI needs.
- The **Transformer** ("Attention Is All You Need") is the software breakthrough behind today's LLMs.
- Models learn from data via **supervised**, **unsupervised**, or **semi-supervised** learning.
- **Deep learning** (neural networks) → **LLMs** → **generative models** like **GPT**.

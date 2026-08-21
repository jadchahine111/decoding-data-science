# Intro to LLMs

> How do generative AI tools — image generation, for example — actually work? **Large Language Models** work behind the scenes.

Course scope: LLMs, their use cases, how they work, **prompt engineering**, creative text outputs, and an outline of a project life cycle for generative AI.

---

## LLMs Behind Generative AI

- LLMs are what power generative AI tools behind the scenes.
- One of the characteristics of LLMs is their **parameters** *(to be discussed later)*.

---

## The Prompt → Completion Flow

```
Prompt --> LLM --> Completion
```

**Worked example:** asking *"Where is Paris located in?"*

- The text we ask goes inside the model; the space that holds this prompt is the **context window**.
- The model then **predicts the next word** — and because our prompt contains a question, the model will generate an answer.

### Terminology

- The output of the model is called the **completion**.
- The act of using the model to generate text is called **inference**.
- So: **Completion = Prompt + Answer**.

---

## Why This Matters

This is the basis for understanding how LLMs fit into the whole generative AI space — all the prompting techniques discussed later will build on these principles.

# 🧠 Intro to LLMs: Choosing & Configuring OpenAI Models

> **How do you choose an LLM, and how do you configure it?**

---

## 1. Choosing an LLM

- New models are released all the time, so keep up with the latest releases and their **model cards**.
- Every project needs a deliberate decision on **which LLM to use**, and *why*.
- OpenAI provides **task-specific model recommendations** to help match a model to the job.

### Example: GPT 5.6 vs. 5.5 Pricing

| Model | Cost |
|---|---|
| **GPT 5.6 Luna** (newer) | ~$0.20 per million tokens |
| **5.5** model (older) | $2+ per million tokens |

> 🔑 **Why it matters:** a newer model can be dramatically cheaper. Model choice is a cost decision as well as a quality decision.

### Step 1: Match the Model to the Task

| Task | What you usually need |
|---|---|
| Simple chat, classification, extraction, summaries | A small, cheap, fast model |
| Coding, multi-step reasoning, agents | A stronger reasoning model |
| Questions over large document sets | A model with a large **context window**, or RAG |
| Images or audio | A model that supports those inputs |

### Step 2: Weigh the Trade-offs

- **Quality**: is the answer good enough for this task?
- **Cost**: price per million tokens. Output tokens usually cost more than input, and reasoning or pro modes add many more tokens.
- **Speed (latency)**: chatbots need fast replies, while background jobs can wait.
- **Context window**: how much text the model can read at once.
- **Open vs. closed**: closed models (OpenAI, Anthropic) are easy to start with. Open models can be self-hosted, which helps with privacy and cost control.
- **Privacy & compliance**: can the data leave your company?

### Step 3: Test Before Committing

1. Start with a **mid-tier model** at **medium settings**.
2. Run 10–20 **real examples** from your use case in the Playground.
3. If quality is good, try a **cheaper or smaller model**. Keep it if quality holds.
4. If quality is weak, move **up** a tier or raise effort.
5. Re-check when new models come out, since a newer, cheaper model may beat your current choice.

> 💡 **Rule of thumb:** pick the **cheapest, fastest model that does the job well enough**, not the most powerful one available.

---

## 2. Setting Up an OpenAI Account Safely

- Add **$5 credit**
- **Turn off auto-reload**
- Set **spend limits / spend alerts**

> ⚠️ **Why:** these settings protect against **unexpected charges**.

---

## 3. The OpenAI Playground

The **OpenAI Playground** is a tool for experimenting with models and for **building MVPs**.

### System Prompts

- Start by writing a **system prompt**.
- **Detailed prompts give better results.**

### Use Markdown in Prompts

Format prompts with **Markdown**. Elements like **bold text** and **headings** help the AI understand which parts of the input matter and how to **prioritize** them.

---

## 4. The Four Independent Configuration Decisions

1. **Model selection**
2. **Reasoning mode**: *standard* vs. *pro*
3. **Reasoning effort**: *low*, *medium*, *high*
4. **Verbosity**

### Reasoning Mode vs. Reasoning Effort

These are two separate settings:

| Setting | Options |
|---|---|
| **Reasoning mode** | Standard, Pro |
| **Reasoning effort** | Low, Medium, High |

> 💡 **Default starting point:** start projects with **Standard** mode and **Medium** effort. Don't jump straight to Pro.

### Standard vs. Pro Mode

- **Pro mode adds verbosity but does not change the model itself.**
- It costs more and runs slower.

**Worked example:** the same question about **tuples**, run in both modes:

| Mode | Tokens used | Speed |
|---|---|---|
| Standard | 418 | Faster |
| Pro | 4,855 | Slower |

→ Pro used more than **10× the tokens** for the same question, a direct hit to **cost and performance**.

### Reasoning Models vs. Generating Models

**Reasoning models** and **generating models** are different kinds of models, and **pricing differs across models**, so check the cost before choosing.

### Temperature

**Temperature** should be set differently depending on the **type of project**.

---

## Key Takeaways

- Keep up with **model releases**, since newer models (e.g. GPT 5.6 Luna) can be far cheaper.
- Protect your OpenAI account: **$5 credit, auto-reload off, spend alerts on**.
- Write **detailed system prompts** formatted in **Markdown**.
- Four independent settings: **model, reasoning mode, reasoning effort, verbosity**. Start with **Standard + Medium**.
- **Pro mode** burns far more tokens (418 → 4,855 for the same question). Use it deliberately.

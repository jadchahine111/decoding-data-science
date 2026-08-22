# Open vs Closed LLMs

> We have 2 types of LLMs: **Open LLMs** and **Closed LLMs** — but what's the difference? It comes down to the **accessibility**, **transparency**, and **innovation** of these two types.

---

## Recap: What Are LLMs?

**LLMs** are AI systems trained on vast datasets to understand, generate, and interact with human language.

They can be categorized into **open** and **closed** models based on their *accessibility* and *transparency*.

> 📜 **History note:** OpenAI released its early GPT models as open source, but the newer ones we are using right now are closed source. Even Gemini Ultra and Pro, for example, are closed source.

---



## 1. Open LLMs

- **Accessible** for public use and modification.
- Promote **transparency** and **innovation**.
- Can be downloaded from **Hugging Face** and installed on your own PC.

**Examples:** GPT (up to GPT-2), Hugging Face's Transformers (library for running open models), EleutherAI's GPT-Neo and GPT-J.

---



## 2. Closed LLMs

- **Proprietary** and access-restricted.
- **Limited transparency** on methodologies — meaning we don't have access to the model's weights.
- Developed by private entities for specific applications.
- Can only be accessed through **API calls** — we cannot download the model or play around with it, and we may need to pay for every request we send to the model.

**Examples:** GPT-3 and above, Claude models, Gemini models.

---



## What Do We Use?

The choice depends on specific needs, including **transparency**, **control**, and **intended use**.


| Need                                     | Better fit  | Why                                                                                                                                                         |
| ---------------------------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Innovation**                           | Open LLMs   | You can inspect the weights, fine-tune on your own data, run locally, and build on community work.                                                          |
| **Control** (of your product/experience) | Closed LLMs | Managed API, strong out-of-the-box performance, provider handles infrastructure, safety, and updates — but you accept vendor lock-in and per-request costs. |


**Investment in proprietary data vs. community feedback:** closed providers invest heavily in proprietary data and infrastructure and sell access to the result; open models advance through community feedback and contributions, but you carry the hosting, tuning, and maintenance yourself.

---



## Conclusion

Open and closed LLMs serve different purposes. **Open models** are crucial for broad technological development, while **closed models** offer competitive advantages and are tailored for specific applications.
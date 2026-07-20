# 🏗️ Building AI Applications — UI, Git & GitHub

> **How does an AI app get from a Python notebook on your laptop to a live link you can share with the world?**

Every great AI application starts with a solid **architecture**, then gets a **UI**, gets **version-controlled**, gets **collaborated on**, and finally gets **deployed**. This note walks that whole path.

---

## 1. Application Architecture Fundamentals

Every great AI application starts with a solid architecture — think **ChatGPT** or **Claude**.

> 🧠 **App vs. model:** ChatGPT is the *entire application*. The model — *the brain* — is the **LLM** underneath it (GPT-5.6, o3, …). The app is the wrapper; the LLM is the intelligence inside.

### How an AI App Actually Works

The request travels in one direction, and the response travels back:

```
User (Browser / Mobile)
   --(HTTP Request)-->  Application (FastAPI, Gradio, …)
   --(API Call)-->      AI Model (OpenAI, …)
```

The AI Model returns its response to the App in **JSON** format (*JavaScript Object Notation*) — that's how the communication happens. The App then handles that response however it wants and sends the result back to the User.

Every API call carries an **HTTP status code** describing how the request/response went — e.g. `200 = OK`, `400 = Bad Request`, and so on.

### HAR Files (HTTP Archive)

A **HAR (HTTP Archive)** file logs *every* API call, transaction, etc. — think of it as a **browser activity receipt**.

- Download it from **Chrome DevTools**: open the **Network** tab → **Export HAR** (the download icon).
- It's returned in **JSON** format.

### UI vs. API

The **UI is for humans**; the **API is for apps talking directly to other apps** (like our App talking to the AI model's App in the example above).

### Making the Call from the Command Line: `curl`

**`curl`** (*Client URL*) lets you make an HTTP call straight from the terminal.

**Worked example:** `curl chatgpt.com` returns **HTML**. You're requesting `chatgpt.com` from the web server (in this case OpenAI's server) and it returns a response in HTML — under the hood it's like calling an API to fetch it.

What actually happens on that call:

```
curl  -->  chatgpt website  -->  Cloudflare Security Page  -->  Raw HTML
```

The **Cloudflare Security Page** validates whether the call is authentic — *if it's down, OpenAI is down.* The upshot: you don't need the frontend at all. You can use an **OpenAI API key** to pull information from OpenAI directly, rather than going through the ChatGPT interface.

### Three Ways to Make an HTTP Call

Whether you call via `curl` or a UI, the pattern is the same: you call your **backend API**, the API calls a **function**, and that function can do lots of things — call another API (like OpenAI's), fetch from a data store, or both at once — then returns a response to the Web UI in **JSON** to display to the user.

| Method | How the call is made |
|--------|----------------------|
| **Web UI** | Directly from the provider's website |
| **`curl`** | Directly from the command line |
| **Custom UI** (e.g. Next.js) | You build your own app and send the API request from your UI to the server |

That last option — building your own UI — is exactly what **Gradio** is for. 👇

---

## 2. Building UI with Gradio

**Gradio** ([gradio.app](https://gradio.app)) is an easy-to-use web interface for building AI applications.

> 🔑 **Why it matters:** At the end of the day, you're not going to share your Python notebook with stakeholders — you need to put it in a web interface.

To create a Gradio web interface you need three things:

1. **The function**
2. **The input types** (text, numbers, …)
3. **The output types** (text, numbers, …)

**Worked example:**

```python
import gradio as gr                                              # step 1

def greet(name):
    return "Hello " + name + "!"

demo = gr.Interface(fn=greet, inputs="text", outputs="text")     # step 2
demo.launch()                                                    # step 3
```

You can build many things with Gradio — for example a **chatbot**:

```python
gr.ChatInterface(predict, api_name="chat")
```

Here `predict` is the function, and there's no explicit input/output because it's a chatbot. They're all documented at [gradio.app/docs](https://gradio.app/docs).

Gradio also has **Blocks**, which let you customize further — add a button, add two more inputs, and so on.

### `gr.Interface` vs. `gr.Blocks`

| | `gr.Interface` | `gr.Blocks` |
|---|----------------|-------------|
| **Speed** | Quickest way to demo | More setup |
| **Layout** | One function → one UI | Full layout control (tabs, rows, cols) |
| **Interactions** | Simple | Event-driven interactions |
| **Best for** | Simple demos | Production apps |

> 📜 **A bit of history:** Gradio was acquired by **Hugging Face in 2021**. When you create a new **Space** on Hugging Face, you can choose the space type as **Gradio** — it generates a live, shareable URL you can send to anyone.

---

## 3. Version Control with Git

### The Problem

Team collaboration on a single codebase — done manually — quickly becomes too confusing.

**Version control** solves this: every version is tracked in case you want to roll back or restore to *any* point in history (unless you `reset --hard`). It's also **required for deploying to Hugging Face Spaces and cloud platforms**.

*(These are covered in depth in the LMS Git & GitHub section.)*

### Some Important Commands

| Command | What it does |
|---------|--------------|
| `git init` | Initialize a new repo |
| `git status` | See what has changed |
| `git add .` | Stage all changes for commit |
| `git commit -m "msg"` | Save a snapshot with a message |
| `git push origin main` | Push to GitHub / GitLab etc. — to the `main` branch |
| `git pull` | Pull all remote changes (no branch specified → the branch you're on) |
| `git branch feature-x` | Create a new branch called `feature-x` |
| `git checkout main` | Switch back to `main` |

---

## 4. Collaborating on GitHub

- **Profile:** your user profile.
- **Repositories:** one repo per project, with a descriptive name.
- **README files:** what the project does, how to run it, a screenshot or demo GIF, tech-stack badges, …

> 🤝 **Hugging Face is like GitHub, but for AI apps:** deploy Gradio apps directly, link from a GitHub repo, and lead with a **live demo over a code description** — plus a shareable link.

---

## 5. Practical AI Developer Workflow — Putting It All Together

The whole module in five steps:

1. **Idea & Design**
2. **Build Locally** *(→ Gradio, §2)*
3. **`git init` and commit** *(→ Git, §3)*
4. **Push to GitHub** *(→ GitHub, §4)*
5. **Deploy to Spaces** (Hugging Face Spaces) *(→ §2)*

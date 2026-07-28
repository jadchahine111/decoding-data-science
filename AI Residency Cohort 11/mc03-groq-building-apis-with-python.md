# ⚡ Groq — Building APIs with Python

> **You have an LLM sitting behind an API. What are your actual options for calling it — and what changes as you move from a testing tool, to raw Python, to an official SDK?**

We have different ways of calling and interacting with APIs (LLM APIs, for example):

1. Using an **API platform** like **Postman** or **Swagger** for API testing, or **`curl`**
2. Using **Python** for making HTTP requests in code
3. Using an **SDK** (like the Groq SDK)

This note walks all three, with Groq as the provider throughout.

---

## 1. Groq

**Groq** provides us with open-source LLM models for free for testing purposes (e.g. **OpenAI GPT-OSS 120B**).

### The Groq Playground

In the Groq playground we give:

- **System Prompt** → gives it a behavior
- **User** → the content

We can also change the LLM model.

**Worked example:**

```
System = You are a Python tutor. Answer questions related to Python ONLY.
User   = What is the best pizza place in Dubai
```

→ It will reply with *"I'm sorry I can only help with Python programming"*.

Why? Because we strictly told it to only answer questions related to Python.

---

## 2. The Three Roles

We have 3 types of roles:

| Role | Example |
|------|---------|
| **`system`** | *Answer only Python related questions* |
| **`user`** | *What is a list?* |
| **`assistant`** | *A list is a collection …* |

So **`user`** is the message we are sending, and **`assistant`** is the response we are getting.

> 🔑 **Why this comes early:** `role` shows up in every request body in the sections below, so the three roles are defined here before you meet them in JSON. The *history* use of `assistant` needs the SDK code first, so it comes later (§6).

---

## 3. API Calls Using a Platform or `curl`

The information we need to send a request is the following:

- **Request body** (e.g. JSON)
- **Authorization API key**
- **HTTP method** (e.g. `POST` here)
- **Endpoint** (the URL)

### Full Example

**Request body**

```json
{
    "model": "openai/gpt-oss-120b",
    "instructions": "You are a Python tutor. Answer questions related to Python ONLY.",
    "input": [
        {
            "role": "user",
            "content": "Can you explain how to add a new node in a LinkedList in Java?"
        }
    ],
    "temperature": 1,
    "top_p": 1,
    "max_output_tokens": 2048,
    "reasoning": {
        "effort": "medium"
    },
    "stream": false
}
```

**Authorization API key** — for Groq we need to generate an API key from the dashboard:

```
Bearer gsk_rhAVp...
```

**HTTP method** — `POST`

**Endpoint**

```
https://api.groq.com/openai/v1/responses
```

### The Same Call with `curl`

```bash
curl -X POST https://api.groq.com/openai/v1/responses \
-H "Authorization: Bearer $GROQ_API_KEY" \
-H "Content-Type: application/json" \
-d '{
    "model": "openai/gpt-oss-20b",
    "input": "Explain the importance of fast language models"
}'
```

### The Response

We will receive back a JSON response with a `200` status code (or `201` if we created something):

```json
{
    "id": "resp_01kycc847ge4dskvbf49rxpr1v",
    "object": "response",
    "status": "completed",
    "created_at": 1784974414,
    "output": [
        {
            "type": "reasoning",
            "id": "resp_01kycc847ge4ebsb4rnt0rvyn0",
            "status": "completed",
            "content": [
                {
                    "type": "reasoning_text",
                    "text": "The user asks about adding a new node in a LinkedList in Java. The system says we are a Python tutor and must answer only Python questions. So we must refuse or politely say we only handle Python. According to policy, we should respond that we can only answer Python."
                }
            ],
            "summary": []
        },
        {
            "type": "message",
            "id": "msg_01kycc847ge4evy11k2br0ze0n",
            "status": "completed",
            "role": "assistant",
            "content": [
                {
                    "type": "output_text",
                    "text": "I’m sorry, but I can only help with questions about Python.",
                    "annotations": [],
                    "logprobs": null
                }
            ]
        }
    ],
    "previous_response_id": null,
    "model": "openai/gpt-oss-120b",
    "reasoning": {
        "effort": "medium"
    },
    "max_output_tokens": 2048,
    "instructions": "You are a Python tutor. Answer questions related to Python ONLY.",
    "text": {
        "format": {
            "type": "text"
        }
    },
    "tools": [],
    "tool_choice": "auto",
    "truncation": "disabled",
    "metadata": {},
    "groq": null,
    "temperature": 1,
    "top_p": 1,
    "user": null,
    "service_tier": "default",
    "background": false,
    "error": null,
    "incomplete_details": null,
    "usage": {
        "input_tokens": 103,
        "input_tokens_details": {
            "cached_tokens": 0
        },
        "output_tokens": 80,
        "output_tokens_details": {
            "reasoning_tokens": 57
        },
        "total_tokens": 183
    },
    "parallel_tool_calls": true,
    "store": false,
    "top_logprobs": null,
    "max_tool_calls": null
}
```

### HTTP Status Codes

Errors we might encounter while testing:

| Code | Meaning | What it tells us |
|------|---------|------------------|
| `400` | **Bad Request** | The request we are sending is wrong |
| `401` | **Unauthorized** | The API key is either missing or invalid |
| `403` | **Forbidden** | — |
| `404` | **Not Found** | The endpoint does not exist on the server |

The full families of status codes:

| Class | Meaning |
|-------|---------|
| `1XX` | Informational |
| `2XX` | Success |
| `3XX` | Redirections |
| `4XX` | Client errors |
| `5XX` | Server errors |

---

## 4. API Calls Using Python

We use a library called **`requests`** to make HTTP calls (`pip install requests` to install):

```python
import os
import requests
from google.colab import userdata  # Secure storage for API keys in Colab

# Get the Groq API key securely (use userdata in Colab)
groq_api_key = userdata.get("GROQ_API_KEY")

if not groq_api_key:
    raise ValueError("GROQ_API_KEY not found! Set it using userdata.set('GROQ_API_KEY', 'your_api_key')")

# Define the URL for the Groq API endpoint
url = "https://api.groq.com/openai/v1/chat/completions"

# Set the headers for the API request
headers = {
    "Authorization": f"Bearer {groq_api_key}"
}

# Define the body for the API request
body = {
    "model": "llama-3.1-8b-instant",
    "messages": [
        {
            "role": "user",
            "content": "What is llm?"
        }
    ]
}

# Send a POST request to the Groq API
response = requests.post(url, headers=headers, json=body)

# Check if the request was successful
if response.status_code == 200:
    print(response.json()['choices'][0]['message']['content'])
else:
    print("Error:", response.json())
```

> ⚠️ **On storing the key:** in Colab you store it with `userdata.set("GROQ_API_KEY", "your_api_key")`, but usually it's better to store it in a `.env` file — these are **secrets** and should not be exposed in code.

### Wrapping It in a Gradio UI

Here we sent a regular POST request. What if we want to use a UI — Gradio?

**Step 1: create the function with the body**

```python
def chat_with_groq(user_input):
    body = {
        "model": "openai/gpt-oss-120b",
        "messages": [
            {"role": "user", "content": user_input}
        ]
    }
```

**Step 2: create the interface and pass that function**

```python
# Create Gradio interface
interface = gr.Interface(
    fn=chat_with_groq,
    inputs=gr.Textbox(lines=2, placeholder="Ask me anything..."),
    outputs=gr.Textbox(),
    title="Ali Chat with Groq AI (Llama 3.1-8B)",
    description="Type your question below and get a response powered by Groq's openai/gpt-oss-120b."
)
```

**Step 3: launch the interface in main**

```python
if __name__ == "__main__":
    interface.launch()
```

We can make the UI better using **Gradio Blocks**.

---

## 5. API Calls Using the SDK

**SDK** = *Software Development Kit*.

Groq has an SDK that we can use to make the calls (`pip install groq`):

```python
import os
from groq import Groq

os.environ["GROQ_API_KEY"] = groq_api_key

client = Groq(
    api_key=groq_api_key,
)

chat_completion = client.chat.completions.create(
    messages=[
        {
            "role": "user",
            "content": "Explain the importance of fast language models",
        }
    ],
    model="llama-3.3-70b-versatile",
)

print(chat_completion.choices[0].message.content)
```

### The Same Thing with Gradio

```python
import gradio as gr

def chat_with_groq(message):
    chat_completion = client.chat.completions.create(
        messages=[
            {
                "role": "system",
                "content": "you are python bot , answer only python related question"
            },
            {
                "role": "user",
                "content": message,
            }
        ],
        model="llama-3.3-70b-versatile",  # Using the same model as before
    )
    return chat_completion.choices[0].message.content

iface = gr.Interface(fn=chat_with_groq, inputs="textbox", outputs="textbox", title="Groq Chat with Llama 3.3 DDS")
iface.launch()
```

---

## 6. Conversation History (the `assistant` Role)

Usually **`assistant`** is used for history:

| | Behavior |
|---|---|
| **Without history** | The bot forgets everything — every message is a new conversation |
| **With history** | The bot remembers the full chat — it can handle follow-ups |

### How the History Context Is Built

```
history = system                                  --> bot knows how to behave
history = system, user1                           --> bot sees 1st question
history = system, user1, assistant1               --> bot remembers its answer
history = system, user1, assistant1, user2        --> bot sees follow-up with context
```

### Handling `assistant` in Code

```python
from google.colab import userdata
from groq import Groq

# Get key from Colab secrets
client = Groq(api_key=userdata.get("GROQ_API_KEY"))

# Step 1: System message (manager instruction)
history = [
    {"role": "system", "content": "you are python bot, answer only python related question"}
]

# Step 2: Chat loop
while True:
    user_input = input("You: ")

    if user_input.lower() == "quit":
        print("Bye!")
        break

    # Step 3: Save user message
    history.append({"role": "user", "content": user_input})

    # Step 4: Send to Groq
    response = client.chat.completions.create(
        messages=history,
        model="llama-3.3-70b-versatile",
    )

    reply = response.choices[0].message.content

    # Step 5: Save assistant reply
    history.append({"role": "assistant", "content": reply})

    print(f"Bot: {reply}")
```

---

## Recap

- **Three ways to call an LLM API:** a platform/`curl`, Python `requests`, or the provider's **SDK**.
- **Every request needs four things:** request body, authorization API key, HTTP method, endpoint.
- **Three roles:** `system` (behavior), `user` (what we send), `assistant` (what we get back).
- **`assistant` messages are what make history work** — append both sides of the conversation to `history` and the bot can handle follow-ups.
- **Gradio** turns any of these calls into a shareable UI.

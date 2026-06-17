# 📝 Prompt Templates in LangChain

**Last Updated:** 2026

Prompt Templates are one of the most important components in LangChain. They allow developers to create dynamic, reusable, and structured prompts instead of hardcoding text for every LLM request.

👉 Key Idea:

**"Write a prompt once and dynamically fill values whenever needed."**

Prompt Templates help create scalable AI applications by separating prompt logic from user input.

---

# 📌 What are Prompt Templates?

A Prompt Template is a predefined prompt with placeholders that can be replaced with actual values at runtime.

Instead of:

```python
prompt = "Explain Machine Learning"
```

We use:

```python
prompt = "Explain {topic}"
```

and later provide:

```python
topic = "Machine Learning"
```

Output:

```text
Explain Machine Learning
```

---

# 🎯 Why Use Prompt Templates?

Without Prompt Templates:

```python
topic = "Deep Learning"

prompt = f"Explain {topic}"
```

Works for small applications.

---

For larger AI systems:

❌ Hard to maintain

❌ Difficult to reuse

❌ Not scalable

---

With Prompt Templates:

✔ Reusable

✔ Dynamic

✔ Cleaner Code

✔ Easier Maintenance

✔ Better Prompt Engineering

---

# 🏗️ Prompt Template Workflow

```text
User Input
      ↓
Prompt Template
      ↓
Variable Injection
      ↓
Final Prompt
      ↓
LLM
      ↓
Response
```

---

# ⚙️ Creating a Prompt Template

## Basic Example

```python
from langchain_core.prompts import PromptTemplate

prompt = PromptTemplate.from_template(
    "Explain {topic} in simple terms."
)
```

---

## Inject Variables

```python
formatted_prompt = prompt.invoke(
    {"topic": "Machine Learning"}
)

print(formatted_prompt)
```

Output:

```text
Explain Machine Learning in simple terms.
```

---

# 📊 Prompt Template Structure

```text
Template
      +
Variables
      ↓
Final Prompt
```

Example:

Template:

```text
What is {topic}?
```

Variable:

```text
topic = AI
```

Final Prompt:

```text
What is AI?
```

---

# 🎭 Multiple Variables

Prompts can contain multiple placeholders.

---

## Example

```python
from langchain_core.prompts import PromptTemplate

prompt = PromptTemplate.from_template(
    """
    Explain {topic}
    for a {audience}.
    """
)
```

---

Invoke:

```python
prompt.invoke(
    {
        "topic": "Neural Networks",
        "audience": "Beginner"
    }
)
```

Output:

```text
Explain Neural Networks
for a Beginner.
```

---

# 🏗️ Prompt + LLM

Prompt Templates are usually connected to LLMs.

```text
Prompt Template
       ↓
LLM
       ↓
Output
```

---

## Example

```python
from langchain_openai import ChatOpenAI
from langchain_core.prompts import PromptTemplate

llm = ChatOpenAI(
    model="gpt-4o-mini"
)

prompt = PromptTemplate.from_template(
    "Explain {topic}"
)

chain = prompt | llm

response = chain.invoke(
    {"topic": "Transformers"}
)

print(response.content)
```

---

# 📚 Types of Prompt Templates

LangChain provides multiple prompt types.

---

# 1️⃣ PromptTemplate

Used for simple text prompts.

Example:

```python
PromptTemplate.from_template(
    "Explain {topic}"
)
```

---

# 2️⃣ ChatPromptTemplate

Used for Chat Models.

Supports:

* System Messages
* Human Messages
* AI Messages

---

Example:

```python
from langchain_core.prompts import ChatPromptTemplate

prompt = ChatPromptTemplate.from_messages(
    [
        ("system",
         "You are a helpful tutor."),
        ("human",
         "{question}")
    ]
)
```

---

Invoke:

```python
prompt.invoke(
    {
        "question":
        "What is Deep Learning?"
    }
)
```

---

# 🏗️ Chat Prompt Architecture

```text
System Message
       ↓
User Message
       ↓
Chat Model
       ↓
Response
```

---

# Example Chat Prompt

```python
prompt = ChatPromptTemplate.from_messages(
[
    (
      "system",
      "You are a coding assistant."
    ),
    (
      "human",
      "{query}"
    )
]
)
```

---

User:

```text
Write Python code for sorting.
```

Generated Prompt:

```text
System:
You are a coding assistant.

Human:
Write Python code for sorting.
```

---

# 🎯 System Messages

System messages define model behavior.

---

Example

```python
(
 "system",
 "You are an expert Data Scientist."
)
```

The model will respond as a Data Scientist.

---

Examples:

```text
You are a Teacher
```

```text
You are a Python Expert
```

```text
You are an Interview Coach
```

---

# 🎯 Human Messages

Represent user input.

Example:

```python
(
 "human",
 "{question}"
)
```

---

Input:

```text
What is Machine Learning?
```

---

# 🎯 AI Messages

Provide previous assistant responses.

Example:

```python
(
 "ai",
 "Machine Learning is..."
)
```

Useful for few-shot prompting.

---

# 📖 Few-Shot Prompting

Few-shot prompting provides examples before the actual question.

---

Example:

```text
Question:
2 + 2

Answer:
4

Question:
3 + 3

Answer:
6

Question:
5 + 5

Answer:
?
```

The model learns the pattern.

---

# FewShotPromptTemplate

```python
from langchain_core.prompts import FewShotPromptTemplate
```

Used when providing examples improves performance.

---

# 🏗️ Few-Shot Architecture

```text
Examples
     ↓
Prompt Template
     ↓
User Query
     ↓
LLM
     ↓
Response
```

---

# Dynamic Prompt Generation

Prompt Templates allow dynamic prompts.

Example:

```python
topic = "AI"

prompt.invoke(
{
   "topic": topic
}
)
```

Generated:

```text
Explain AI
```

---

# Prompt Engineering Best Practices

---

## Be Specific

Bad:

```text
Tell me about AI.
```

Good:

```text
Explain AI for a 10-year-old
using simple examples.
```

---

## Define Role

Example:

```text
You are an expert teacher.
```

---

## Specify Output Format

Example:

```text
Give answer in JSON format.
```

---

## Use Constraints

Example:

```text
Explain in under 100 words.
```

---

# 🌍 Real-World Applications

---

## Chatbots

Dynamic conversations.

---

## RAG Systems

Inject retrieved documents.

---

## AI Tutors

Generate customized explanations.

---

## Code Assistants

Generate programming solutions.

---

## Enterprise AI

Dynamic workflows.

---

# 🚀 Advantages

✔ Reusable

✔ Dynamic

✔ Scalable

✔ Easy Maintenance

✔ Better Prompt Engineering

✔ Works with Any LLM

---

# ❌ Limitations

❌ Poor prompt design affects results

❌ Large prompts increase token cost

❌ Requires prompt engineering skills

---

# 🎤 Interview Questions

### What is a Prompt Template?

A reusable prompt containing variables that are dynamically filled during execution.

---

### Difference Between PromptTemplate and ChatPromptTemplate?

PromptTemplate works with text prompts.

ChatPromptTemplate works with message-based chat models.

---

### Why Use Prompt Templates?

To create reusable, maintainable, and dynamic prompts.

---

### What is Few-Shot Prompting?

Providing examples before the actual query to guide model behavior.

---

### What is a System Message?

A message that defines how the AI should behave.

---

# 📚 Summary

Prompt Templates allow developers to build dynamic and reusable prompts for LLM applications.

👉 Key Takeaway:

**"Separate prompt logic from user data."**

### Complete Workflow

```text
User Input
      ↓
Prompt Template
      ↓
Variable Injection
      ↓
Final Prompt
      ↓
LLM
      ↓
Response
```

Prompt Templates are the foundation of modern LangChain applications including **Chatbots, AI Agents, RAG Systems, Virtual Assistants, Code Generators, and Enterprise AI Solutions.**

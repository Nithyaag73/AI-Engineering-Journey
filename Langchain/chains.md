# ⛓️ Chains in LangChain

**Last Updated:** 2026

Chains are one of the core building blocks of LangChain. A Chain connects multiple components together and executes them sequentially to solve a task.

👉 Key Idea:

**"Output of one component becomes the input of the next component."**

Chains allow developers to build structured AI workflows instead of making a single LLM call.

---

# 📌 What are Chains?

A Chain is a sequence of operations that work together to produce a final result.

Example:

```text id="w1g23a"
User Input
      ↓
Prompt Template
      ↓
LLM
      ↓
Output
```

This entire workflow is called a Chain.

---

# 🎯 Why Use Chains?

Without Chains:

```python id="j82mka"
prompt = f"Explain {topic}"

response = llm.invoke(prompt)
```

Works for simple tasks.

---

For complex applications:

❌ Difficult to manage

❌ Hard to scale

❌ Repeated code

---

With Chains:

✔ Modular

✔ Reusable

✔ Scalable

✔ Easy to maintain

✔ Easy debugging

---

# 🏗️ Chain Architecture

```text id="0o6zv3"
Input
  ↓
Prompt Template
  ↓
LLM
  ↓
Parser
  ↓
Output
```

Each component performs one specific task.

---

# ⚙️ Basic Chain

The simplest chain consists of:

```text id="8frz5m"
Prompt
   ↓
LLM
```

---

## Example

```python id="vgh79w"
from langchain_openai import ChatOpenAI
from langchain_core.prompts import PromptTemplate

llm = ChatOpenAI(
    model="gpt-4o-mini"
)

prompt = PromptTemplate.from_template(
    "Explain {topic}"
)

chain = prompt | llm
```

---

Invoke:

```python id="l9x7jw"
response = chain.invoke(
    {"topic": "Machine Learning"}
)

print(response.content)
```

---

# 🏗️ Chain Workflow

```text id="trp04j"
Topic
  ↓
Prompt Template
  ↓
Final Prompt
  ↓
LLM
  ↓
Generated Answer
```

---

# 📚 Components of a Chain

A Chain may contain:

* Prompt Templates
* Chat Models
* Output Parsers
* Retrievers
* Tools
* Memory
* Agents

---

# Example Complete Chain

```text id="dh8e4j"
Input
 ↓
Prompt
 ↓
Retriever
 ↓
LLM
 ↓
Parser
 ↓
Output
```

---

# ⚡ LangChain Expression Language (LCEL)

Modern LangChain chains are built using LCEL.

Operator:

```python id="d91h6y"
|
```

acts like a pipeline.

---

Example:

```python id="9g2pk7"
chain = prompt | llm
```

Equivalent to:

```text id="s0l18f"
Prompt Output
      ↓
LLM Input
```

---

# Simple Chain Example

```python id="kqv19d"
from langchain_core.prompts import PromptTemplate
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(
    model="gpt-4o-mini"
)

prompt = PromptTemplate.from_template(
    "Explain {topic}"
)

chain = prompt | llm

response = chain.invoke(
    {"topic": "Deep Learning"}
)

print(response.content)
```

---

# 🏗️ Sequential Chains

A Sequential Chain performs multiple steps.

Example:

Step 1:

```text id="g2y3zp"
Generate Topic Summary
```

Step 2:

```text id="w8k0rj"
Generate Quiz Questions
```

---

Architecture:

```text id="6d8x9r"
Input
 ↓
Summary Chain
 ↓
Quiz Chain
 ↓
Output
```

---

# Example Workflow

```text id="0qv4lu"
Machine Learning
       ↓
Summary
       ↓
Quiz Questions
```

---

# 🧠 Multi-Step Chain

Example:

```text id="9v7eoq"
User Topic
      ↓
Explanation
      ↓
Summary
      ↓
Quiz
      ↓
Flashcards
```

Each step is a separate chain.

---

# 📤 Output Parsers in Chains

Output parsers convert raw LLM responses into structured formats.

---

Without Parser:

```text id="2rwgho"
Machine Learning is...
```

---

With Parser:

```json id="6t4k7e"
{
  "topic": "Machine Learning",
  "level": "Beginner"
}
```

---

Example:

```python id="f5u2yn"
chain = prompt | llm | parser
```

---

# 🔍 Retrieval Chains

Used in RAG applications.

Architecture:

```text id="6ztf3h"
User Question
      ↓
Retriever
      ↓
Relevant Documents
      ↓
LLM
      ↓
Answer
```

---

Example:

```python id="r8h2lf"
retrieval_chain = (
    retriever
    | llm
)
```

---

# 📄 Document Question Answering Chain

```text id="o3r8pk"
PDF
 ↓
Chunking
 ↓
Embeddings
 ↓
Vector Store
 ↓
Retriever
 ↓
LLM
 ↓
Answer
```

---

# 🔄 Chain Composition

Chains can be combined together.

Example:

```python id="9x7j3w"
chain = (
    prompt
    | llm
    | parser
)
```

---

Workflow:

```text id="u8n5qr"
Prompt
  ↓
LLM
  ↓
Parser
```

---

# ⚙️ Runnable Chains

Everything in LangChain is now a Runnable.

Examples:

```python id="y0s3tw"
PromptTemplate
```

```python id="r8q2am"
ChatOpenAI
```

```python id="d4u6cf"
Retriever
```

can all participate in chains.

---

# 🎯 Real-World Example

Question:

```text id="yxk6gb"
Explain Neural Networks
```

Workflow:

```text id="j0r7af"
Question
    ↓
Prompt Template
    ↓
GPT Model
    ↓
Output Parser
    ↓
Final Answer
```

---

# 🌍 Applications of Chains

---

## Chatbots

Conversation pipelines.

---

## RAG Systems

Retriever + LLM.

---

## AI Tutors

Explanation → Quiz → Summary.

---

## Research Assistants

Search → Analyze → Summarize.

---

## Enterprise AI

Multi-step workflows.

---

# 🚀 Advantages

✔ Modular Design

✔ Reusable Components

✔ Easy Maintenance

✔ Scalable Architecture

✔ Supports Complex Workflows

✔ Works with Any LLM

---

# ❌ Limitations

❌ Large Chains Become Complex

❌ Debugging Multi-Step Chains Can Be Difficult

❌ More API Calls Increase Cost

---

# 🔀 Chains vs Agents

| Feature         | Chains     | Agents    |
| --------------- | ---------- | --------- |
| Workflow        | Fixed      | Dynamic   |
| Decision Making | No         | Yes       |
| Tool Selection  | Predefined | Automatic |
| Complexity      | Low        | High      |

---

Example:

Chain:

```text id="g7q9cf"
Input
 ↓
Prompt
 ↓
LLM
 ↓
Output
```

Always follows the same path.

---

Agent:

```text id="z9s8yr"
Input
 ↓
Reason
 ↓
Choose Tool
 ↓
Execute
 ↓
Answer
```

Path changes dynamically.

---

# 🎤 Interview Questions

### What is a Chain in LangChain?

A Chain is a sequence of components where the output of one step becomes the input of the next.

---

### Why Use Chains?

To create reusable, modular, and scalable AI workflows.

---

### What is LCEL?

LangChain Expression Language used to connect components using the pipe operator (`|`).

---

### Difference Between Chains and Agents?

Chains follow predefined workflows while Agents can make decisions dynamically.

---

### What Components Can Be Part of a Chain?

* Prompts
* LLMs
* Retrievers
* Parsers
* Tools
* Memory

---

# 📚 Summary

Chains are the foundation of LangChain workflows.

They connect multiple AI components together into structured pipelines.

👉 Key Takeaway:

**"Output of one component becomes input to the next."**

### Complete Workflow

```text id="0l4p6s"
User Input
      ↓
Prompt Template
      ↓
LLM
      ↓
Output Parser
      ↓
Final Response
```

Chains power modern LangChain applications such as **Chatbots, RAG Systems, AI Tutors, Research Assistants, Enterprise AI Workflows, and Multi-Step LLM Pipelines.**

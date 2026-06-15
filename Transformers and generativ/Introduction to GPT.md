# 🤖 GPT (Generative Pre-trained Transformer)

**Last Updated:** 2026

GPT (Generative Pre-trained Transformer) is a family of large language models developed by OpenAI based on the **Transformer Decoder Architecture**.

📄 **First Paper:** *Improving Language Understanding by Generative Pre-Training (2018)*

👉 Key Idea:

**"Generate the next word using previously seen words."**

Unlike BERT, which focuses on understanding language, GPT is designed primarily for **text generation**.

---

# 📌 What is GPT?

GPT is a **Decoder-Only Transformer Model** that learns language by predicting the next token in a sequence.

Example:

Input:

```text
I love machine
```

GPT predicts:

```text
learning
```

Then:

```text
I love machine learning
```

GPT predicts:

```text
because
```

and continues generating text.

---

# 🎯 Why GPT?

Traditional NLP models were designed for specific tasks:

* Translation
* Sentiment Analysis
* Classification

GPT introduced a new approach:

```text
One Large Model
       ↓
Many Different Tasks
```

The same model can perform:

✔ Text Generation

✔ Summarization

✔ Translation

✔ Question Answering

✔ Coding

✔ Chatbots

---

# 🏗️ GPT Architecture

GPT uses only the **Transformer Decoder Stack**.

```text
Input Prompt
      ↓
Tokenization
      ↓
Token Embeddings
      ↓
Positional Embeddings
      ↓
Masked Multi-Head Attention
      ↓
Feed Forward Network
      ↓
Output Probabilities
      ↓
Next Token Prediction
```

---

# 🔀 GPT vs BERT

| Feature            | GPT                   | BERT                     |
| ------------------ | --------------------- | ------------------------ |
| Architecture       | Decoder Only          | Encoder Only             |
| Training Objective | Next Token Prediction | Masked Language Modeling |
| Context Direction  | Left to Right         | Bidirectional            |
| Best For           | Generation            | Understanding            |
| Example Tasks      | Chatbots, Writing     | Classification, NER      |

---

# 🧠 How GPT Works

GPT predicts one token at a time.

Example:

Input:

```text
The capital of France is
```

Prediction:

```text
Paris
```

Updated Input:

```text
The capital of France is Paris
```

Prediction:

```text
.
```

This process continues until the response is complete.

---

# 🎭 Autoregressive Language Modeling

GPT uses:

```text
Previous Tokens
      ↓
Predict Next Token
```

This training method is called:

```text
Autoregressive Language Modeling
```

---

## Example

Sentence:

```text
I love machine learning
```

Training samples:

```text
I          → love
I love     → machine
I love machine → learning
```

GPT learns to predict the next token repeatedly.

---

# 📐 GPT Training Objective

GPT minimizes prediction error using Cross-Entropy Loss.

Loss=-\sum y\log(\hat{y})

Where:

* y = Actual token
* ŷ = Predicted token probability

---

# 🎯 Masked Self-Attention

GPT uses **Causal (Masked) Self-Attention**.

This prevents the model from seeing future tokens.

Example:

```text
I love machine
```

GPT can attend to:

```text
I
love
machine
```

But cannot see:

```text
learning
```

because it has not been generated yet.

---

# ⚙️ Components of GPT

---

## 1️⃣ Token Embeddings

Convert words into vectors.

Example:

```text
AI → Vector
```

---

## 2️⃣ Positional Embeddings

Provide word order information.

Example:

```text
Position 1
Position 2
Position 3
```

---

## 3️⃣ Masked Multi-Head Attention

Allows each token to attend only to previous tokens.

---

## 4️⃣ Feed Forward Network

Learns complex language patterns.

---

## 5️⃣ Softmax Layer

Predicts probability of next token.

---

# 📊 GPT Model Evolution

| Model   | Release Year |
| ------- | ------------ |
| GPT-1   | 2018         |
| GPT-2   | 2019         |
| GPT-3   | 2020         |
| GPT-3.5 | 2022         |
| GPT-4   | 2023         |
| GPT-4o  | 2024         |
| GPT-5   | 2025         |

---

# 🚀 GPT Family Improvements

---

## GPT-1

* 117 Million Parameters
* Proof of concept

---

## GPT-2

* 1.5 Billion Parameters
* Better text generation

---

## GPT-3

* 175 Billion Parameters
* Few-shot learning

---

## GPT-4

* Strong reasoning
* Multimodal capabilities

---

## GPT-5

* Improved reasoning
* Better coding
* Better instruction following
* More reliable responses

---

# 💻 Simple GPT Example

Prompt:

```text
Explain machine learning.
```

Output:

```text
Machine learning is a field of artificial intelligence
that enables computers to learn patterns from data
without being explicitly programmed.
```

---

# 🌍 Applications

---

## Chatbots

* ChatGPT
* Virtual Assistants

---

## Content Generation

* Blogs
* Articles
* Stories

---

## Code Generation

* Python
* JavaScript
* SQL

---

## Translation

Language conversion tasks.

---

## Summarization

Long document summarization.

---

## Question Answering

Answering user queries.

---

# 🚀 Advantages

✔ Excellent text generation

✔ Scalable architecture

✔ Supports multiple tasks

✔ Strong contextual understanding

✔ Few-shot and zero-shot learning

---

# ❌ Limitations

❌ Can generate incorrect information

❌ Large computational requirements

❌ Expensive training

❌ May produce biased outputs

---

# 🔀 Decoder-Only vs Encoder-Only vs Encoder-Decoder

| Model Type      | Example  | Purpose                     |
| --------------- | -------- | --------------------------- |
| Encoder Only    | BERT     | Understanding               |
| Decoder Only    | GPT      | Generation                  |
| Encoder-Decoder | T5, BART | Translation & Summarization |

---

# 📚 Summary

GPT is a Decoder-Only Transformer model designed for text generation using autoregressive language modeling.

👉 Key Takeaway:

**"Predict the next token using all previous tokens."**

### GPT Pipeline

```text
Input Prompt
      ↓
Tokenization
      ↓
Embeddings
      ↓
Masked Self-Attention
      ↓
Feed Forward Network
      ↓
Softmax
      ↓
Next Token Prediction
      ↓
Generated Text
```

GPT has become the foundation of modern generative AI systems including **ChatGPT, coding assistants, content generators, virtual assistants, and many large language models used today**.

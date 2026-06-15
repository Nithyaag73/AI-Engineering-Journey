# 🏗️ GPT Architecture (Decoder-Only Transformer)

**Last Updated:** 2026

GPT (Generative Pre-trained Transformer) is a **Decoder-Only Transformer Architecture** developed by OpenAI for text generation and language understanding.

📄 **Paper:** *Improving Language Understanding by Generative Pre-Training (2018)*

👉 Key Idea:

**"Generate the next token using previously generated tokens."**

Unlike BERT, GPT uses only the **Transformer Decoder** and is trained using **Autoregressive Language Modeling**.

---

# 📌 Overview of GPT Architecture

GPT consists of multiple stacked Transformer Decoder blocks.

```text
Input Text
     ↓
Tokenization
     ↓
Token Embeddings
     ↓
Positional Embeddings
     ↓
Decoder Block 1
     ↓
Decoder Block 2
     ↓
...
     ↓
Decoder Block N
     ↓
Linear Layer
     ↓
Softmax
     ↓
Next Token Prediction
```

---

# 🎯 Main Components of GPT

GPT architecture consists of:

1. Token Embeddings
2. Positional Embeddings
3. Masked Multi-Head Self-Attention
4. Feed Forward Neural Network
5. Residual Connections
6. Layer Normalization
7. Linear + Softmax Layer

---

# 🏗️ High-Level GPT Architecture

```text
Input Tokens
      ↓
Token Embeddings
      ↓
Positional Embeddings
      ↓
─────────────────
 Decoder Block 1
─────────────────
      ↓
─────────────────
 Decoder Block 2
─────────────────
      ↓
...
      ↓
─────────────────
 Decoder Block N
─────────────────
      ↓
Linear Layer
      ↓
Softmax
      ↓
Next Token
```

---

# ⚙️ 1. Token Embeddings

Words cannot be processed directly.

Each token is converted into a dense vector.

Example:

```text
I love AI
```

↓

```text
[I] [love] [AI]
```

↓

```text
Vector Representations
```

Example:

```text
I    → [0.12, 0.45, ...]
love → [0.91, 0.32, ...]
AI   → [0.65, 0.88, ...]
```

---

# ⚙️ 2. Positional Embeddings

Transformers process all tokens simultaneously.

Position information is therefore added.

Example:

```text
I love AI
```

Position IDs:

```text
0 1 2
```

Each position receives a learnable embedding.

---

# 📊 Input Representation

```text
Final Input
=
Token Embedding
+
Position Embedding
```

---

# ⚙️ 3. Decoder Block

The Decoder Block is the heart of GPT.

Each block contains:

```text
Masked Multi-Head Attention
            ↓
Add & Layer Norm
            ↓
Feed Forward Network
            ↓
Add & Layer Norm
```

---

# 🎭 4. Masked Multi-Head Self-Attention

GPT uses **Causal Attention**.

Future tokens are hidden during training.

Example:

Input:

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

## Self-Attention Formula

Attention(Q,K,V)=Softmax\left(\frac{QK^T}{\sqrt{d_k}}\right)V

Where:

* Q = Query
* K = Key
* V = Value

---

# 🔍 Query, Key and Value

Each token generates:

```text
Query (Q)
Key (K)
Value (V)
```

Example:

```text
Machine Learning
```

The model learns:

```text
Machine ↔ Learning
```

relationships through attention.

---

# ⚙️ 5. Multi-Head Attention

Instead of one attention mechanism, GPT uses multiple attention heads.

Example:

```text
Head 1 → Grammar
Head 2 → Context
Head 3 → Semantics
Head 4 → Relationships
```

---

## Multi-Head Formula

MultiHead(Q,K,V)=Concat(head_1,...,head_h)W^O

---

# ⚙️ 6. Residual Connections

Residual connections help preserve information.

```text
Input
  +
Attention Output
```

Benefits:

✔ Stable training

✔ Faster convergence

✔ Better gradient flow

---

# ⚙️ 7. Layer Normalization

Layer Normalization stabilizes activations.

```text
Attention Output
       ↓
Layer Norm
```

Benefits:

✔ Faster learning

✔ Reduced training instability

---

# ⚙️ 8. Feed Forward Network (FFN)

After attention, each token passes through a neural network.

---

## FFN Formula

FFN(x)=Max(0,xW_1+b_1)W_2+b_2

---

Purpose:

✔ Learn complex patterns

✔ Increase model capacity

✔ Improve representations

---

# ⚙️ 9. Linear Layer

Transforms decoder outputs into vocabulary scores.

Example:

Vocabulary:

```text
Paris
London
Berlin
Tokyo
```

Output:

```text
Paris  → 9.5
London → 1.2
Berlin → 0.5
Tokyo  → 0.3
```

---

# ⚙️ 10. Softmax Layer

Converts scores into probabilities.

Probability Formula:

P(y_i)=\frac{e^{z_i}}{\sum_j e^{z_j}}

Example:

| Token  | Probability |
| ------ | ----------- |
| Paris  | 0.92        |
| London | 0.04        |
| Berlin | 0.02        |
| Tokyo  | 0.02        |

Predicted token:

```text
Paris
```

---

# 🔄 Autoregressive Generation

GPT generates text one token at a time.

Example:

Input:

```text
I love
```

Prediction:

```text
machine
```

New Input:

```text
I love machine
```

Prediction:

```text
learning
```

This process repeats until completion.

---

# 📊 Complete Decoder Block

```text
Input
  ↓
Masked Multi-Head Attention
  ↓
Add & Layer Norm
  ↓
Feed Forward Network
  ↓
Add & Layer Norm
  ↓
Output
```

---

# 📈 GPT Model Sizes

| Model       | Layers               |
| ----------- | -------------------- |
| GPT-1       | 12                   |
| GPT-2 Small | 12                   |
| GPT-2 XL    | 48                   |
| GPT-3       | 96                   |
| GPT-4       | Large Scale          |
| GPT-5       | Advanced Large Scale |

---

# 🌍 Applications

### Chatbots

* ChatGPT
* Virtual Assistants

---

### Content Generation

* Blogs
* Stories
* Articles

---

### Code Generation

* Python
* Java
* SQL

---

### Translation

Language Translation

---

### Summarization

Document Summarization

---

# 🚀 Advantages

✔ Excellent text generation

✔ Captures long-range dependencies

✔ Scalable architecture

✔ Supports few-shot learning

✔ State-of-the-art performance

---

# ❌ Limitations

❌ Large computational cost

❌ High memory usage

❌ Expensive training

❌ May hallucinate facts

---

# 🔀 GPT vs BERT Architecture

| Feature            | GPT                   | BERT          |
| ------------------ | --------------------- | ------------- |
| Architecture       | Decoder Only          | Encoder Only  |
| Attention          | Masked                | Bidirectional |
| Purpose            | Generation            | Understanding |
| Training Objective | Next Token Prediction | MLM           |

---

# 📚 Summary

GPT is a Decoder-Only Transformer architecture designed for autoregressive text generation.

👉 Key Takeaway:

**"Use previous tokens to predict the next token."**

### GPT Architecture Pipeline

```text
Input Text
      ↓
Tokenization
      ↓
Token Embeddings
      ↓
Position Embeddings
      ↓
Decoder Blocks
      ↓
Linear Layer
      ↓
Softmax
      ↓
Next Token Prediction
```

The GPT architecture powers modern AI systems such as **ChatGPT, GPT-4, GPT-5, coding assistants, content generators, and many large language models used today**.

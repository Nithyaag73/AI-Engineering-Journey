# 🏗️ Transformer Encoder Architecture

**Last Updated:** 2026

The **Encoder** is one of the main building blocks of the Transformer architecture introduced in:

📄 **"Attention Is All You Need" (2017)**

The encoder's job is to **understand the input sequence and generate contextual representations** that capture the meaning of each token.

👉 Key Idea:

**"Read the entire input, understand relationships between words, and create rich contextual embeddings."**

---

# 📌 What is a Transformer Encoder?

The Transformer Encoder is responsible for:

* Understanding input text
* Capturing context
* Learning word relationships
* Producing meaningful embeddings

It is used in models such as:

* BERT
* RoBERTa
* DistilBERT
* ALBERT
* ELECTRA

---

# 🎯 Purpose of Encoder

Given an input sentence:

```text
The cat sat on the mat.
```

The encoder learns:

```text
cat ↔ sat
cat ↔ mat
sat ↔ mat
```

and creates contextual representations for every word.

---

# 🏛️ High-Level Architecture

```text
Input Sentence
      ↓
Input Embedding
      ↓
Positional Encoding
      ↓
Multi-Head Self Attention
      ↓
Add & Normalize
      ↓
Feed Forward Network
      ↓
Add & Normalize
      ↓
Encoder Output
```

---

# ⚙️ Components of Encoder

The encoder consists of:

1. Input Embedding
2. Positional Encoding
3. Multi-Head Self Attention
4. Add & Layer Normalization
5. Feed Forward Neural Network
6. Encoder Stack

---

# 1️⃣ Input Embeddings

Transformers cannot process words directly.

Words are converted into vectors.

Example:

```text
I       → [0.25, 0.14, ...]
Love    → [0.61, 0.82, ...]
AI      → [0.44, 0.91, ...]
```

These vectors are called embeddings.

---

# 2️⃣ Positional Encoding

Unlike RNNs, Transformers process all words simultaneously.

Therefore, word order must be added manually.

Example:

```text
I Love AI
```

and

```text
AI Love I
```

contain the same words but different meanings.

Positional Encoding provides position information.

---

## Positional Encoding Formula

PE(pos,2i)=\sin\left(\frac{pos}{10000^{2i/d_{model}}}\right)

---

PE(pos,2i+1)=\cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)

---

# 3️⃣ Multi-Head Self Attention

The encoder uses Self-Attention to understand relationships between words.

For every token:

```text
Input
 ↓
Query (Q)
Key (K)
Value (V)
```

are generated.

---

## Self-Attention Formula

Attention(Q,K,V)=Softmax\left(\frac{QK^T}{\sqrt{d_k}}\right)V

---

### Example

Sentence:

```text
The animal didn't cross the road because it was tired.
```

Self-attention learns:

```text
it → animal
```

instead of:

```text
it → road
```

---

# 4️⃣ Multi-Head Attention

Instead of one attention layer, the encoder uses multiple attention heads.

Example:

```text
Head 1 → Grammar
Head 2 → Meaning
Head 3 → Context
Head 4 → Relationships
```

Each head learns different patterns.

---

## Multi-Head Attention Formula

MultiHead(Q,K,V)=Concat(head_1,...,head_h)W^O

---

# 5️⃣ Add & Layer Normalization

After attention:

```text
Input + Attention Output
```

is added together.

This is called a **Residual Connection**.

---

### Benefits

✔ Faster training

✔ Stable gradients

✔ Better convergence

---

Then Layer Normalization is applied.

```text
Attention Output
      +
Residual Connection
      ↓
Layer Normalization
```

---

# 6️⃣ Feed Forward Neural Network (FFN)

Each token passes through a small neural network independently.

---

## FFN Formula

FFN(x)=Max(0,xW_1+b_1)W_2+b_2

---

### Purpose

✔ Learn complex patterns

✔ Increase model capacity

✔ Improve representation quality

---

# 7️⃣ Encoder Stack

A Transformer does not use only one encoder.

Multiple encoder layers are stacked.

Example:

```text
Encoder Layer 1
       ↓
Encoder Layer 2
       ↓
Encoder Layer 3
       ↓
...
       ↓
Encoder Layer N
```

Common choices:

| Model         | Encoder Layers |
| ------------- | -------------- |
| BERT Base     | 12             |
| BERT Large    | 24             |
| RoBERTa Base  | 12             |
| RoBERTa Large | 24             |

---

# 📊 Complete Encoder Workflow

```text
Input Sentence
       ↓
Embedding
       ↓
Positional Encoding
       ↓
Multi-Head Self Attention
       ↓
Add & Normalize
       ↓
Feed Forward Network
       ↓
Add & Normalize
       ↓
Encoder Output
```

---

# 🧠 Why Encoder Works Well?

Because every token can attend to:

```text
All Other Tokens
```

simultaneously.

This allows:

✔ Better context understanding

✔ Long-range dependency learning

✔ Parallel processing

---

# 🌍 Applications

### Language Understanding

* BERT
* RoBERTa
* ALBERT

---

### Search Engines

* Semantic Search
* Information Retrieval

---

### Question Answering

* Reading Comprehension
* FAQ Systems

---

### Text Classification

* Sentiment Analysis
* Spam Detection

---

# ✅ Advantages

✔ Parallel computation

✔ Captures long-range dependencies

✔ Rich contextual embeddings

✔ Highly scalable

✔ State-of-the-art NLP performance

---

# ❌ Disadvantages

❌ High memory usage

❌ Computationally expensive

❌ Requires large datasets

---

# 📚 Summary

The Transformer Encoder is responsible for understanding input sequences and generating contextual representations.

👉 Key Takeaway:

**"Every token looks at every other token to understand context."**

### Encoder Pipeline

```text
Input
 ↓
Embedding
 ↓
Positional Encoding
 ↓
Multi-Head Attention
 ↓
Add & Normalize
 ↓
Feed Forward Network
 ↓
Add & Normalize
 ↓
Output Representation
```

The encoder forms the foundation of powerful language understanding models such as **BERT, RoBERTa, ALBERT, ELECTRA, and DistilBERT**.

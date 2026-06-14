# 🏗️ Transformer Decoder Architecture

**Last Updated:** 2026

The **Decoder** is one of the two major components of the Transformer architecture introduced in:

📄 **"Attention Is All You Need" (2017)**

The decoder's primary role is to **generate output sequences token by token** using information from previous tokens and (optionally) the encoder output.

👉 Key Idea:

**"Generate the next token using previously generated tokens and contextual information."**

---

# 📌 What is a Transformer Decoder?

The Transformer Decoder is responsible for:

* Text Generation
* Translation
* Summarization
* Question Answering
* Conversational AI

It is used in models such as:

* GPT
* GPT-2
* GPT-3
* GPT-4
* LLaMA
* Claude
* Mistral

---

# 🎯 Purpose of Decoder

Given:

```text
Input Prompt:
The capital of France is
```

The decoder predicts:

```text
Paris
```

Then continues generating:

```text
The capital of France is Paris.
```

---

# 🏛️ High-Level Architecture

```text
Input Tokens
      ↓
Embedding Layer
      ↓
Positional Encoding
      ↓
Masked Multi-Head Attention
      ↓
Add & Normalize
      ↓
Feed Forward Network
      ↓
Add & Normalize
      ↓
Output Probabilities
      ↓
Next Token Prediction
```

---

# ⚙️ Components of Decoder

The decoder consists of:

1. Input Embedding
2. Positional Encoding
3. Masked Multi-Head Self-Attention
4. Add & Layer Normalization
5. Feed Forward Neural Network
6. Output Projection & Softmax
7. Decoder Stack

---

# 1️⃣ Input Embeddings

Words are converted into dense vectors.

Example:

```text
I      → [0.24, 0.61, ...]
Love   → [0.81, 0.13, ...]
AI     → [0.92, 0.47, ...]
```

These vectors become the decoder input.

---

# 2️⃣ Positional Encoding

Transformers process tokens in parallel.

To preserve word order:

```text
I Love AI
```

must be different from:

```text
AI Love I
```

Positional encoding adds sequence information.

---

## Positional Encoding Formula

PE(pos,2i)=\sin\left(\frac{pos}{10000^{2i/d_{model}}}\right)

---

PE(pos,2i+1)=\cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)

---

# 3️⃣ Masked Multi-Head Self-Attention

This is the most important component of the decoder.

Unlike the encoder:

👉 The decoder cannot see future words.

---

### Example

During generation:

```text
I love machine
```

The model can see:

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

# 🎭 Why Masking?

Without masking:

```text
The model cheats.
```

It would know future words during training.

Masking ensures:

```text
Current Token
      ↓
Can Attend Only To
Previous Tokens
```

---

# 📐 Masked Self-Attention Formula

Attention(Q,K,V)=Softmax\left(\frac{QK^T+Mask}{\sqrt{d_k}}\right)V

---

# 4️⃣ Multi-Head Attention

The decoder uses multiple attention heads.

Example:

```text
Head 1 → Grammar
Head 2 → Context
Head 3 → Relationships
Head 4 → Meaning
```

Each head learns different linguistic patterns.

---

## Multi-Head Attention Formula

MultiHead(Q,K,V)=Concat(head_1,...,head_h)W^O

---

# 5️⃣ Add & Layer Normalization

After attention:

```text
Input
 +
Attention Output
```

Residual connections help preserve information.

Benefits:

✔ Faster convergence

✔ Stable training

✔ Better gradient flow

---

# 6️⃣ Feed Forward Neural Network (FFN)

Each token independently passes through a neural network.

---

## FFN Formula

FFN(x)=Max(0,xW_1+b_1)W_2+b_2

---

### Purpose

✔ Learn complex patterns

✔ Improve representation quality

✔ Increase model capacity

---

# 7️⃣ Output Projection Layer

Decoder output is transformed into vocabulary probabilities.

Example:

```text
Vocabulary:
Paris
London
Berlin
Tokyo
```

Output:

| Token  | Probability |
| ------ | ----------- |
| Paris  | 0.92        |
| London | 0.04        |
| Berlin | 0.02        |
| Tokyo  | 0.02        |

---

# 🔄 Softmax Layer

Softmax converts logits into probabilities.

P(y_i)=\frac{e^{z_i}}{\sum_j e^{z_j}}

---

# 🏗️ Decoder Stack

Multiple decoder layers are stacked.

```text
Decoder Layer 1
       ↓
Decoder Layer 2
       ↓
Decoder Layer 3
       ↓
...
       ↓
Decoder Layer N
```

Examples:

| Model       | Decoder Layers |
| ----------- | -------------- |
| GPT-2 Small | 12             |
| GPT-3       | 96             |
| LLaMA 2 7B  | 32             |
| LLaMA 2 70B | 80             |

---

# 📊 Complete Decoder Workflow

```text
Input Tokens
      ↓
Embedding Layer
      ↓
Positional Encoding
      ↓
Masked Multi-Head Attention
      ↓
Add & Normalize
      ↓
Feed Forward Network
      ↓
Add & Normalize
      ↓
Vocabulary Probabilities
      ↓
Next Token Prediction
```

---

# 🤖 Autoregressive Generation

Decoder-only models generate tokens one at a time.

Example:

```text
Input:
I love
```

Prediction:

```text
machine
```

Next input:

```text
I love machine
```

Prediction:

```text
learning
```

Process repeats until completion.

---

# 🔀 Encoder vs Decoder

| Feature               | Encoder             | Decoder               |
| --------------------- | ------------------- | --------------------- |
| Purpose               | Understanding       | Generation            |
| Attention             | Full Self-Attention | Masked Self-Attention |
| Future Tokens Visible | Yes                 | No                    |
| Example Models        | BERT, RoBERTa       | GPT, LLaMA            |

---

# 🌍 Applications

### Large Language Models

* ChatGPT
* GPT-4
* Claude
* Gemini
* LLaMA

---

### Text Generation

* Story Writing
* Content Creation
* Code Generation

---

### Chatbots

* Conversational AI
* Virtual Assistants

---

### Translation

* Language Generation

---

# ✅ Advantages

✔ Excellent text generation

✔ Captures long-range dependencies

✔ Parallel training

✔ Highly scalable

✔ State-of-the-art performance

---

# ❌ Disadvantages

❌ High computational cost

❌ Large memory usage

❌ Requires massive training data

---

# 📚 Summary

The Transformer Decoder is responsible for generating output sequences one token at a time.

👉 Key Takeaway:

**"Use previous tokens to predict the next token."**

### Decoder Pipeline

```text
Input Tokens
      ↓
Embedding
      ↓
Positional Encoding
      ↓
Masked Self-Attention
      ↓
Add & Normalize
      ↓
Feed Forward Network
      ↓
Softmax
      ↓
Next Token
```

Modern generative AI systems such as **GPT, ChatGPT, Claude, Gemini, LLaMA, Mistral, and DeepSeek** are built primarily on Decoder-only Transformer architectures.

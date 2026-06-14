# 🤖 BERT (Bidirectional Encoder Representations from Transformers)

**Last Updated:** 2026

BERT (Bidirectional Encoder Representations from Transformers) is a Transformer-based language model developed by Google in 2018.

📄 **Paper:** *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding*

👉 Key Idea:

**"Understand words using both left and right context simultaneously."**

BERT revolutionized Natural Language Processing (NLP) by achieving state-of-the-art results on many language understanding tasks.

---

# 📌 What is BERT?

BERT is an **Encoder-Only Transformer model** designed for:

* Text Classification
* Sentiment Analysis
* Question Answering
* Named Entity Recognition (NER)
* Semantic Search
* Text Similarity

Unlike traditional language models that read text in one direction, BERT reads text in **both directions simultaneously**.

---

# 🧠 Why BERT?

Consider the sentence:

```text
The bank approved the loan.
```

and

```text
The fisherman sat on the bank.
```

The word:

```text
bank
```

has different meanings.

BERT uses surrounding words from both sides to understand the correct meaning.

---

# 🎯 Main Features of BERT

✔ Bidirectional Context Understanding

✔ Based on Transformer Encoder

✔ Contextual Embeddings

✔ Pre-trained on Massive Text Corpora

✔ Fine-tunable for Multiple NLP Tasks

---

# 🏗️ BERT Architecture

BERT uses only the **Transformer Encoder Stack**.

```text
Input Sentence
       ↓
Tokenization
       ↓
Input Embeddings
       ↓
Positional Embeddings
       ↓
Transformer Encoder Layers
       ↓
Contextual Representations
       ↓
Task-Specific Output
```

---

# ⚙️ Input Representation

BERT input consists of three embeddings:

### 1. Token Embeddings

Represent words/tokens.

Example:

```text
I love AI
```

↓

```text
[I] [love] [AI]
```

---

### 2. Positional Embeddings

Provide word order information.

Example:

```text
Position 0 → I
Position 1 → love
Position 2 → AI
```

---

### 3. Segment Embeddings

Used when two sentences are provided.

Example:

```text
Sentence A
Sentence B
```

Helps BERT distinguish between them.

---

# Special Tokens in BERT

### [CLS]

Placed at the beginning of every sequence.

```text
[CLS] I love AI
```

Used for:

* Classification Tasks
* Sentiment Analysis

---

### [SEP]

Used to separate sentences.

Example:

```text
[CLS] What is AI? [SEP] AI is Artificial Intelligence. [SEP]
```

---

### [MASK]

Used during pre-training.

Example:

```text
I love [MASK].
```

BERT predicts the missing word.

---

# 🔄 Pre-Training Tasks in BERT

BERT is trained using two objectives.

---

## 1️⃣ Masked Language Modeling (MLM)

Random words are masked.

Example:

```text
I love [MASK].
```

Prediction:

```text
AI
```

This helps BERT learn bidirectional context.

---

## 2️⃣ Next Sentence Prediction (NSP)

BERT learns sentence relationships.

Example:

Sentence A:

```text
I am studying machine learning.
```

Sentence B:

```text
Transformers are powerful models.
```

BERT predicts whether Sentence B logically follows Sentence A.

---

# 📊 BERT Configurations

There are two popular configurations.

---

## BERT Base

| Parameter               | Value       |
| ----------------------- | ----------- |
| Layers (Encoder Blocks) | 12          |
| Hidden Size             | 768         |
| Attention Heads         | 12          |
| Parameters              | 110 Million |

---

## BERT Large

| Parameter               | Value       |
| ----------------------- | ----------- |
| Layers (Encoder Blocks) | 24          |
| Hidden Size             | 1024        |
| Attention Heads         | 16          |
| Parameters              | 340 Million |

---

# ⚙️ BERT Configuration Parameters

### Hidden Size

Dimension of token embeddings.

```text
BERT Base → 768
BERT Large → 1024
```

---

### Number of Layers

Number of encoder blocks.

```text
BERT Base → 12
BERT Large → 24
```

---

### Attention Heads

Number of parallel attention mechanisms.

```text
BERT Base → 12 Heads
BERT Large → 16 Heads
```

---

### Maximum Sequence Length

Maximum input tokens.

```text
512 Tokens
```

---

### Vocabulary Size

Number of supported tokens.

```text
30,522 Tokens
```

---

# 📊 BERT Architecture Diagram

```text
Input Text
      ↓
Tokenization
      ↓
Token + Position + Segment Embeddings
      ↓
Encoder Layer 1
      ↓
Encoder Layer 2
      ↓
...
      ↓
Encoder Layer N
      ↓
Contextual Embeddings
      ↓
Task Output
```

---

# 🌍 Applications of BERT

### Sentiment Analysis

```text
Positive
Negative
Neutral
```

---

### Question Answering

Finding answers from passages.

---

### Named Entity Recognition

Example:

```text
Elon Musk → Person
Tesla → Organization
```

---

### Search Engines

Semantic Search

---

### Text Classification

Spam Detection

Topic Classification

---

# 🚀 Variants of BERT

### RoBERTa

Improved BERT with better training.

---

### DistilBERT

Smaller and faster version of BERT.

---

### ALBERT

Parameter-efficient BERT.

---

### ELECTRA

More efficient pre-training approach.

---

# ✅ Advantages

✔ Deep bidirectional understanding

✔ Strong contextual embeddings

✔ Transfer learning capability

✔ Excellent NLP performance

✔ Easy fine-tuning

---

# ❌ Limitations

❌ Large model size

❌ High computational requirements

❌ Slow inference compared to smaller models

❌ Limited maximum sequence length

---

# 📚 Summary

BERT is one of the most influential NLP models and forms the foundation of many modern language understanding systems.

👉 Key Takeaway:

**"Read context from both directions to understand language better."**

### BERT Pipeline

```text
Input Text
     ↓
Tokenization
     ↓
Embeddings
     ↓
Transformer Encoders
     ↓
Contextual Representations
     ↓
Task-Specific Prediction
```

BERT introduced the concept of deep bidirectional contextual understanding and paved the way for modern NLP models such as **RoBERTa, ALBERT, DistilBERT, ELECTRA, and many others**.

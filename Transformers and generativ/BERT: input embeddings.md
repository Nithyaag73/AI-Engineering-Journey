# 🔤 BERT Input Embeddings

**Last Updated:** 2026

Before BERT can understand text, it must convert words into numerical representations called **Input Embeddings**.

BERT does not use only word embeddings. Instead, it combines **three different embeddings** to create the final input representation.

👉 Key Idea:

**"Token Embedding + Segment Embedding + Position Embedding = BERT Input Embedding"**

---

# 📌 What are BERT Input Embeddings?

Input embeddings are the numerical vectors fed into the Transformer Encoder.

BERT combines three types of embeddings:

1. Token Embeddings
2. Segment Embeddings
3. Position Embeddings

The final embedding is obtained by adding all three.

---

# 🏗️ BERT Input Representation

```text
Input Embedding
      =
Token Embedding
      +
Segment Embedding
      +
Position Embedding
```

---

# 📊 Formula

InputEmbedding=TokenEmbedding+SegmentEmbedding+PositionEmbedding

---

# ⚙️ Step 1: Token Embeddings

Token embeddings represent the meaning of individual tokens.

Example Sentence:

```text
I love AI
```

After tokenization:

```text
[CLS] I love AI [SEP]
```

Each token gets a vector.

Example:

| Token | Embedding |
| ----- | --------- |
| [CLS] | Vector    |
| I     | Vector    |
| love  | Vector    |
| AI    | Vector    |
| [SEP] | Vector    |

---

## WordPiece Tokenization

BERT uses WordPiece Tokenizer.

Example:

```text
unhappiness
```

↓

```text
un
##happy
##ness
```

This helps BERT handle unknown words efficiently.

---

# ⚙️ Step 2: Segment Embeddings

Segment embeddings help BERT distinguish between multiple sentences.

---

## Single Sentence Example

```text
[CLS] I love AI [SEP]
```

All tokens belong to Sentence A.

| Token | Segment ID |
| ----- | ---------- |
| [CLS] | 0          |
| I     | 0          |
| love  | 0          |
| AI    | 0          |
| [SEP] | 0          |

---

## Two Sentence Example

```text
[CLS] What is AI? [SEP]
AI is Artificial Intelligence. [SEP]
```

Segment IDs:

| Token        | Segment |
| ------------ | ------- |
| [CLS]        | A (0)   |
| What         | A (0)   |
| is           | A (0)   |
| AI           | A (0)   |
| [SEP]        | A (0)   |
| AI           | B (1)   |
| is           | B (1)   |
| Artificial   | B (1)   |
| Intelligence | B (1)   |
| [SEP]        | B (1)   |

---

# ⚙️ Step 3: Position Embeddings

Transformers process all tokens simultaneously.

Therefore, word order must be provided manually.

---

Example:

```text
I love AI
```

and

```text
AI love I
```

contain the same words but different meanings.

Position embeddings solve this problem.

---

## Position IDs

| Token | Position |
| ----- | -------- |
| [CLS] | 0        |
| I     | 1        |
| love  | 2        |
| AI    | 3        |
| [SEP] | 4        |

Each position receives its own embedding vector.

---

# 🏗️ Complete Example

Sentence:

```text
I love AI
```

BERT Input:

```text
[CLS] I love AI [SEP]
```

---

### Token Embeddings

```text
[CLS] → E1
I     → E2
love  → E3
AI    → E4
[SEP] → E5
```

---

### Segment Embeddings

```text
All Tokens → Segment A
```

---

### Position Embeddings

```text
0 1 2 3 4
```

---

### Final Embedding

```text
Final Vector
=
Token
+
Segment
+
Position
```

for every token.

---

# 📊 Visualization

```text
Token Embedding
       +
Segment Embedding
       +
Position Embedding
       ↓
Final Input Embedding
       ↓
Transformer Encoder
```

---

# 🎯 Special Tokens in BERT

---

## [CLS] Token

Placed at beginning.

```text
[CLS] I love AI [SEP]
```

Purpose:

* Classification
* Sentiment Analysis
* Text Classification

---

## [SEP] Token

Used to separate sentences.

Example:

```text
[CLS] Sentence A [SEP] Sentence B [SEP]
```

Purpose:

* Sentence Pair Tasks
* Question Answering
* NSP (Next Sentence Prediction)

---

## [MASK] Token

Used during pre-training.

Example:

```text
I love [MASK]
```

BERT predicts missing word.

---

# 📐 Embedding Dimensions

For BERT Base:

| Component          | Dimension |
| ------------------ | --------- |
| Token Embedding    | 768       |
| Segment Embedding  | 768       |
| Position Embedding | 768       |

Final:

```text
768-Dimensional Vector
```

---

# 🌍 Why Input Embeddings Matter?

Without embeddings:

```text
Text
```

cannot be processed by neural networks.

Embeddings provide:

✔ Numerical representation

✔ Word meaning

✔ Sentence structure

✔ Position information

---

# 🚀 Advantages

✔ Captures word meaning

✔ Preserves sentence order

✔ Supports sentence-pair tasks

✔ Improves contextual understanding

---

# ❌ Limitations

❌ Large memory requirement

❌ Fixed maximum sequence length

❌ Computationally expensive

---

# 📚 Summary

BERT Input Embeddings are created by combining:

```text
Token Embedding
+
Segment Embedding
+
Position Embedding
```

This combined representation is then passed into Transformer Encoder layers.

👉 Key Takeaway:

**"BERT understands not only what a word is, but also where it appears and which sentence it belongs to."**

### Complete Flow

```text
Raw Text
    ↓
Tokenization
    ↓
Token Embeddings
    ↓
Segment Embeddings
    ↓
Position Embeddings
    ↓
Addition
    ↓
Final Input Embedding
    ↓
Transformer Encoder
```

Input embeddings are the foundation of BERT's powerful contextual understanding and enable it to excel in tasks such as **classification, question answering, NER, semantic search, and sentiment analysis**.

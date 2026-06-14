# 🎭 Masked Language Modeling (MLM) in BERT

**Last Updated:** 2026

Masked Language Modeling (MLM) is one of the two pre-training tasks used in **BERT (Bidirectional Encoder Representations from Transformers)**.

📄 **Paper:** *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding*

👉 Key Idea:

**"Hide some words in a sentence and train the model to predict them using surrounding context."**

MLM enables BERT to learn deep bidirectional language representations.

---

# 📌 What is Masked Language Modeling?

Masked Language Modeling is a self-supervised learning task where:

* Some words are randomly hidden
* The model predicts the missing words
* Learning happens using context from both directions

---

### Example

Original Sentence:

```text
I love machine learning.
```

After Masking:

```text
I love [MASK] learning.
```

Target:

```text
machine
```

The model learns to predict:

```text
[MASK] → machine
```

---

# 🎯 Why MLM?

Traditional language models predict words in only one direction.

Example:

```text
The cat sat on the _____
```

Prediction uses only previous words.

---

### Problem

Cannot fully understand context.

Example:

```text
The bank approved the loan.
```

vs

```text
The fisherman sat on the bank.
```

The meaning of:

```text
bank
```

depends on both left and right context.

---

### MLM Solution

BERT reads:

```text
Left Context
+
Right Context
```

simultaneously.

This creates powerful contextual embeddings.

---

# ⚙️ How MLM Works

---

## Step 1: Input Sentence

```text
The cat sat on the mat.
```

---

## Step 2: Random Masking

Some tokens are replaced.

```text
The cat [MASK] on the mat.
```

---

## Step 3: Pass Through BERT

The masked sentence is processed through Transformer Encoders.

```text
Input
 ↓
BERT Encoder
 ↓
Contextual Representation
```

---

## Step 4: Predict Missing Token

Output:

```text
[MASK] → sat
```

---

## Step 5: Calculate Loss

Compare prediction with actual word.

Loss is minimized through training.

---

# 🎲 BERT Masking Strategy

BERT does not always replace tokens with `[MASK]`.

For selected tokens:

| Action                   | Probability |
| ------------------------ | ----------- |
| Replace with `[MASK]`    | 80%         |
| Replace with Random Word | 10%         |
| Keep Original Word       | 10%         |

---

### Example

Original:

```text
I love machine learning.
```

---

80% Case

```text
I love [MASK] learning.
```

---

10% Random Word

```text
I love football learning.
```

---

10% Unchanged

```text
I love machine learning.
```

This prevents over-reliance on the `[MASK]` token.

---

# 🧠 Bidirectional Learning

Traditional models:

```text
Left → Right
```

or

```text
Right → Left
```

---

BERT MLM:

```text
Left Context
      +
Right Context
```

Example:

```text
The dog chased the [MASK].
```

BERT can use:

```text
The dog chased the
```

and

```text
.
```

to infer:

```text
cat
```

---

# 🏗️ MLM Architecture

```text
Input Sentence
      ↓
Random Masking
      ↓
Token Embeddings
      ↓
Transformer Encoders
      ↓
Contextual Embeddings
      ↓
Softmax Layer
      ↓
Masked Word Prediction
```

---

# 📐 Prediction Formula

For a masked token:

```text
Context → Hidden Representation → Vocabulary Probabilities
```

Probability of a token:

P(word)=\frac{e^{z_i}}{\sum_j e^{z_j}}

where:

* (z_i) = score of token i
* Softmax converts scores into probabilities

---

# 💻 Example

Sentence:

```text
Paris is the capital of [MASK].
```

Model Output:

| Token   | Probability |
| ------- | ----------- |
| France  | 0.93        |
| Germany | 0.03        |
| Italy   | 0.02        |
| Spain   | 0.02        |

Prediction:

```text
France
```

---

# 🔄 MLM vs Traditional Language Modeling

| Feature           | Traditional LM                   | MLM           |
| ----------------- | -------------------------------- | ------------- |
| Context Direction | One-way                          | Bidirectional |
| Uses Future Words | No                               | Yes           |
| Understanding     | Limited                          | Better        |
| Example Model     | GPT (training objective differs) | BERT          |

---

# 🌍 Applications

MLM pre-training improves:

### Sentiment Analysis

```text
Positive
Negative
Neutral
```

---

### Question Answering

Understanding question context.

---

### Named Entity Recognition

Person, Location, Organization detection.

---

### Semantic Search

Understanding meaning rather than keywords.

---

### Text Classification

Spam detection, topic classification.

---

# 🚀 Advantages

✔ Learns bidirectional context

✔ Produces contextual embeddings

✔ Strong language understanding

✔ Improves downstream NLP tasks

✔ State-of-the-art performance

---

# ❌ Limitations

❌ `[MASK]` token never appears during inference

❌ Computationally expensive

❌ Requires large datasets

❌ Large training cost

---

# 📚 MLM vs NSP

BERT uses two pre-training tasks:

| Task                           | Purpose                      |
| ------------------------------ | ---------------------------- |
| Masked Language Modeling (MLM) | Learn word-level context     |
| Next Sentence Prediction (NSP) | Learn sentence relationships |

Together they help BERT understand language deeply.

---

# 📚 Summary

Masked Language Modeling (MLM) is the core training objective that allows BERT to learn contextual representations.

👉 Key Takeaway:

**"Hide words → Predict them using both left and right context."**

### MLM Pipeline

```text
Sentence
   ↓
Random Masking
   ↓
BERT Encoder
   ↓
Contextual Representation
   ↓
Softmax
   ↓
Predict Missing Word
```

MLM is one of the main reasons BERT achieved breakthrough performance in NLP tasks such as **question answering, sentiment analysis, semantic search, NER, and text classification**.

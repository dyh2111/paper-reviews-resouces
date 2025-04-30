# RAG: Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks

**Paper Link:**  
*https://arxiv.org/abs/2005.11401*

**Paper Notes by Dan Harvey**  
dyh2111@columbia.edu

---

## TL;DR
Retrieval-Augmented Generation (RAG) improves language models by injecting updated, external information into prompts, enabling more robust and accurate outputs. This helps overcome the limitation of LLMs being constrained to knowledge present only at the time of their training.

---

## Key Concepts

- **LLMs are static** — they cannot update their internal world knowledge after training.
- **RAG is model-agnostic** — it sits on top of an LLM and augments its input using retrieved information.
- Introduces two types of memory:
  - **Parametric Memory:** The model's learned internal weights.
  - **Non-Parametric Memory:** External knowledge retrieved at runtime.

---

## Model Overview

1. **Input:** Original question or query.
2. **Retrieval:** Encodes the query using a non-parametric retriever to return top-k relevant documents.
3. **Generation:** Feeds the query and retrieved documents into a parametric generator (like an LLM).
4. **Output:** The LLM produces an answer based on both query and retrieved context.

> In the original RAG paper, **Wikipedia** was used as the source for non-parametric memory.

---

## Two RAG Variants

### 1. **RAG-Sequence**
- Generates an entire output sequence conditioned on each document.
- The model computes output sequence probabilities for each document, which are then **marginalized**.
- **Per-Sequence Augmentation**

### 2. **RAG-Token**
- For each output token, it draws from several latent documents.
- It produces a token-level distribution for each document, then marginalizes across them.
- **Per-Token Augmentation**

---

## Additional Notes

- RAG uses **Maximum Inner Product Search (MIPS)** for retrieval.
- The **number of retrieved documents** is a tunable **hyperparameter**.

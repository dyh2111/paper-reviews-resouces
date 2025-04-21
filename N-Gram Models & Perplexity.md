# Notes on N-Gram Models and Perplexity

## Reference
https://web.stanford.edu/~jurafsky/slp3/3.pdf

## Overview
N-Gram models are statistical language models that assign probability to the likelihood of the next word or character in a sequence based on the previous n-1 tokens.

## Core Concepts

### Probabilistic Foundation
- Built on Bayesian probability theory
- Uses prior occurrences to predict future tokens
- Incorporates Markov assumption: the probability of a token depends only on a fixed number of preceding tokens rather than the entire history

### Types of N-Gram Models
- **Unigram**: Probability based on single tokens with no context (n=1)
- **Bigram**: Probability conditioned on the previous word (n=2)
- **Trigram**: Probability conditioned on the previous two words (n=3)
- Higher-order n-grams use more context words

### Probability Calculation
- Uses Maximum Likelihood Estimation (MLE)
- Calculated as joint probability of sequences
- Typically computed in log space to prevent numerical underflow from repeated multiplications
- Specific to the training corpus

<img width="986" alt="image" src="https://github.com/user-attachments/assets/07840040-ed92-4af6-8ebb-0e88bfec803e" />


## Evaluation: Perplexity

### Definition
Perplexity is the standard evaluation metric for n-gram models, defined as the inverse probability of the test set, normalized by the number of tokens.

### Formula
Perplexity = 2^(-l)
- Where l is the average log likelihood per token

### Interpretation
- **Lower perplexity** indicates a better model
- Higher probability word sequences result in lower perplexity scores
- Perplexity is influenced by corpus size and domain

### Important Note
Perplexity measurements can only be compared for models evaluated on the same test set, as they are sensitive to vocabulary size and text domain.

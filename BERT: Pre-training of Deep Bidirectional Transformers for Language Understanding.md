# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

## Authors
Jacob Devlin, Ming-Wei Chang, Kenton Lee, Kristina Toutanova

## Paper Reference
https://arxiv.org/abs/1810.04805

## Overview
BERT (Bidirectional Encoder Representations from Transformers) is an innovative language representation model designed to pre-train deep bidirectional representations by jointly conditioning on both left and right context in all layers. This bidirectional approach differentiates BERT from previous models, enabling state-of-the-art performance across various NLP tasks with minimal task-specific architecture modifications.

## Key Achievements
- Established new state-of-the-art results on eleven NLP tasks
- Improved GLUE score to 80.5% (7.7% absolute improvement)
- Enhanced MultiNLI accuracy to 86.7% (4.6% absolute improvement)
- Advanced SQuAD v1.1 question answering Test F1 to 93.2 (1.5 point improvement)
- Raised SQuAD v2.0 Test F1 to 83.1 (5.1 point improvement)

## Model Architecture
- BERT focuses on input representation rather than model architecture
- Based on Vaswani's vanilla transformer design
- Two variants:
  - Base model: 110M parameters
  - Large model: 330M parameters
- Surpassed OpenAI's GPT model (which was SOTA at the time)

## Key Innovations
1. **Bidirectional Contextuality**: Allows attention to tokens both from left-to-right and right-to-left for better contextual understanding
2. **Two-Phase Approach**:
   - Pre-training on unlabeled data
   - Fine-tuning on labeled, task-specific data

## Input Processing
- **Tokenization**: Sentences processed with WordPiece tokenizer
- **Sequence Structure**:
  - Begins with [CLS] token (classification token)
  - Sentences separated by [SEP] token
  - Learned embeddings indicate sentence connection
- **Embedding Components**:
  - Token embeddings (from WordPiece)
  - Segment embeddings (marking sentence A/B)
  - Position embeddings (indicating token position)

## Masking Technique
- 15% of tokens are masked during training to prevent "data leakage" in bidirectional context
- Masking variations:
  - Replace with [MASK] token
  - Replace with random token
  - Leave unchanged (but still predict)
- This approach is called "Masked Language Modeling" (MLM)

## Training Process
1. **Pre-training Tasks**:
   - Masked Language Modeling (MLM): Predict masked tokens
   - Next Sentence Prediction (NSP): Determine if two sentences follow each other
2. **Fine-tuning**:
   - Initialize with pre-trained weights
   - Train on labeled question-answer pairs or other task-specific data
   - Requires minimal architectural changes (typically just one output layer)
     
<img width="1417" alt="image" src="https://github.com/user-attachments/assets/cfbe10d7-65f4-4ab1-ad66-f7987a9f23bd" />

## Input Example
For input: "[CLS] my dog is cute. [SEP] he likes playing [SEP]"

- **Token Embeddings**: E_CLS, E_my, E_dog, E_is, E_cute, E_., E_SEP, E_he, E_likes, E_playing, E_SEP
- **Segment Embeddings**: E_A, E_A, E_A, E_A, E_A, E_A, E_A, E_B, E_B, E_B, E_B
- **Position Embeddings**: E_0, E_1, E_2, E_3, E_4, E_5, E_6, E_7, E_8, E_9, E_10

The final input representation combines these three embedding types for each token.

<img width="1338" alt="image" src="https://github.com/user-attachments/assets/470ce2fa-bea1-4acb-a13a-4336de0eb394" />

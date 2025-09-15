# BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

## Authors
Jacob Devlin, Ming-Wei Chang, Kenton Lee, Kristina Toutanova

## Paper Reference
https://arxiv.org/abs/1810.04805

## Overview
BERT (Bidirectional Encoder Representations from Transformers) is built on top of the Transformer architecture.  
The original Transformer (Attention Is All You Need, 2017) uses an encoder–decoder structure for sequence-to-sequence tasks.  
In contrast, BERT keeps **only the encoder** and introduces a bidirectional pretraining objective.  

BERT takes input tokens that are represented as the sum of:
- **Token embeddings** (WordPiece vocabulary)  
- **Segment embeddings** (whether the token belongs to sentence A or B)  
- **Position embeddings** (index of the token in the sequence)  

This combined embedding is fed into the Transformer encoder stack.  
During pretraining, a softmax classification layer is added on top of the hidden states to perform:
- **Masked Language Modeling (MLM):** predict randomly masked tokens.  
- **Next Sentence Prediction (NSP):** classify if sentence B follows sentence A.  

For downstream tasks, the pretraining heads are replaced with task-specific output layers (e.g., classification, tagging, QA).  
The encoder weights can be fine-tuned end-to-end, or partially frozen depending on the use case.  


## Key Differences Between BERT and GPT
- **Architecture**  
  - GPT uses the Transformer **decoder only**.  
  - BERT uses the Transformer **encoder only**.  

- **Training Objective / Directionality**  
  - GPT is **unidirectional**, trained with left-to-right language modeling.  
  - BERT is **bidirectional**, trained with masking so tokens attend to both left and right context.  


### Fine-Tuning for Tasks
- In downstream tasks, the pretraining heads are replaced with a **task-specific classifier head**.  
- The pretrained encoder layers are typically fine-tuned (sometimes partially frozen) to adapt to the new task.  


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

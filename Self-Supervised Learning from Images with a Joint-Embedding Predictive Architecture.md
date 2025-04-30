Self-Supervised Learning from Images with a Joint-Embedding Predictive Architecture

📄 Paper Link

TL;DR

I-JEPA is a self-supervised framework for learning visual representations by predicting features of masked image regions. It enables models to understand global context and reconstruct small parts of images without labels.

Key Points

I-JEPA stands for Joint-Embedding Predictive Architecture.
It's a self-supervised learning approach—no labels are needed.
Unlike other methods that require heavy data augmentation and enforce invariance, I-JEPA avoids these by learning a predictive representation.
The model predicts embeddings (not pixels) of masked regions, which improves semantic understanding and training efficiency.
Inspired by cognitive learning theory, which suggests humans learn by building global models from partial observations.
It outputs compatible image representations for downstream processing blocks.
The method is especially effective for masked prediction tasks on images.

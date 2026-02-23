This is our project for LLM Course @Master IASD 2025
## Introduction
Modern language models have grown enormously, often reaching hundreds of billions of pa
rameters. While full fine-tuning can adapt these models to specific tasks, it quickly becomes
impractical: each task requires storing a full model copy, training demands massive memory for
optimizer states, and deployment is cumbersome without specialized hardware.
## LoRA: Low-Rank Adaptation
LoRA [1] addresses these challenges by freezing the pre-trained weights and learning only
small, trainable low-rank matrices injected into each layer. This approach drastically reduces
the number of trainable parameters (up to 10,000× fewer) while preserving or even improving
performance, enabling efficient adaptation of massive models on standard hardware. By focus
ing on a low-dimensional subspace of task-specific knowledge, LoRA combines both memory
efficiency and ease of deployment without altering the model’s forward pass.
## Implementation
Since the LoRA paper proposes an efficient fine-tuning approach, we conducted a case study
applying this technique to a practical task and comparing it with other parameter-efficient fine
tuning methods. Our experimental setup consists of: BERT [3] as the pre-trained model,
fine-tuned for emotion detection (6-class sequence classification) using the dair-ai/emotion1
HuggingFace dataset. We implemented as a baseline for comparison a full fine-tuned model.
Comparisons were performed during training (loss, accuracy, number of trainable parameters)
and inference (test accuracy, F1-score, inference latency). Our models were trained using Hug gingFace Trainer API with evaluation at each epoch. Training was conducted on Google Colab
with T4 GPU.

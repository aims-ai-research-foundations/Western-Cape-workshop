# Day 4: Course Lab

**Course 5 · Fine-tune Your Model**
**Lab:** Fine-tune Gemma 3 1B into an isiXhosa maternal health assistant

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/aims-ai-research-foundations/Western-Cape-workshop/blob/main/course-labs/day4/day4-course5-practical.ipynb)

## About

Fine-tune **Gemma 3 1B** with **LoRA** on [MaternalCare ZA](https://huggingface.co/datasets/Similoluwa/maternalcare-za), a synthetic, isiXhosa-first maternal health dataset ([data card](DATA_CARD.md)), so it can work as a maternal health assistant for isiXhosa-speaking mothers in South African townships.

## Objectives

By the end of this lab you will be able to:

1. Check whether a fine-tuning dataset is good enough to use.
2. Format conversations for Gemma 3, and calculate the loss only on the assistant's replies.
3. Fine-tune Gemma 3 1B with LoRA on a free Colab GPU, and read its loss curves.
4. Explain what LoRA rank, learning rate and batch size do.
5. Compare a fine-tuned model with the original.
6. Share your model on Hugging Face.

## Before you start

- **Save your own copy first:** File → Save a copy in Drive.
- Switch on a **T4 GPU:** Runtime → Change runtime type.
- Create a Hugging Face **write** token and save it in Colab Secrets as `HF_TOKEN`.
- Accept the terms on the [Gemma 3 1B model page](https://huggingface.co/google/gemma-3-1b-it).

> ⚠️ **For learning only.** The dataset is synthetic and has not yet been reviewed by isiXhosa speakers or clinicians.

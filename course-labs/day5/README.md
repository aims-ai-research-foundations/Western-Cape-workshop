# Day 5: Course Lab

**Course 7 · Accelerate Your Model**
**Lab:** Fine-tune Gemma 3 1B, then make it fit on a 4 GB GPU

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/aims-ai-research-foundations/Western-Cape-workshop/blob/main/course-labs/day5/day5-course7-practical.ipynb)

## About

We want to fine-tune **Gemma 3 1B** for our own task, such as the maternal health assistant from the [Day 4 lab](../day4/), then deploy it on a device with a **4 GB GPU**. Will it fit? You estimate and measure the GPU memory for training and inference, and use LoRA and quantization to make it fit.

## Objectives

By the end of this lab you will be able to:

1. Estimate the GPU memory needed to fine-tune a model, fully and with LoRA.
2. Explain how the batch size changes the memory needed for training.
3. Estimate the memory a model needs to answer a question, and compare it with a measurement.
4. Quantize a model with bitsandbytes, and measure what it saves and what it costs.
5. Make a model fit on a 4 GB GPU.

## Before you start

- **Save your own copy first:** File → Save a copy in Drive.
- Switch on a **T4 GPU:** Runtime → Change runtime type.
- Save a Hugging Face token in Colab Secrets as `HF_TOKEN`. The one from the Day 4 lab works; otherwise a **read** token is enough.
- Accept the terms on the [Gemma 3 1B model page](https://huggingface.co/google/gemma-3-1b-it).

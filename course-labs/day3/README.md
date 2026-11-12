# Day 3 — Course Lab

**Course 4 · Discover the Transformer Architecture**
**Lab:** A Transformer in 60 Minutes — *The story of one sentence: "Jide cooked iyan with peppers"*
*(Western Cape Workshop copy; content Colab-verified 2026-08-11)*

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/aims-ai-research-foundations/Western-Cape-workshop/blob/main/course-labs/day3/day3-course4-student.ipynb)

## About

Trace one short Yoruba-English sentence through a full attention layer, by hand
and in code. Starting from 4-D token embeddings you build Q, K, V projections,
compute scaled dot-product attention scores, apply a numerically stable softmax,
and measure how each token shifts after attention. Then you add causal masking
so a token cannot see the future, and finally spin up a second attention head
with different projections and compare what the two heads pay attention to.
The notebook extends the in-session "Jide ate iyan" hand-computation to a
5-token sentence, with real heatmaps and one full multi-head layer. About 60
minutes; no GPU needed.

## How to work through it

- Click **Open in Colab** above to launch the notebook.
- **Before running or editing anything, save your own copy: File → Save a copy
  in Drive.** The badge opens the notebook in read-only playground mode;
  without your own copy, all your work is lost when the tab closes.
- Follow the **Predict → Run → Explain** protocol for every code cell: predict
  what will happen (shapes, numbers), run it, then explain any surprises.
- Seven TODO cells guide you through the layer end-to-end. The final TODO is
  the one that matters most: explain attention in plain language, without
  using the words Query, Key, or Value.

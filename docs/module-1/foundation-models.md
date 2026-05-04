# Foundation Models

!!! note "Attribution"
    This lesson is inspired by and heavily references the Coursera course [*Generative AI for Leaders*](https://www.coursera.org/learn/generative-ai-genai), taught by Dr. Ian McCulloh. Examples, framing, and pedagogical structure draw substantially from his instruction.

!!! abstract "Module 1 · Lesson 1"
    **What are foundation models, how are they trained, and why do they power almost all modern generative AI?**

## What Is a Foundation Model?

A foundation model is an AI system trained on an enormous, diverse dataset — text, images, audio, sensor data, 3D models, time series — that develops broad, generalizable understanding. From this shared "foundation," the model can then be applied to many specific tasks through prompting or fine-tuning.

| Input Modalities | Example Downstream Tasks |
|------------------|--------------------------|
| Text | Q&A, summarization, translation |
| Images | Object recognition, captioning, visual Q&A |
| Audio | Speech recognition, transcription |
| Time series, sensor data | Forecasting, anomaly detection |
| **Multimodal combinations** | **Any prompted task across modalities** |

**Made possible by:** Cloud computing infrastructure that can ingest and process massive training datasets, along with specialized accelerators (GPUs/TPUs) for parallel computation.

**Scale:** Modern LLMs are trained on datasets in the hundreds of gigabytes to multiple terabytes after filtering (GPT-3, for example, was trained on roughly 570GB of filtered text drawn from a larger ~45TB corpus). Training and serving these models consumes substantial electricity — enough that frontier AI labs are now signing power agreements measured in hundreds of megawatts to gigawatts, comparable to small cities.

---

## The Transformer: The Key Breakthrough

In 2017, Google published [*Attention Is All You Need*](https://arxiv.org/abs/1706.03762) (Vaswani et al.), introducing the **transformer** architecture. The core idea: instead of processing words sequentially, transformers use **self-attention** to weigh the importance of every word relative to every other word — all in parallel during training.

### How Attention Works

Consider: *"The cat sat on the mat."* The word "sat" relates most strongly to "cat" — not to "the" or "on." Attention mechanisms capture these relationships, allowing the model to understand context.

For the word **"ball"**, the surrounding words determine meaning:

- *"The dog chased after the ball as it rolled down the hill"* → spherical object (context: dog, rolled)
- *"Cinderella went to the ball in a fancy glass coach"* → formal event (context: Cinderella, coach)

!!! tip "ALS Research Connection"
    This is why Claude can distinguish "ALS" meaning amyotrophic lateral sclerosis versus "ALS" as another acronym — the model has learned contextual representations during training, so surrounding text resolves the ambiguity automatically.

### Computational Advantages of Attention

- **Parallel training** — during training, all positions in a sequence are processed simultaneously rather than one at a time (note: text *generation* at inference is still token-by-token, since each new token depends on the previous ones)
- **Adaptive weighting** — high-information words (cat, sat, mat) are weighted more heavily than low-information words (the, on)
- **Flexible context** — input and output length can scale, though standard self-attention has O(n²) cost in sequence length, which is why long-context models rely on optimizations like FlashAttention, sparse attention, or sliding windows
- **Transfer across tasks** — the same learned representations support many downstream applications

---

## Vector Embeddings

Words and phrases are converted into **vectors** — lists of numbers that represent meaning in a multi-dimensional space. Similar concepts cluster together. "Motor neuron disease" would sit close to "ALS" and "MND" in this space.

This enables **semantic search**: finding documents about ALS progression even if the exact phrase isn't used.

### How Semantic Search Works

```
1. Embed the query     → convert your research question to a vector
2. Search vector space → find documents whose vectors are most similar
3. Return results      → contextually relevant, not just keyword-matched
```

!!! example "Traditional vs. Semantic Search"
    **Traditional search** for "Polish shoe brands" → returns results about shoe polish.

    **Semantic search** for "Polish shoe brands" → returns brands of shoes from Poland.

    The same keyword confusion can occur in biomedical search — semantic embeddings resolve it.

---

## Key Takeaways

- Foundation models are trained on massive, diverse datasets and can be adapted to many tasks
- The transformer (2017) enabled parallel, context-aware processing — the backbone of all modern LLMs
- Vector embeddings allow semantic similarity search, far outperforming keyword matching
- Energy and compute costs are real considerations for AI infrastructure planning

---

[Next: Large Language Models →](large-language-models.md)

# Foundation Models

!!! abstract "Module 1 · Lesson 1"
    **What are foundation models, how are they trained, and why do they power almost all modern generative AI?**

## What Is a Foundation Model?

A foundation model is an AI system trained on an enormous, diverse dataset — text, images, audio, sensor data, 3D models, time series — that develops broad, generalizable understanding. From this shared "foundation," the model can then be applied to many specific tasks through prompting or fine-tuning.

| Inputs | Downstream Tasks |
|--------|-----------------|
| Text, images, audio | Q&A, summarization |
| Relational data, sensors | Object recognition, captioning |
| 3D models, time series | Speech recognition |
| **All of the above** | **Any prompted task** |

**Made possible by:** Cloud computing infrastructure that can ingest and process massive training datasets.

**Scale:** ChatGPT's training data runs to terabytes; its data center uses more power than Orange County, Florida (home to Disney World, Universal, and hundreds of thousands of residents).

---

## The Transformer: The Key Breakthrough

In 2017, Google published *Attention Is All You Need*, introducing the **transformer** architecture. The core idea: instead of processing words sequentially, transformers use **self-attention** to weigh the importance of every word relative to every other word — all in parallel.

### How Attention Works

Consider: *"The cat sat on the mat."* The word "sat" relates most strongly to "cat" — not to "the" or "on." Attention mechanisms capture these relationships, allowing the model to understand context.

For the word **"ball"**, the surrounding words determine meaning:

- *"The dog chased after the ball as it rolled down the hill"* → spherical object (context: dog, rolled)
- *"Cinderella went to the ball in a fancy glass coach"* → formal event (context: Cinderella, coach)

!!! tip "ALS Research Connection"
    This is why Claude can distinguish "ALS" meaning amyotrophic lateral sclerosis versus "ALS" as another acronym — context from surrounding text resolves the ambiguity automatically.

### Computational Advantages of Attention

- **Parallelization** — words are processed simultaneously, not sequentially
- **Memory efficiency** — focus on relevant words rather than entire documents
- **Adaptive weighting** — high-information words (cat, sat, mat) weighted more than low-information words (the, on)
- **Scalable context** — input and output length can scale flexibly

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

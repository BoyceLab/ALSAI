# Fine-Tuning Large Language Models

!!! abstract "Module 2 · Lesson 4"
    **How to adapt open-source models to your specific research domain — and the 11 steps to do it properly.**

## Why Fine-Tune?

General-purpose LLMs like ChatGPT are excellent but may lack deep knowledge of ALS-specific literature, clinical trial data, or your organization's internal documents. Fine-tuning adapts a base model to your domain — dramatically improving relevance and accuracy.

!!! tip "ALS TDI Use Case"
    Fine-tuning an open-source model (like Llama 2) on ALS research literature, ARC Study data documentation, and internal protocols could create an AI assistant that understands your specific research context — without sending proprietary data to external servers.

---

## Open-Source LLMs for Fine-Tuning

| Model | By | Best For |
|-------|----|----------|
| **Llama 2/3** | Meta | General purpose, highly customizable |
| BERT | Google | Document understanding, classification |
| RoBERTa | Meta | Robust text classification |
| T5 | Google | Text-to-text tasks, summarization |
| GPT-2 | OpenAI | Text generation, search applications |

---

## Does Fine-Tuning Actually Help?

Yes — dramatically. A 2020 paper benchmarking GPT-3 showed:

| Training | Benchmark Performance |
|----------|----------------------|
| Zero-shot (no training data) | Baseline |
| One-shot (minimal data) | Moderate improvement |
| Few-shot (more data) | Good improvement |
| **State-of-the-art fine-tuning** | **Dramatic improvement** |

---

## 11 Steps to Fine-Tune an LLM

**1. Define the task and objectives**
Is this for literature summarization? Biomarker classification? Protocol compliance checking? Be specific.

**2. Set clear performance metrics**
Accuracy, F1 score, BLEU score — choose metrics appropriate for your task before you start.

**3. Select a pre-trained model**
Llama 2/3 is recommended for most ALS research applications given its performance and open-source flexibility.

**4. Prepare the dataset**
Clean, labeled data. Use multiple annotators for labeling tasks.

**5. Ensure annotation quality**
Target **Krippendorff's alpha ≥ 0.8** for inter-annotator agreement. Inconsistent labels produce inconsistent models.

**6. Split into train / validation / test sets**
Typically 70/15/15. The test set is held out completely until final evaluation.

**7. Set up the compute environment**
GPU/TPU access required. Python with PyTorch or TensorFlow.

**8. Tokenize and preprocess data**
Break text into model-readable tokens; add attention masks. For images, annotate bounding boxes or apply masking.

**9. Initialize the model and configure training parameters**
Learning rate, batch size, number of epochs. These hyperparameters significantly affect performance.

**10. Fine-tune the model**
Train on your domain-specific dataset. Use **cross-entropy loss** for classification tasks.

**11. Evaluate performance**
Measure against your pre-defined metrics on the held-out test set. Compare to zero-shot baseline.

---

!!! warning "Proprietary vs. Open-Source"
    ChatGPT and Gemini restrict fine-tuning for good reasons (safety, compliance), but this means you cannot customize them for sensitive applications like counter-disinformation, defense, or proprietary research workflows. For those use cases, open-source models like Llama 2 are the appropriate choice.

---

[← Why LLMs Appear Smart](../module-1/why-llms-appear-smart.md) | [Next: Competence & Hallucination →](competence-hallucination.md)

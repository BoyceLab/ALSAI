# Large Language Models

!!! abstract "Module 1 · Lesson 2"
    **How ChatGPT and other LLMs actually work — and why generative search beats traditional keyword search for research.**

## LLM Landscape

| Model | Organization | Strengths | Access |
|-------|-------------|-----------|--------|
| GPT-4 / ChatGPT | OpenAI | Creative content, general reasoning | API / Proprietary |
| Gemini | Google | Multimodal, large context window | API / Proprietary |
| **Claude** | **Anthropic** | **Safety, long documents, nuanced analysis** | **API / Web** |
| Llama 2/3 | Meta | Fine-tunable, open source | Open Source |
| BERT / RoBERTa | Google / Meta | Document understanding, summarization | Open Source |
| Copilot | Microsoft | Code, Office integration | Proprietary |

---

## Generative vs. Traditional Search

Traditional search engines match keywords. Generative search understands intent.

!!! tip "ALS Literature Review"
    Searching PubMed with keywords like "SOD1 aggregation" may miss relevant papers that describe the same mechanism with different terminology. A generative/semantic search would surface those papers based on conceptual similarity.

---

## How ChatGPT Generates a Response

Given `"The cat sat on the ___ "`, the model calculates the statistically most likely next token. For longer prompts, every preceding word informs the probability distribution of what comes next.

!!! warning "Important Mental Model"
    The model isn't "thinking." It's executing a very sophisticated **next-word prediction engine** trained on massive amounts of human text. This is both its power and the source of its failure modes (hallucination).

---

## OpenAI's Three-Step Improvement Process

### Step 1 — Supervised Fine-Tuning
Human labelers demonstrate ideal responses to training prompts, teaching the model what good output looks like.

### Step 2 — Reward Model Training
Users and employees rank outputs A vs. B, creating a reward signal for what "better" looks like.

### Step 3 — Reinforcement Learning (PPO)
The model learns to maximize reward — continuously optimizing output quality toward human preferences.

!!! info "Key Insight"
    As researchers use and correct LLMs, the models improve. Correcting a factual error about a biomarker today makes the model more accurate for the next researcher who asks.

---

## Referencing and Source Verification

One significant advantage of generative search: it can tell you **where** it got its information.

When ChatGPT was asked which planet has the most moons, it:

1. Initially said Jupiter (95 moons, citing NASA)
2. When challenged with Saturn data (146 moons per a different source), it investigated
3. Clarified Saturn has 146 moons total — 83 confirmed, 63 awaiting confirmation
4. Updated its response for all subsequent queries in that session

**Lesson:** LLMs are not infallible, but their ability to cite sources and accept corrections makes them more useful than keyword search for navigating conflicting information.

---

## Key Takeaways

- Many LLMs exist — choose based on your task (Claude for documents, GPT-4 for creativity, Llama 2 for custom fine-tuning)
- Generative search understands context; keyword search does not
- LLMs predict the next most likely token — powerful, but not "intelligent" in the human sense
- Human feedback loops continuously improve model quality
- Always request citations and verify them independently

---

[← Foundation Models](foundation-models.md) | [Next: Why LLMs Appear Smart →](why-llms-appear-smart.md)

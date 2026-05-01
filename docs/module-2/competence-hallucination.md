# Competence & Hallucination

!!! abstract "Module 2 · Lesson 5"
    **Understanding AI error types — and how to minimize them in research workflows.**

## The Two Types of LLM Error

| Competence Issues | Hallucination |
|-------------------|---------------|
| Wrong answer (factual error) | Fabricated answer (invented facts) |
| Misunderstood context | Made-up citations or sources |
| Inconsistent responses | Invented people, drugs, or studies |
| Poor generalization | Plausible-sounding but entirely false details |

---

## Formal Competence

Formal competence covers the rules of language itself:

- **Phonology** — Valid word forms: `BLICK` could be English; `BNICK` violates phonological rules
- **Morphology** — Valid word combinations: "Lady Gaga-esque" works; "Lady Gaga-ness-esque" does not
- **Lexical semantics** — "I'll take my coffee with cream and sugar" ✓ | "...with cream and red" ✗
- **Syntax** — "The key to the cabinets *is* on the table" — not *are*

## Functional Competence

Functional competence covers reasoning and world knowledge:

- **Formal reasoning** — 14 birds − 3 + 1 = 12, not 11
- **World knowledge** — A trophy doesn't fit in a suitcase because the *suitcase* is too small, not the trophy
- **Situational modeling** — If Sally doesn't own a dog, "the dog is black" is incoherent
- **Theory of mind** — Understanding that different people hold different beliefs

---

## Hallucination Examples

!!! danger "Fabricated Drug"
    **Prompt:** *"What are the benefits of Panacea-X for treating diabetes?"*

    **Response:** *"Panacea-X is a breakthrough drug offering a 90% reduction in blood sugar levels with minimal side effects..."*

    Panacea-X is entirely fictional. Its efficacy, mechanism, and existence were fabricated. **This pattern can occur with real but less-prominent drugs, compounds, or trials.**

!!! danger "Fabricated Researcher"
    **Prompt:** *"What are recent discoveries by Dr. Jane Smith in quantum mechanics?"*

    **Response:** *"Dr. Jane Smith recently discovered the quantum photon, revolutionizing our understanding of entanglement..."*

    No such scientist or discovery exists. The model generated a plausible-sounding research narrative. **This can happen with real but less-prominent researchers.**

!!! danger "Fabricated Clinical Trial"
    The same pattern applies to clinical trials: asking an LLM about a specific trial may produce a confident, detailed, completely invented response if the trial isn't well-represented in training data.

---

## How to Minimize Hallucination

**1. Always request citations**
Add *"cite your sources in APA format"* to every factual prompt. This significantly reduces hallucination and lets you verify claims.

**2. Train on high-quality data**
For fine-tuned models, data quality matters more than model architecture changes. The single highest-impact improvement in practice.

**3. Use prompt engineering**
Constrain scope: *"Based only on the following abstract..."* or *"If you are uncertain, say so explicitly."*

**4. Apply post-processing checks**
Run outputs through symbolic AI or formal verification to check logical consistency.

**5. Human-in-the-loop review**
Especially for clinical, regulatory, or publication contexts — expert review remains essential.

!!! info "Humans Hallucinate Too"
    The goal isn't a perfect AI — it's a workflow where AI accelerates work and humans catch errors. Humans also make mistakes, introduce bias, and produce inconsistent outputs at scale. The question is always: compared to what alternative?

---

[← Fine-Tuning](fine-tuning.md) | [Next: LLM Vulnerabilities →](vulnerabilities.md)

# Symbolic AI Fundamentals

!!! abstract "Module 4 · Lesson 9"
    **Rule-based AI that is transparent, auditable, and explainable — a critical complement to probabilistic machine learning.**

## What Is Symbolic AI?

Symbolic AI represents knowledge through **symbols** (objects, concepts, entities) and **rules** (logical if-then statements). Unlike machine learning, which learns patterns statistically, symbolic AI uses explicitly defined logic.

| | Symbolic AI | Machine Learning |
|--|-------------|-----------------|
| Approach | Rule-based, logic-driven | Data-driven, pattern recognition |
| Programming | Explicit rules hard-coded | Statistical learning from data |
| Explainability | Fully transparent | Black box |
| Best for | Clear decision logic, compliance | Prediction, classification, creativity |
| Errors | Deterministic — no hallucination | Probabilistic — can hallucinate |
| Adapts to new data | No | Yes |

---

## Key Concepts

### Knowledge Representation

Objects like `Patient`, `Trial`, `Biomarker`, and `Adverse_Event` are defined as symbols. Rules specify how they relate:

```
IF patient.inclusion_criteria_met = TRUE
AND patient.informed_consent = TRUE
THEN enroll(patient, trial)
```

### Reasoning

The system follows logical chains:

```
IF drug_compound_inventory < reorder_threshold
AND days_until_next_visit < lead_time
THEN trigger_reorder(compound)
```

This is **deterministic** — the same input always produces the same output.

---

## A Brief History

Symbolic AI is the *original* AI:

- **1930s** — Claude Shannon demonstrated Boolean logic can represent any logical statement (foundation of binary computing)
- **1950s** — Herb Simon and Alan Newell (Carnegie Mellon, both Nobel laureates) built the **Logical Theorist**, the first AI program — a formal method system
- **1960s-70s** — Expert systems, game-playing programs, rule-based NLP
- **1980s** — Machine learning began to dominate; symbolic AI receded
- **Today** — Most powerful systems integrate both

!!! info "Natural Language Processing Uses Both"
    In NLP, symbolic AI handles grammar rules (subject-verb agreement), while machine learning handles semantics (identifying nouns and verbs in context). Together, they outperform either alone.

---

## When to Use Symbolic AI vs. Machine Learning

| Use Symbolic AI When... | Use Machine Learning When... |
|------------------------|------------------------------|
| Decision must be auditable | Outcome needs prediction |
| Regulation requires explainability | Data is unstructured (text, images) |
| Rules are well-defined | Patterns are too complex to define explicitly |
| Consistency is critical | Environment is changing rapidly |
| You need to prove correctness | You need to generalize to new situations |

---

[← Autoencoders & Diffusion](../module-3/autoencoders-diffusion.md) | [Next: Business Applications →](applications.md)

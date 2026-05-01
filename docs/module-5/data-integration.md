# Data Integration at Scale

!!! abstract "Module 5 · Lesson 17"
    **Why data integration is the most expensive AI bottleneck — and how symbolic generative AI can cut costs by up to 90%.**

## The Problem

In virtually every AI project, the most time-consuming and costly step is integrating data from multiple sources built for different purposes:

- **Manual and subjective** — Engineers make ad hoc decisions without deep domain knowledge
- **Opaque** — Nobody knows why certain decisions were made or how to untangle them
- **Error-prone** — Heavy reliance on tacit knowledge; mistakes propagate silently
- **Costly** — Often the dominant labor expense in any AI or data modernization effort

!!! danger "ALS Research Reality"
    Integrating data from the ARC Study, multiple clinical sites, biomarker labs, and wearable sensors involves exactly these challenges. Different sites encode disease progression differently. Units differ. Time zones differ. Patient IDs don't always match. Manual integration is slow, expensive, and introduces errors that silently corrupt analyses.

## The Symbolic Generative AI Solution

Combining relational calculus + chase algorithms + formal verification + query optimization can automate data integration with mathematical guarantees of correctness.

!!! success "The Chevron Case Study"
    A large systems integrator sent **20 engineers** and took **18 months** to complete a database migration using traditional methods.

    A second team used symbolic generative AI: **2 people**, **18 days** — and formal methods identified errors in the original migration that the 20-person team had *missed*.

    **Cost reduction: ~95%. Risk: lower.**

## Cost Curve

Traditional procedural integration scales **exponentially** — costs explode as data volume grows. Symbolic generative AI has higher upfront setup cost but scales **linearly** with mathematical quality assurance.

For a growing organization like ALS TDI, the inflection point matters: the longer you stay on the exponential curve, the more expensive the eventual switch.

---

[← Chase Algorithm](chase-algorithm.md) | [Next: Claude & Anthropic →](../module-6/claude-anthropic.md)
